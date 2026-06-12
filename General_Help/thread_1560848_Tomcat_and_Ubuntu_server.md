---
title: "Tomcat and Ubuntu server"
date: 2010-08-25
forum: General Help
---

### Post by zombie_ on 2010-08-25
Hello everyone, 

I can start the Tomcat like this on the Ubuntu server.

>sudo /etc/init.d/tomcat6 start
 * Starting Tomcat servlet engine tomcat6                                [ OK ] 


I created the /myapps folder inside the Tomcat folder, and put my test.WAR file. 

Now I would like to know how I can deploy the WAR file. 


Thanks in advance,

---

### Post by _sluimers_ on 2010-09-04
Well as far as I know there are two ways to deploy a warfile.
One of them is going to [http://localhost:8080/manager](http://localhost:8080/manager) or [http://localhost/manager](http://localhost/manager) if you set your tomcat port to 80.

The other(better) option is going to /etc/tomcat6/Catalina/localhost and add another xml file similar to the ones already there. You'd probably want to make a ROOT.xml with 

```
<Context path="/ROOT" docBase="/home/<myname>/webapps/website.war" />
```

---

