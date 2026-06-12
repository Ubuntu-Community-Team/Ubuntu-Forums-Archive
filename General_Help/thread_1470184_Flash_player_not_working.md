---
title: "Flash player not working"
date: 2010-05-02
forum: General Help
---

### Post by olyduck on 2010-05-02
Just installed 10.4 and can't get Flash to work.  Can't play You Tube videos. Photoshop.com tells me I need to get the latest version of Flash Player, and I did, but no change.  I've installed the Flash Installer and almost everything else name Flash to no avail.

Next steps?

Thanks, Olyduck

---

### Post by koekjestrommel on 2010-05-02
sudo aptitude install gsfonts gsfonts-x11 flashplugin-nonfree


Worked for me, first I tried to install java, stumpled on this tried it, worked within one minute. Java still doesnt work for me though :(

---

### Post by no2498 on 2010-05-02
you need to install all extras the for me on 804 it was medubuntu extras
gives you the win 32 codes, java,flash

---

### Post by olyduck on 2010-05-02
I finally solved it by downloading a different version of Flash from the Adobe site

.rpm for linux

No I can play Flash videos and use photoshop.com

Thanks to all for your previous suggestions,
Olyduck

---

### Post by TBABill on 2010-05-02
Ummmm.....Ubuntu is Debian based and uses deb files, not RPMs. Are you sure you didn't download a deb from Adobe?

Easiest way to do all this is to enable ubuntu extras in the software center. Did you already do that? Much easier than installing everything item by item.

---

### Post by techunit on 2010-05-02
Well it doesn't matter now. Please change the Thread tools to solved if this has fixed your problem

---

### Post by aimanwm on 2010-05-02
I tried number 2, but it did not work.  I am wondering if I even have the exact same problem.  My issue is this--

**package  flashplugin-nonfree 10.0.1.218 really9.0.262.0ubuntu1 failed to  install/upgrade:**


Package is in a very bad inconsistent state - you should  reinstall it  before attempting configuration.

---

### Post by techunit on 2010-05-02
> **aimanwm said:**
> I tried number 2, but it did not work.  I am  wondering if I even have the exact same problem.  My issue is this--

**package  flashplugin-nonfree 10.0.1.218 really9.0.262.0ubuntu1 failed  to  install/upgrade:**


Package is in a very bad inconsistent state - you should  reinstall it   before attempting configuration.


Are you using 64bit Ubuntu?

---

### Post by alcyst on 2010-05-12
I have the same problem as aimanwm, have tried many suggestions, no improvement

---

### Post by alcyst on 2010-05-12
The upside of this flash problem is I get to visit Apple-iPad-land from the comfort of a Ubuntu desktop

---

### Post by brayden551 on 2010-05-18
First, Make sure your ubuntu is updated. Goto System > Administration > Update Manager. Now, Click check. After that - Click install updates. Wait for the updates to install and then download the **.deb** from adobe.com. Make sure firefox is closed. Now download the Flash Player Installer from Ubuntu software Center. Now that your system is updated, you can run the .deb package. Wait for it to install. Once installed. Log off and Log back onto Ubuntu. Now, open Firefox and go to a flash website (ex. youtube, grooveshark) Firefox should say "Additional plug-ins are required......" Click the button beside that and then install **ADOBE** flash plug-in. Restart Firefox and then try you tube again. :) 

~Hope this helps!

---

