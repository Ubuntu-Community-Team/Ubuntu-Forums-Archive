---
title: "deploy a WAR file through Tomcat in a Ubuntu server"
date: 2010-08-26
forum: General Help
---

### Post by zombie_ on 2010-08-26
Im dying to know if anybody has any clue how I can deploy a WAR file with a Tomcat that happens to be installed on a server. I divided it to different small questions but no strait answer so far.

These are the things I've done: 

created a myapps folder inside the tomcat directory, and copied the WAR file there. 

These are the questions: 

1. I did not touch anything inside the Tomcat folder, anything need to be changed?. 
2.How to start the Tomcat so that it can deploy th e WAR file? 

many many thanks!

---

### Post by _sluimers_ on 2010-09-05
I did it by creating an xml file in /etc/tomcat6/Catalina/localhost similar to the ones already there.

---

### Post by zombie_ on 2010-09-08
Can you copy/paste it here please?

Thanks

---

### Post by _sluimers_ on 2010-09-23
ROOT.xml
```

<Context path="/ROOT" docBase="/home/rogier/webapps/website.war" />

```

Unfortunately, my server crashed, so this is copied from my old server to my new one and for some reason it's no longer working for me :/
There must be something extra that needs to be done or something.

---

