---
title: "Cannot Start 1 Webapp in Tomcat - And No Logs!"
date: 2009-10-21
forum: General Help
---

### Post by dwarbi on 2009-10-21
Hi there,

I've successfully set up Tomcat 5.5 on my Hardy server, and it starts up just fine (for example, jsp-examples) but when I try to start up my own app - which is a Web service, I get the following error:
FAIL - Application at context path /{appname} could not be started

I can't find any logs - well, that's not true, in the log folder I found {appname}.log, but it was empty. Is there any way I can try to start the app from a command line so I can see the processes as the execute? Maybe write to a file...

Thanks so much for any help...

Cheers!
Denis

---

### Post by dwarbi on 2009-10-22
I followed these steps to add in logging:
[http://tomcat.apache.org/tomcat-5.5-doc/logging.html](http://tomcat.apache.org/tomcat-5.5-doc/logging.html)

So now I get lots of great logs! But not one single mention (that I can find) of the attempt to start my application and the subsequent failure. Does anyone have any advice? I can't figure out how to find the cause of this error. :-\

---

### Post by Mighty_Joe on 2009-10-23
How are you trying to start your application?  Where do you get this error if you didn't have logging enabled?

---

