---
title: "can not see public folder in FF"
date: 2012-08-25
forum: General Help
---

### Post by davidtheo on 2012-08-25
HI all
 
I am using Ubuntu 12.02 64 bit

 The follow happens when I make a project with the ZF command and with Zend Studio
 

 The folders in my development folder are
 
removed by me
 

 in my virtual host file my documentRoot and Directory paths are
 path_to_folder/myworkspace/project/public
 

 When i view my project in FF I get
 

 ```
Internal Server Error
 

 The server encountered an internal error or misconfiguration and was unable to complete your request.
 

 Please contact the server administrator, [no address given] and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 

 More information about this error may be available in the server error log.
``` If I change my virtual host file to
 path_to_folder/myworkspace/project
 I get this
 
    ```

 Index of /
removed by me

``` It looks like FF does not have permission to view the public folder but it has the same permissions as the others.
 

 Can someone please help me

---

### Post by davidtheo on 2012-08-25
I worked it out

I just needed to run 

```
**sudo a2enmod rewrite**
```

---

