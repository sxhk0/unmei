###### Unmei —

#### Syntax

##### `application_config.unmei`

```py
Version "1.0"

# Options for linter
Linting {
    Enabled True
    Use "presslinter"
}

# Configure environment variables
Environment {
    APP_MODE "production"
}
```

##### `proxy-rules.unmei`

```py
BlockIf @{request.country != "BR"} {
    Redirect "/unavailable-region.html"
}

BlockIf @{request.ip != "289.23.632.34"} {
    Redirect "/blocked.html"
}
```

###### Translates to: `firewall-rules.unmei.js`

```js
module.exports = [
    BlockIf: {
        Condiction: (request) => {
            return request.country !== 'BR'
        },
        Children: {
            Redirect: '/unavailable-region.html'
        }
    },
    BlockIf: {
        Condiction: (request) => {
            return request.ip !== '289.23.632.34'
        },
        Children: {
            Redirect: '/blocked.html'
        }
    }
]
```

#### License

> [MIT](/LICENSE) @ Itallo Gabriel ([@sxhk0](https://github.com/sxhk0))
