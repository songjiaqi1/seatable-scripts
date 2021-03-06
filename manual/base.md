# Base object

Base object provide a way to manipulate data in a base.

## Table

#### getActiveTable

Get the currently selected table.

##### Example

```javascript
const table = base.getActiveTable();
output.markdown(`#### ${table.name}`);
```

#### getTables

Get all tables.

##### Example

```javascript
const tables = base.getTables();
output.text(tables.length);
```

#### getTableByName

Get a table via its name.

##### Example

```javascript
const table = base.getTableByName('A test table');
output.text(table._id);
```

#### addTable

Add a table.

##### Example

```javascript
base.addTable('New table');
```

#### renameTable

Rename a table.

##### Example

```javascript
base.renameTable('Old name', 'New name');
```

#### deleteTable

Delete a table.

##### Example

```javascript
base.deleteTable('Old table');
```

## View

#### getActiveView

Get the current selected view.

##### Example

```javascript
const view  = base.getActiveView();
output.text(view.name);
```

#### getViews

Get all views of a table.

##### Example

```javascript
const views = base.getViewsByName('Table name');
output.text(views.length);
```

#### getViewByName

Get a view by table object and view name.

##### Example

```javascript
const view = base.getViewByName(table, 'View Name');
output.text(view.name);
```

#### addView

Add a view to a table

```javascript
base.addView(tableName: String, viewName: String);
```

##### Example

```javascript
base.addView('table', 'view1');
```

#### renameView

Rename a view

```javascript
base.renameView(tableName: String, currentViewName: String, nextViewName: String);
```

##### Example

```javascript
base.renameView('table', 'view1', 'view2');
```

#### deleteView

Delete a view

```javascript
base.deleteView(tableName: String, viewName: String);
```

##### Example

```javascript
base.deleteView('table', 'view2');
```

## Column

#### getColumns

Get columns of a table.

```javascript
base.getColumns(table: Object);
```


###### Example

```javascript
const columns = base.getColumns(table);

column.forEach((column) => {
	output.text(column.name);
})


#### getShownColumns

Get all visible columns in a view

```javascript
const columns = base.getShownColumns(table: Object, view: Object);
```


##### Example

```javascript
const columns = base.getShownColumns(table, view);
column.forEach((column) => {
	output.text(column.name);
});
```

#### getColumnByName

Get column object by name.

```javascript
const column = base.getColumnByName(table: Object, name: String);
```

##### Example

```javascript
const column = base.getColumnByName(table, "A test column");
output.text(column.name);
```

#### getColumnsByType

Get columns of a specific type.

```javascript
const columns = base.getColumnsByType(table: Object, type: String);
```

##### Example

```javascript
const columns = base.getColumnsByType(table, "text");
output.text(column.length);
```

### Row

#### getRows

Get rows of a specific view.

```javascript
const rows = base.getRows(table: Object, view: Object);
```

#### getGroupedRows

Get grouped rows of a specific view. The view should be a view containing group of rows.

```javascript
base.getGroupedRows(table: Object, view: Object);
```

##### Example

```javascript
const table = base.getTableByName('table');
const view = base.getViewByName(table, 'grouped view');
const groupViewRows = base.getGroupedRows(table, view);
```

##### getRowById

Get a row by its ID.

```javascript
const row = base.getRowById(table: Object, rowId: String);
```

##### Example

```javascript
const row = base.getRowById(table, "M_lSEOYYTeuKTaHCEOL7nw");
```

#### deleteRowById

Delete a row in a table by its ID.

```javascript
base.deleteRowById(table: Object, rowId: String);
```

##### Example

```javascript
base.deleteRowById(table, "M_lSEOYYTeuKTaHCEOL7nw");
```

#### addRow

Add a row to a table. The new row will append at the end of the table. If view is given, append the row at the end of that view.

```javascript
base.addRow(tableName: String, rowData: Object, viewName?: String)
```

##### Example

```javascript
// use case
base.addRow('Table1', {'Name': 'Joe Key', 'Age': '18'});

// use case
base.addRow('Table1', {'Name': 'Joe Key', 'Age': '18'}, 'Default View');
```

#### modifyRow

Modify a row in a table.

```javascript
base.modifyRow(table: Object, row: Object, updateRowData: Object);
```

##### Example

```javascript
const table = base.getTableByName('table');
const row = base.getRowById(table, "M_lSEOYYTeuKTaHCEOL7nw");
base.modifyRow(table, row, {'Name': 'new name', 'number': 100});
```
