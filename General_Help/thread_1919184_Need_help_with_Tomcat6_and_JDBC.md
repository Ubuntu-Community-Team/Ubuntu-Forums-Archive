---
title: "Need help with Tomcat6 and JDBC"
date: 2012-02-02
forum: General Help
---

### Post by DRouleau on 2012-02-02
Ok I've decided to finally give Java a shot after years of avoiding it.  However I can't seem to figure out how to get this installed and working.  I followed the examples about installing Tomcat and that seems to be there and running fine.  I find a lot of articles saying to put the JDBC files in the WEB-INF directory, however I can't find that directory. This is my first time trying this and I've been at it for 3+ hours now with no progress. Any help will be much appreciated. 
Thank you in advance!!

---

### Post by dragonfly41 on 2012-02-02
I've got tomcat7 installed (manually)

to find WEB-INF locations in your webapps try command **sudo locate WEB-INF**

e.g. when I run **sudo locate jdbc **I see this ..

/usr/local/tomcat7/lib/tomcat-jdbc.jar
/usr/local/tomcat7/webapps/docs/jdbc-pool.html
/usr/local/tomcat7/webapps/docs/funcspecs/fs-jdbc-realm.html


[EDIT]

I don't use jdbc yet  .. but ..

try command **echo $CATALINA_HOME**

my output is /usr/local/tomcat7

I believe that you place your jdbc jar in $CATALINA_HOME/webapps/[yourwebappname]/WEB-INF/lib/ for each deployed application

if you place it in $CATALINA_HOME/webapps/ROOT/WEB-INF/lib/
the jdbc driver will be made available for every deployed application and this may result in conflicts between jars.

---

### Post by DRouleau on 2012-02-02
ok so a few "problems" here.  First when I did the search nothing was found.  Secondly my tomcat6 directory is in /etc and there is no lib directory in it.
This is the content of /etc/tomcat6
Catalina
catalina.properties
context.xml
logging.properties
policy.d
server.xml
tomcat-users.xml
web.xml

---

### Post by dragonfly41 on 2012-02-02
Please see my added postscript above on /WEB-INF/lib/ paths

...

In my working configuration although I have tomcat7 installed (manually) in /usr/local/ 
it could have been installed in other folders 
such as /etc/ 

Here is a tutorial I followed (but it does not mention jdbc)

[http://diegobenna.blogspot.com/2011/01/install-tomcat-7-in-ubuntu-1010.html](http://diegobenna.blogspot.com/2011/01/install-tomcat-7-in-ubuntu-1010.html)

The content of /etc/tomcat6/ you have posted in fact I see in ..

/usr/local/tomcat7/conf/

your equivalent should be

/etc/tomcat6/conf/

[COLOR=Navy]
[EDIT]

This is why I chose /usr/local/ for tomcat7 installation ..

[http://linuxcommand.org/lts0040.php#local](http://linuxcommand.org/lts0040.php#local)[/COLOR]

---

### Post by DRouleau on 2012-02-02
Ok I followed that link and have the jdk directory all set up... got to the tomcat page on my server and it says:
Tomcat6 veterans might be pleased to learn that this system instance of Tomcat is installed with CATALINA_HOME in /usr/share/tomcat6
when I look there CATALINA_HOME isn't there, that should be a directory right?

---

### Post by dragonfly41 on 2012-02-02
In terminal run command ..

sudo gedit /etc/environment

and you'll see $CATALINA_HOME specified as an environment variable

Here is what mine looks like ..


[COLOR=Navy]PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
CATALINA_HOME="/usr/local/tomcat7"
CATALINA_BASE="/usr/local/tomcat7"
JAVA_HOME="/usr/lib/jvm/jdk1.7.0"
JRE_HOME="/usr/lib/jvm/jdk1.7.0/jre"[/COLOR]

---

### Post by DRouleau on 2012-02-03
I did that and I have:

JAVA_HOME="/usr/local/jdk1.7.0_02"
JRE_HOME="/usr/local/jdk1.7.0_02/jre"
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

I'm guessing I need to add those other 2?
in my case it would be?
CATALINA_HOME="/etc/tomcat6"
CATALINA_BASE="/etc/tomcat6"

---

### Post by dragonfly41 on 2012-02-03
Correct.

---

### Post by DRouleau on 2012-02-03
Ok, I'll give that a shot, though to know if it's working I guess I'll have to create something and move it over.  I'm developing on my XP machine as that is where I have a desktop and then I'll have to move it over to my Ubuntu server.

---

### Post by dragonfly41 on 2012-02-03
I'm in the same position of having to develop tomcat webapps on both Windows and Ubuntu and I'm considering using <context> to map both servers webapps to a shared NTFS partition.

[EDIT]

[http://stackoverflow.com/questions/715506/tomcat-6-how-to-change-the-root-application](http://stackoverflow.com/questions/715506/tomcat-6-how-to-change-the-root-application)

---

