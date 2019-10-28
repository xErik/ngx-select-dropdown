# ngx-select-dropdown

[![GitHub license](https://img.shields.io/github/license/manishjanky/ngx-select-dropdown.svg)](https://github.com/me-and/mdf/blob/master/LICENSE)
[![npm](https://img.shields.io/npm/v/ngx-select-dropdown.svg)]()
[![Build Status](https://travis-ci.org/manishjanky/ngx-select-dropdown.svg?branch=master)](https://travis-ci.org/manishjanky/ngx-select-dropdown)
[![Codecov branch](https://codecov.io/gh/manishjanky/ngx-select-dropdown/branch/master/graphs/badge.svg)]()
[![npm](https://img.shields.io/npm/dt/ngx-select-dropdown.svg)]()
[![GitHub top language](https://img.shields.io/github/languages/top/manishjanky/ngx-select-dropdown.svg)]()
[![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/manishjanky/ngx-select-dropdown.svg)]()

`ngx-select-dropdown` Custom Dropdown component for Angular 4+ with multiple and single selection options

## Features
* single select dropdown
* multi select dropdown
* search dropdown list
* arrows keys support
* limit number of items displayed in dropdown
* custom sort 
* angular forms support
* angular v4 and above supported
* cross browser support


## Examples

* [demo-page](https://manishjanky.github.io/ngx-select-dropdown/)

## Installation

* `npm install ngx-select-dropdown`

### Using with webpack and tsc builds/ angular-cli builds

* Import `SelectDropDownModule` into your app.module:

```
import { SelectDropDownModule } from 'ngx-select-dropdown'
```

* Add `SelectDropDownModule` to the imports of your NgModule:

```
@NgModule({
  imports: [
    ...,
    SelectDropDownModule
  ],
  ...
})
class YourModule { ... }
```

* Include CSS-styles in you `angular-cli.json`:

```
 "styles": [
        "../node_modules/ngx-select-dropdown/dist/assets/style.css"
      ],
```


* Use `<ngx-select-dropdown></ngx-select-dropdown>` in templates to add the custom dropdown:

```
<ngx-select-dropdown
  (change)="selectionChanged($event)"
  [multiple]="true"
  [(ngModel)]="dataModel"
  [config]="config"
  [options]="dropdownOptions">
</ngx-select-dropdown>
```

* Use `<ngx-select-dropdown></ngx-select-dropdown>` in templates with reactive form:
```
<ngx-select-dropdown
  (change)="selectionChanged($event)"
  formControlName="selectData"
  [multiple]="true"
  [config]="config"
  [options]="dropdownOptions">
</ngx-select-dropdown>
```

## Config

### Input

* `multiple: boolean` - `true|false` Whether multiple selection allowed or not, defaults to `false`.
* `options: Array` - Array of string/objects that are the dropdown options.
* `disabled: boolean` - Disables the dropdown.
* `config: Object` - Configuration object, see below.

```
config = {
        // If objects array passed which key to be displayed defaults to description.
        
        displayKey: "description",
        
        // true|false for the search functionlity defaults to false.
        
        search: true,
        
         // Height of the list, in case of no more items to show, the scroll defaults to auto.
         // With auto" height, scroll will never appear.
         
        height: 'auto',
        
        // Text to be displayed when, no item is selected defaults to "Select".
        
        placeholder: 'Select', 
        
        // Custom function to sort the items. Default is undefined and Array.sort() .
        
        customComparator: ()=>{},
        
        // Limits the no of options displayed in the UI similar to Angular's limitTo pipe.
        
        limitTo: dropdownOptions.length,
        
        // Text to be displayed when more than one items are selected, like "Option 1 + 5 more".
        
        moreText: 'more',
        
        // Text displayed when no items are found after searching.
        
        noResultsFound: 'No results found!',
        
        // Text displayed in search input.
        
        searchPlaceholder: 'Search',
        
        // Key on which search should be performed, if undefined all keys will be searched.
        
        searchOnKey: 'name'
      }
```

### Output

* `change: Event` - change event when user changes the selected options
* `open: Event` - open event when the dropdown toogles on
* `close: Event` - close event when the dropdown toogles off
* `searchChange: Event` - search change event when the search text changes

### Change detection

As of now, `ngx-select-dropdown` uses the Default change detection strategy, which means dirty checking for immutable data types. But in Javascript Objects and arrays are mutable. So, when changing any of the `@Input` parameters, if you mutate an object, change detection will not detect it. For example:

```
this.options.push({id: 34, description: 'Adding new item'});

// or

config.height = '200px';

```

Both the above scenarios will not trigger any change detection. In order for the componet to detect the changes, you need to do this:

```
this.options = [...this.options, {id: 34, description: 'Adding new item'}];

// or

config = {...config, height:'200px'};

```

## Changelog
* v0.1.0
```
 Added a change event so that user can attach a change event handler.
 If multiselect the selected text will display first item and + count for eg. (Option 1 + 2 more) .
```
* v0.2.0
```
 Angular 4 and above support.
 Bug with search functionality fixed.
```
* v0.3.0
```
 Support for Observable data source for options and async pipe.
 IE bug with styling.
 Few other minor bug fixes.
```
* v0.4.0
```
 Use arrows keys and enter to select items from available options.
 Case insensitive search.
 Few other minor bug fixes.
```
* v0.5.0
```
 Support for scroll bar with too many list items.
 Few other minor bug fixes.
```
* v0.7.0
```
 Support for limito pipe to limit number of options displayed in case of too many options.
 Support for customComparator / custom sort function
 Few other minor bug fixes.
```
* v0.7.2
```
 Support for angular 6
 Removed dependency on rxjs
```
* v0.8.0
```
 No Results found indicator with custom text passed with config
 Custom text for *more* when more than 1 items selected
 Open event emitted
 Close event emitted
 Search placeholder text
```
* v1.0.0
```
 Search on a specified key value.
 Support for Reactive forms
 Few other minor imoprovements and fixes
```
* v1.2.0
```
 Search text change event searchChange
```

## Help Improve

Found a bug or an issue with this? [Open a new issue](https://github.com/manishjanky/ngx-select-dropdown/issues) here on GitHub.

## Contributing to this project

Anyone and everyone is welcome to contribute. Please take a moment to
review the [guidelines for contributing](CONTRIBUTING.md).

* [Bug reports](CONTRIBUTING.md#bugs)
* [Feature requests](CONTRIBUTING.md#features)
* [Pull requests](CONTRIBUTING.md#pull-requests)
