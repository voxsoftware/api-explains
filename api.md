
# Explicación de API

1. Todos los endspoints del API devuelven JSON. EN caso de que ocurra un error se devolverá código 500 y así: 

```javascript
{
	"error": {
		"code": "XXX", // opcional
		"message": "Message del error",
		"stack": "Stack trace"
	}
}
```


Estos son los endpoints del API



* ```POST /api/function/c/app.init ``` (debe ejecutarse al inicio de todas las vistas)	
	
**Parámetros**
Ninguno


**Respuesta**
null


	

*  ```POST /api/function/c/user@login``` Iniciar sesión

**Parámetros**

```javascript 
{
	"email": "xxxx",
	"password": "xxx"
}
```

**Respuesta**
```
{
	"sid": "TOKEN" // este token debe usarse de aquí en adelante en cualquier llamado
}
```




* ```POST /api/function/c/user@current``` Verificar el usuario actual 

**Parámetros**

```javascript
{
	"sid": "TOKEN"
}
```

**Respuesta**
```javascript
// en caso satisfactorio de iniciado sesión
{
	"_id" : {
		"$oid": "5c490fec989de47c0d3158db"
	},
	"username" : "admin",
	"name" : "Administrador",
	"permissions" : [ 
		"all"
	]

}

// en caso de que no hay usuario iniciado sesión
null
```

* ```POST /api/db/query``` Hacer un query a la base de datos

**Parámetros**

```javascript 
{
	"options": {
		"tablename": "person"
	}
	"query": {
		// aquí es válido cualquier query valido para MongoDB
		"xx": "xx"
	},
	"limit": 20 // opcional 
	"sort": { // opcional
		// aquí es válido cualquier sort válido para MongoDB
		"_id": -1
	}
}
```








