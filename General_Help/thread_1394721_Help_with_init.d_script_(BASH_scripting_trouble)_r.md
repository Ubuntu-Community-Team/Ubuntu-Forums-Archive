---
title: "Help with init.d script (BASH scripting trouble) runlevels, Tomcat"
date: 2010-01-30
forum: General Help
---

### Post by matt_man on 2010-01-30
9.04 Jaunty Jackalope Desktop

I'm using the catalina.sh script this comes with Apache Tomcat server, but Tomcat isn't starting up when the system starts.

Here's what works:
#/etc/rc2.d/S86catalina.sh start
will start the server if I can it manually on the command line.

This also works:
#sudo telinit 3
#sudo telinit 2
So if the server is not running, when going back to runlevel 2, the server automatically starts as expected.

I added a debug line to the startup scripts that writes to a file, so I know the script is being run when the system starts, it's just that Tomcat isn't running afterwards.

Here's the section of the script I'm concerned about: (It's straight from the catalina.sh that ships with Tomcat.)
"$_RUNJAVA" "$LOGGING_CONFIG" $JAVA_OPTS
.
.
.
>> "CATALINA_OUT" 2>&1 &

Why are some variables in quotation marks, and others not?

Also, what is the meaning of 2>&1 & at the end?

---

### Post by john newbuntu on 2010-01-31
It could be a environment variable problem or a dependency issue.
You need to check the log file ("$CATALINA_BASE"/logs/catalina.out) to see what is going on.
The last ampersand is for running it in the background as a server.  The 2>&1 is for redirecting stderr and stdout to the same file.

---

