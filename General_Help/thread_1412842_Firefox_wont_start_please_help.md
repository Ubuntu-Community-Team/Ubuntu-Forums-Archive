---
title: "Firefox wont start please help"
date: 2010-02-21
forum: General Help
---

### Post by norsch on 2010-02-21
Total newbie here, just ran "update manager" no problems, tried to start firefox, got the starting firefox message at bottom of screen, then nothing, tried to run galeon and exactly the same. Please help

---

### Post by akand074 on 2010-02-21
the process just needs to be restarted because you must have updated firefox. Either kill the process using the system monitor (System > Administration > System Monitor) or restart.

---

### Post by gadolinio on 2010-02-21
If restarting the system doesn't solve the problem, maybe you could try uninstalling firefox and then reinstalling it.
Go to System--> administration --> synaptic package manager. You'll be asked for your user password.
The program has a search box on the top. Type "firefox" there, without pressing enter.
The list you see in that screen will change and you'll find an item called firefox with a green square to its left. Right-click that item, and select uninstall. Click apply. Then, after the uninstallation process is finished, right-click it again and click install, then apply again.
Hope it helps...

---

### Post by norsch on 2010-02-22
Thanks for the replies guys, I have tried restarting = still the same. I tried Gadolino's uninstsall and reinstall, exactly the same. So everything else seems to work fine, but still no Firefox or Galeon web browser. Any more ideas? Or am I going to have to do a total reinstall?

---

### Post by sdowney717 on 2010-02-22
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)
I think this gives firefox 3.6.2

install chrome browser.
[http://www.google.com/chrome/eula.html?platform=linux](http://www.google.com/chrome/eula.html?platform=linux)

---

### Post by lovinglinux on 2010-02-22
> **norsch said:**
> Thanks for the replies guys, I have tried restarting = still the same. I tried Gadolino's uninstsall and reinstall, exactly the same. So everything else seems to work fine, but still no Firefox or Galeon web browser. Any more ideas? Or am I going to have to do a total reinstall?

Since both browsers are not starting, try to re-install xulrunner. Go to "System >>> Administration >>> Synaptic Package Manager" and locate the installed version of xulrunner (probably xulrunner-1.9.1). Right-click on it, then select "Mark for Reinstallation" then click "Apply".

---

### Post by norsch on 2010-02-22
> **lovinglinux said:**
> Since both browsers are not starting, try to re-install xulrunner. Go to "System >>> Administration >>> Synaptic Package Manager" and locate the installed version of xulrunner (probably xulrunner-1.9.1). Right-click on it, then select "Mark for Reinstallation" then click "Apply".
Thanks to all of youfor taking the time to help, But mant thanks to lovinglinux for solving my problem.:D

---

### Post by lovinglinux on 2010-02-22
> **norsch said:**
> Thanks to all of youfor taking the time to help, But mant thanks to lovinglinux for solving my problem.:D

You are welcome.

---

### Post by jaychamp on 2010-02-22
I'm having the same issue and not having any luck.  I've tried reinstalling FF, xulrunner and even installing any browser for that matter and get the same error every time.

When I try to reinstall FF:

E: xulrunner-1.9-subprocess post-installation script returned error exit status 1

Then when I try to reinstall xulrunner:

/usr/lib/libnss3.so version 'NSS_3.1.2.3' not found (required by /usr/lib/xulrunner-1.9.0.18/libxul.so)

And the same error if I try 1.9.1

libnss3.so is present in the lib folder

---

### Post by lovinglinux on 2010-02-22
> **jaychamp said:**
> I'm having the same issue and not having any luck.  I've tried reinstalling FF, xulrunner and even installing any browser for that matter and get the same error every time.

When I try to reinstall FF:

E: xulrunner-1.9-subprocess post-installation script returned error exit status 1

Then when I try to reinstall xulrunner:

/usr/lib/libnss3.so version 'NSS_3.1.2.3' not found (required by /usr/lib/xulrunner-1.9.0.18/libxul.so)

And the same error if I try 1.9.1

libnss3.so is present in the lib folder

Have you tried to remove xulrunner completely then re-install? Removing xulrunner might remove other packages that depend on it, not only Firefox. So check which packages are removed so you can install them again later.

If that doesn't work, then you will have to fix the installation error, but I don't know how to do that.

Alternatively, you could install Firefox 3.6. It doesn't depend on xulrunner package, so it will probably work.

See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for instructions.

---

### Post by jaychamp on 2010-02-22
> **lovinglinux said:**
> Have you tried to remove xulrunner completely then re-install? Removing xulrunner might remove other packages that depend on it, not only Firefox. So check which packages are removed so you can install them again later.

If that doesn't work, then you will have to fix the installation error, but I don't know how to do that.

Alternatively, you could install Firefox 3.6. It doesn't depend on xulrunner package, so it will probably work.

See the [COLOR=Sienna]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567") for instructions.
Yes I tried completely removing it with the same result.  I'll give 3.6 a try but I seem to get the error no matter what I install though programs that don't depend on it will still install it seems.  Is it because it's trying to fix it every time I run any kind of install?

---

### Post by newboyx on 2010-02-22
> **lovinglinux said:**
> Since both browsers are not starting, try to re-install xulrunner. Go to "System >>> Administration >>> Synaptic Package Manager" and locate the installed version of xulrunner (probably xulrunner-1.9.1). Right-click on it, then select "Mark for Reinstallation" then click "Apply".


Thanks!  Got me up and running again.

---

### Post by sdowney717 on 2010-02-24
using Namoroka is nice. I dont get those grey screens anymore and overall is much better.

[http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html)

I followed this and also had to use synaptic to install all the 3.6 packages

---

