---
title: "Run MySQL Migration tool"
date: 2006-06-23
forum: General Help
---

### Post by nroussi on 2006-06-23
Hi all,
I downloaded the migration tool and I tried to run it through the terminal window and I get teh following error
nic@ubuntu:~/Desktop/mysql-migration-toolkit-script-1.0.6$ ./run_migration
./grtsh: error while loading shared libraries: libjvm.so: cannot open shared object file: No such file or directory
. I read that there might be a problem with the jre libraries and I followed these instructions [http://ubuntuforums.org/showthread.php?t=148075](http://ubuntuforums.org/showthread.php?t=148075) .
In the run_migration file I have the following:
#!/bin/sh

# Change the following paths to your local installation of JRE 1.4
JRE_LIB_PATHS="/usr/local/jdk1.5.0_06/jre/bin/java"

#/opt/j2sdk1.4.2_07/jre/lib/i386/:/opt/j2sdk1.4.2_07/jre/lib/i386/server
if test -z ""; then
	export LD_LIBRARY_PATH="/usr/local/jdk1.5.0_06/jre/bin/java"
fi
#:/opt/j2sdk1.4.2_07/jre/lib/i386/:/opt/j2sdk1.4.2_07/jre/lib/i386/server
./grtsh -x scripts/TextMigrationScript.lua
When I check the command "whereis java" I get:
nic@ubuntu:~$ whereis java
java: /usr/bin/java /etc/java /usr/bin/X11/java /usr/share/java /usr/share/man/man1/java.1.gz
Also, when I right-click on the run_migration file and select "Display" it says "Java Loading" and then it gives the following exception:

JNLParseException[ Could not parse launch file. Error at line 0.]
	at com.sun.javaws.jnl.XMLFormat.parse(XMLFormat.java:51)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(LaunchDescFactory.java:46)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(LaunchDescFactory.java:58 )
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(LaunchDescFactory.java:112)
	at com.sun.javaws.Main.launchApp(Main.java:182)
	at com.sun.javaws.Main.main(Main.java:136)

Can someone please help?

---

