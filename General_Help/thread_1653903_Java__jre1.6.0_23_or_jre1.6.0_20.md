---
title: "Java  jre1.6.0_23 or jre1.6.0_20"
date: 2010-12-27
forum: General Help
---

### Post by mailc on 2010-12-27
I have downloaded and installed the latest Java Version 6 Update 23  and in /OPT i have 2 folders : /opt/java/32/jre1.6.0_23  and jre1.6.0_23 . 

 I had followed instructions for download and installation and removing of old Java versions. But still when I try to verify the version installed it says jre1.6.0_20. 

Using Ubuntu 10.04 .   Computer is not working right : when I play chess on FlyorDie many times it just hangs and more worrisome when using KeePassX to automatically insert a password and username in a site, for no apparent reason computer just reboots on its own - has not done these things before update to Java Version 6 Update 23.
Any suggestions appreciated.
 (I am not computer savvy and would like to avoid having to reinstall).

---

### Post by Irony on 2010-12-27
Make sure you have followed the instructions here for manual install;

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Make sure you update alternatives. Also make sure you have deleted the old java first.

---

### Post by mailc on 2010-12-27
Thanks     
No problems removing old Java and downloading new one to /OPT. 
But then the Instructions say :'Inform the system and make the new JRE the default
(#9 of Instructions). 

And as instructed when I ran 
:/opt/java/32$ sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_23/bin/java" 1  

I get errors:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

And I don't know how to handle these. I had ignored them before with the result that Java did not perform properly.
Thanks

---

### Post by mailc on 2010-12-27
Also when trying to 'Tell the system, that the new Java must be the default'   (Instructions #10. ),   I get same errors: 

~$ sudo update-alternatives --set java /opt/java/32/jre1.6.0_23/bin/java

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

And in Firefox I never get something similar to 'Java(TM) Plug-in 1.6.0_23'  as the Instructions say

---

### Post by mailc on 2010-12-27
The errors were apparently resolved with:

sudo dpkg-reconfigure locales

---

