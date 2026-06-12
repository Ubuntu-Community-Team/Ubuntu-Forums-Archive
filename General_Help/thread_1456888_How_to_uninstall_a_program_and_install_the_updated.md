---
title: "How to uninstall a program and install the updated version???"
date: 2010-04-17
forum: General Help
---

### Post by chris.jericho on 2010-04-17
Hey there....

I had downloaded Bluefish editor from the Ubuntu Software center,,,,, some time ago...  but today I just visited their new site and I found out that their latest stable version is 2.0.0 where as I have the 1.0.7.....

how do I remove the existing one and install the latest stable release..?????
I searched in the software center but it wasn't available.....   what do I do and how do I get the latest release....

this is the instruction given but can't understand it....  please someone help!!!

[http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_9.04_or_newer](http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_9.04_or_newer)

---

### Post by dcstar on 2010-04-17
> **chris.jericho said:**
> Hey there....

I had downloaded Bluefish editor from the Ubuntu Software center,,,,, some time ago...  but today I just visited their new site and I found out that their latest stable version is 2.0.0 where as I have the 1.0.7.....

how do I remove the existing one and install the latest stable release..?????
I searched in the software center but it wasn't available.....   what do I do and how do I get the latest release....

this is the instruction given but can't understand it....  please someone help!!!

[http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_9.04_or_newer](http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_9.04_or_newer)
"**add** the following line to /etc/apt/sources.list " by running this command:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by 3rdalbum on 2010-04-17
> **dcstar said:**
> "**add** the following line to /etc/apt/sources.list " by running this command:
```
gksudo gedit /etc/apt/sources.list
```

Don't do it that way. Go into the Software Sources program and go into the Third Party tab. Click the Add button and paste in the line that it tells you insert (it's the one that starts with 'deb')

---

### Post by chris.jericho on 2010-04-18
Thanks for all the help fellows.... :) Bluefish 2.0.0 is now installed successfully and I can work on my websites with ease. :)

Just wanted to ask one thing.... if in the future, Bluefish will update and a newer version will be available... then will I get automatic updates or I have to manually update again just like how I did it right now??

---

### Post by 3rdalbum on 2010-04-18
> **chris.jericho said:**
> Thanks for all the help fellows.... :) Bluefish 2.0.0 is now installed successfully and I can work on my websites with ease. :)

Just wanted to ask one thing.... if in the future, Bluefish will update and a newer version will be available... then will I get automatic updates or I have to manually update again just like how I did it right now??

If you've added that Bluefish repository (which is what we told you how to do), then any new versions will appear in your Update Manager and will be updated that way.

---

### Post by chris.jericho on 2010-04-18
alright cool thanks :)

---

### Post by Wobbo on 2010-04-20
Ubuntu 10.04 still not using Bluefish 2.0. 

By is Ubu 10.04 still Bluefish 1.0.7...

---

### Post by chris.jericho on 2010-04-20
no you update it and it will be updated.////.. i have the 2.0.0 version installed in my machine :)... i am using 10.04

---

