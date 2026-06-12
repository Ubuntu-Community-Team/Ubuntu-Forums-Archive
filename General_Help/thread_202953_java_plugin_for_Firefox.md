---
title: "java plugin for Firefox"
date: 2006-06-24
forum: General Help
---

### Post by cssutto on 2006-06-24
I have about worn out my keyboard with this problem.

I have downoaded the latest Sun jre as a self extracting.

It extracted and shows that it is in /usr/java/

I have gone through the 

 ln -s /usr/java/jre1.5.0.07/plugin/i586ns7-gcc29
ln: creating symbolic link `./i586ns7-gcc29' to `/usr/java/jre1.5.0.07/plugin/i586ns7-gcc29': File exists

And because it did not work, I repeated it using .06, etc., and got file exists for each.

Package manager says I do not have .07 installed.  Sun's verify test says I do not have it installed.

I am lost.

I need it.  I have a couple of projects that require the plugin.

Does anyone have any suggestions?

I do have the latest firefox.  Just checked my ver with the firefox web page to be sure.

CSSJR

---

### Post by Winblowz on 2006-06-24
All you have to do to install Sun Java with the plugin is 
```
apt-get install sun-java5-jre
apt-get install sun-java5-plugin
```

---

### Post by cssutto on 2006-06-24
Thank you for the quick reply.

But this is what I get as a result of both commands.

/$ sudo apt-get install sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
sun-java5-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

CSSJR

---

### Post by Winblowz on 2006-06-24
```
apt-get remove sun-java5-plugin
apt-get update
apt-get install sun-java5-plugin
```
Try that;)

---

### Post by cssutto on 2006-06-24
Upon entering your commands, ubuntu reported that the plugin was removed.

After the last command, it reported that it had installed the plugin.

But it still does not work.

I even did a cold boot to see if that would bring something to life.

CSSJR

---

### Post by viciouslime on 2006-06-24
Maybe if you try not just removing the plugin but also the sun java package. Then when you reinstall both it will ask you to accept the licence.

---

