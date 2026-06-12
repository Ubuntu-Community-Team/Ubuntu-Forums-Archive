---
title: "CATALINA_HOME and CATALINA_BASE environment variables not set when installing Tomcat6"
date: 2009-10-18
forum: General Help
---

### Post by bogdan_mbe on 2009-10-18
Hello,

I've encountered a little problem when I've installed Tomcat6 on my Ubuntu 9.04 Desktop Edition. 
I followed the exact steps described [here]("https://help.ubuntu.com/9.04/serverguide/C/tomcat.html"), in the official Server Guide:
> sudo apt-get install tomcat6 tomcat6-admin tomcat6-common tomcat6-examples tomcat6-docs
The problem is that CATALINA_HOME and CATALINA_BASE environment variables are not set.

Everything else works fine, but how can I manually set them?
I've noticed that when I go to localhost on the Tomcat configured port (default -> localhost:8080) in the "It works!" page it says:

"Tomcat6 veterans might be pleased to learn that this system instance of Tomcat is installed with CATALINA_HOME in /usr/share/tomcat6 and CATALINA_BASE in /var/lib/tomcat6, following the rules from /usr/share/doc/tomcat6-common/RUNNING.txt.gz."

But, if I consider this, then I should find in $CATALINA_HOME/conf the configuration files but there is no "conf" folder in /usr/share/tomcat6. There are only "bin", "lib", "skel", and "webapps". Also, where should I find the logs that should be found at $CATALINA_HOME/logs? Same wonderings about CATALINA_OPTS...

Please, If you have any idea that might help me, do share it with me.
Thanks.

---

