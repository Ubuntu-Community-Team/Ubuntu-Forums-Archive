---
title: "ubuntu 10.10 + firefox 11 + icedtea 6 + savevid.com = firefox crash"
date: 2012-04-12
forum: General Help
---

### Post by New00Folder on 2012-04-12
Hi!

I'm running firefox 11 on ubuntu 10.10 and I have the icedtea6 plugin installed for java applets. Whenever I go to [savevid.com]("http://www.savevid.com") and the browser has to execute the applet, firefox crashes. I also have chrome on my system and it too has icedtea plugin but it runs the applet without a hitch.

What can be the problem here and what do I do about it?

Thanks

---

### Post by imachavel on 2012-04-12
try opening a terminal

ctrl+alt+t

now type in 

sudo apt-get uninstall "name of java plug in version etc."

so if the java plug in was javappletv.6.1 then you would type

sudo apt-get uninstall javaappletv.6.1

if that doesn't work then try

sudo apt-get remove "name of java plug in"


now re install it, or if you'd prefer to use chrome browser and install the plug in again through chrome:

[http://blog.sudobits.com/2011/09/04/how-to-install-google-chrome-on-ubuntu-11-10/](http://blog.sudobits.com/2011/09/04/how-to-install-google-chrome-on-ubuntu-11-10/)

nice looking web site huh?

---

### Post by New00Folder on 2012-04-13
Hi imachavel,

Is there any reason to believe the plugin wasn't installed correctly the first time?

---

### Post by claracc on 2012-04-13
I think the problem is with icedtea6 java plugin which has been list-blocked by mozilla since has some security problems. As far as i know there isn't yet a security update for it.

You could try to go to plugins in firefox and see if this plugin has been unactivated.

I have installed last oracle java plugin ( [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) )in order to see java applets in firefox for now.

---

### Post by New00Folder on 2012-04-15
Thanks claracc; oracle's java plugin isn't causing firefox to crash.

As a side effect, Chrome too is using oracle's plugin instead of icedtea now. Maybe that's because I set the new java as default.

---

### Post by claracc on 2012-04-15
You are welcome.

Glad to help.

---

