# go-logger
a simple log manager for go

# Install

```
go get github.com/phachon/go-logger
go get ./...
```
# Requirement
go 1.8

# Support adapter
- console
- file
- ....

# Use

- ### example

```
import (
    "go-logger"
)
func main()  {
    logger := go_logger.NewLogger()

    //add adapter, config adapter
    logger.Attach("console", map[string]interface{}{
        "color": false,
    })
    logger.Attach("file", map[string]interface{}{
        "filename": "test.log",
    })

    logger.SetLevel(go_logger.LOGGER_LEVEL_DEBUG)
    //Asynchronous or synchronous ? default is synchronous
    logger.SetAsync()

    logger.Emergency("this is a emergency log!")
    logger.Alert("this is a alert log!")
    logger.Critical("this is a critical log!")
    logger.Error("this is a error log!")
    logger.Warning("this is a warning log!")
    logger.Notice("this is a notice log!")
    logger.Info("this is a info log!")
    logger.Debug("this is a debug log!")

    //if you want use asynchronous type, must write a line at the end logger.Flush()
    logger.Flush()
}
```
- ### console adapter
```
logger.Attach("console", map[string]interface{}{
    "color": false, // color: bool, console text color
})
```
#### console color preview
![image](https://github.com/phachon/go-logger/blob/master/example/images/console.png)

- ### file adapter

```
logger.Attach("file", map[string]interface{}{
    "filename": "test.log",  //filename: string, file path and name
    //file slice type "line" "line" "date"
    "slice": map[string]interface{}{
        "size": 5,          //slice file by max size (kb)
        //"line": 1000,     //slice file by max line
        //"date": "y",      //slice by date year
        //"date": "m",      //slice by date month
        //"date": "d",      //slice by date day
        //"date": "h",      //slice by date hour
        //"date": "i",      //slice by date minute
        //"date": "s",      //slice date second
    },
})
```

## Feedback

Welcome to submit comments and code, contact information phachon@163.com

## License

MIT

Thanks
---------
Create By phachon@163.com
