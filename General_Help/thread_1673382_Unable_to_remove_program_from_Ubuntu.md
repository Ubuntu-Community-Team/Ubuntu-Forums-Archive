---
title: "Unable to remove program from Ubuntu"
date: 2011-01-22
forum: General Help
---

### Post by RSASKA on 2011-01-22
Hello,

I am trying to uninstall a program, Tomcat6 from Ubuntu. I followed the directions in 

[http://www.webune.com/forums/uninstall-apache-tomcat-in-ubuntu.html](http://www.webune.com/forums/uninstall-apache-tomcat-in-ubuntu.html)

And didn't receive errors. However, this website

[http://www.webune.com/forums/how-to-list-installed-packages-in-ubuntu.html](http://www.webune.com/forums/how-to-list-installed-packages-in-ubuntu.html)

gives the command to find installed packages in ubuntu

When I went to terminal and typed in dpkg -L tomcat6, it gave

/var/log/tomcat6
/var/lib/tomcat6
/var/lib/tomcat6/webapps
/var/cache/tomcat6
/etc
/etc/tomcat6
/etc/tomcat6/catalina.properties
/etc/tomcat6/logging.properties
/etc/tomcat6/context.xml
/etc/tomcat6/server.xml
/etc/tomcat6/tomcat-users.xml
/etc/tomcat6/web.xml
/etc/tomcat6/policy.d
/etc/tomcat6/policy.d/01system.policy
/etc/tomcat6/policy.d/02debian.policy
/etc/tomcat6/policy.d/03catalina.policy
/etc/tomcat6/policy.d/04webapps.policy
/etc/tomcat6/policy.d/50local.policy
/etc/default
/etc/default/tomcat6
/etc/init.d
/etc/init.d/tomcat6
/etc/cron.daily
/etc/cron.daily/tomcat6


I even tried restarting, but no luck. How to I remove all reminants of Tomcat6. I really need to do this?

---

### Post by hakermania on 2011-01-22
This is really dangerous and use it on your own risk!!!
The script will normally delete from your system every entry of tomcat6 (EVERY ENTRY), and must be run with ***root privileges***:
```
#!/bin/bash
updatedb
locate tomcat6 > to_remove
while read -r;
do
files+=("$REPLY");
done < to_remove
rm -r "${files[@]}"
echo "The files removed where:
"${files[@]}""
rm to_remove
```What it does is to
a) update the database of all the filenames of your system that locate uses
b) writes to a file all the output of the locate command
c) Removes every file found
d) Removes the temp file used

Again: Use at your own risk. I used it successfully:
[IMG]http://i54.tinypic.com/2vdmwwz.png[/IMG]

---

### Post by RSASKA on 2011-01-22
If that is the case, can't I manually delete every Tomcat6 entry?

I'm novice with computers and don't want to take such a  risk.

Please guide.

---

### Post by RSASKA on 2011-01-22
My goal is to delete Tomcat6 entirely, and then do a clean APT install,i.e. go to terminal, type in 

sudo **apt-get** install tomcat6 tomcat6-admin tomcat6-common tomcat6-user tomcat6-docs tomcat6-examples

because it will install in one directory and be easier to use and maintain.

---

### Post by hakermania on 2011-01-22
Look, it isn't such a risk.
From a terminal, run updatedb and then locate tomcat6 to see which files will be deleted if you run the script.
On the other hand, If there are tomcat6 files in your file system but without the filename "tomcat6" then you can "sudo gnome-search-tool" and search for files than contain the word tomcat6....
This is what I'd do.

---

### Post by gmargo on 2011-01-22
Those configuration files are left behind because you instructed the system to leave them behind.  How?  By using "apt-get remove" instead of "apt-get purge".

The good news is that you can run "apt-get purge tomcat6" now, and it should remove those config files.

---

### Post by RSASKA on 2011-01-23
Good Morning!

I tried it out and Tomcat has been successfully uninstalled. 

Thank you!

---

