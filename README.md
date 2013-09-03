# gojsonschema

## Description
An implementation of JSON Schema, based on IETF's draft v4 - Go language

## Status

Functional, two features are missing : dependencies as schemas and id(s) as scope for references

Test phase : Passed 97% of Json Schema Test Suite

Internal improvements/refactoring in progress, anyway the interface will not change

## Usage 

### Basic example

```
package main 

import (
	"github.com/sigu-399/gojsonschema"
	"fmt"
)

func main() {

	schema, err := gojsonschema.NewJsonSchemaDocument("http://myhost/bla/schema1.json")
	// OR
	//schema, err := gojsonschema.NewJsonSchemaDocument("file:///home/me/myschemas/schema1.json")
	
	if err != nil {
		panic(err.Error())
	}

	jsonToValidate, err := gojsonschema.GetHttpJson("http://myotherhost/blu/extract56.json")
	// OR
	//jsonToValidate, err := gojsonschema.GetFileJson("/home/billy/hotels.json")
	
	if err != nil {
		panic(err.Error())
	}

	validationResult := schema.Validate(jsonToValidate)

	fmt.Printf("IsValid %v\n", validationResult.IsValid())
	fmt.Printf("%v\n", validationResult.GetErrorMessages())

}

```

## References

###Website
http://json-schema.org

###Schema Core
http://json-schema.org/latest/json-schema-core.html

###Schema Validation
http://json-schema.org/latest/json-schema-validation.html

## Dependencies
https://github.com/sigu-399/gojsonpointer

https://github.com/sigu-399/gojsonreference

## Uses

gojsonschema uses the following test suite :

https://github.com/json-schema/JSON-Schema-Test-Suite