# _Thoughts And Notes To Review_

- GENERAL DATABASE -
  - ID
  - Year
  - Make
  - Model
  - Category (5-Door, Coupe, CUV, Hatchback,Sedam SUV, Truck, Van/Minivan, Wagon)

Vehicle Categories have different features?

Convenience Features
Entertainment Features
Specs and Dimension
Body Exterior
Powertrain
Safety and Security
Suspension/Handling
Lighting, Visibility and Instrumentation

psql - create db | pgAdmin
<server_folder> - knex init

## _I THINK THAT THE LESS DATA MANIPULATION ON THE CLIENT SIDE THE BETTER_

### Alternatives to remove empty properties returned from DB:

~~Maybe can be done through query~~

Option#1 - Has a _SIDE EFFECT_ and modifies the original object

```javascript
for (var keys in props.convenienceDetails) {
  if (props.convenienceDetails[keys].length === 0) {
    delete props.convenienceDetails[keys];
  }
}
```

Option#2 - Creates new _ARRAY_ with an object and it's properties

```javascript
let reformattedData = data.map(obj => {
  console.log("This is obj ", obj);
  let rObj = {};
  for (var keys in obj) {
    if (obj[keys].length > 0) {
      rObj[keys] = obj[keys];
    }
  }
  return rObj;
});
console.log("This is reformatted ", reformattedData);
```

Option#3 - _TOO COMPLICATED_ ~~Create default value for empty properties of undefined.~~

Option#4 - Before rendering in the component create conditional statement to only show properties with value length > 0

### How to convert property value of typeof array into obj literals

### How can I hide unnecesary data from user?

Option#1 - Don't retrieve them through query. _SOUNDS BEST_

Option#2 - At the List component of the table setting value of them to empty string and then use Option#2 of removing empty properties

### How to deal with vehicle who doesn't have collection?

Through controller? Or at App? Or Component?
