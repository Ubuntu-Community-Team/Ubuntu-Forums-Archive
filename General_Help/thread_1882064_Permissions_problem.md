---
title: "Permissions problem"
date: 2011-11-16
forum: General Help
---

### Post by davidtheo on 2011-11-16
I am getting this error when creating a project with Zend
I think it is due to Zend not having permissions 

  	 	 	 	 	```
david@ubuntu:/var/www$ zf create project strood_crafts /www/strood_crafts 
 PHP Warning:  mkdir(): Permission denied in /usr/share/php/libzend-framework-php/Zend/Tool/Project/Provider/Project.php on line 55 
  
 Warning: mkdir(): Permission denied in /usr/share/php/libzend-framework-php/Zend/Tool/Project/Provider/Project.php on line 55 
                           An Error Has Occurred                          
  Could not create requested project directory 'strood_crafts'            
  
 Zend Framework Command Line Console Tool v1.11.10 
 Details for action "Create" and provider "Project" 
   Project 
     zf create project path name-of-profile file-of-profile 

``` 
 


1, can I make an public folder where Zend and netbeans can write to in ```
/var/www/
```



2, If I can not to the above can you please help me getting a virtual host working

```

Listen 8080
NameVirtualHost *:8080
<VirtualHost *:8080>
 DocumentRoot /home/david/workspace/strood_crafts/public
</VirtualHost>

```

---

### Post by davidtheo on 2011-11-16
when I go to localhost:8080 I am now getting this error

```

**Internal Server Error**

 The server encountered an internal error or misconfiguration and was unable to complete your request.
 Please contact the server administrator,  [no address given] and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 More information about this error may be available in the server error log.
  Apache/2.2.20 (Ubuntu) Server at localhost Port 8080
```

---

### Post by davidtheo on 2011-11-16
I worked it all out, and got it working,

---

