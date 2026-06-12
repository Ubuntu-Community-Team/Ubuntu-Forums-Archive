---
title: "Firefox 3.5.7 reallllly slow"
date: 2010-02-11
forum: General Help
---

### Post by Objekt on 2010-02-11
Firefox 3.5.7 is glacially, painfully slow on my 64-bit Ubuntu 9.10 install.  With exactly the same version of Firefox, and using exactly the same plugins and add-ons, it was lightning fast when I was running it in Windows XP, or on a Win XP virtual machine under Ubuntu.  Lately I've been wondering why.

I don't know whether this is an Ubuntu problem, an Ubuntu 64-bit problem, or a Firefox problem.

Is the Linux version of Firefox 3.6 supposed to be substantially faster?  I've been wanting to upgrade, but although I have Ubuntuzilla installed, it hasn't automagically updated itself to 3.6.  Possibly I have broken something or failed to install Ubuntuzilla correctly.

Could this be an inherent problem with running 64-bit Ubuntu?  I am pretty sure Firefox does not release native 64-bit versions, so maybe it is a problem with running 32-bit code in a 64-bit environment.  I don't really know how that works, but if Ubuntu is having to do some sort of emulation, or other tricks to use an app coded in a non-native format, that could explain the slowness.

Also Firefox does not quit normally.  When I close the window, it goes away instantly, but the Firefox process almost always keeps running in the background.  I know this because I am almost always asked whether I want to terminate the Firefox process when I try to log out or restart the system.

To clarify, Firefox opens slowly, and general operations - opening menus, browsing, etc. - are noticeably slower than using the same version was under Windows XP.  Not sure why, and I'm open to suggestions on how to fix.

Also: I have desktop effects turned off.  My router is set to use the OpenDNS servers.  Anyway it's not so much a problem with how fast pages load, it's all the other things Firefox does which are slow: opening/closing tabs, drawing menus, etc.

---

### Post by vickoxy on 2010-02-11
Install Chrome-the fastest browser definitely for linux. Even java and flash are working fine. Missing only moonlight 2.0...

---

### Post by mikewhatever on 2010-02-11
Objekt, what add-ons do you have installed, Ghostery, by any chance? It should be comparable in speed to the Windows version, since you mentioned it. Not quite sure who told you Firefox for Linux is 32bit only, that's incorrect. In case you don't want to list all ad-ons, run firefox in safe mode:

firefox -safe-mode


> **vickoxy said:**
> Install Chrome-the fastest browser definitely for linux. Even java and flash are working fine. Missing only moonlight 2.0...

Oh really?

[http://www.theregister.co.uk/2010/02/11/opera/](http://www.theregister.co.uk/2010/02/11/opera/)

---

### Post by Objekt on 2010-02-11
Well, I'm at work now so I'll have to wait until I get home to list the add-ons.

It's quite puzzling that I had the same setup -add ons, plugins, and so on - under both Windows XP and Ubuntu 9.10, yet Firefox was much faster in Windows.

I upgraded my Windows Firefox to 3.6 and it's still loads faster than 3.5.7 under Ubuntu.  With 3.6, I had to change some of my add-ons to updated versions, but the loadout is still essentially the same.

---

### Post by khelben1979 on 2010-02-11
If you download Firefox from the mozilla.org website and install it you can use Firefox 3.6 today on your Ubuntu.

I'm running Firefox 3.6 on my Debian Lenny over here. Works okay and feels faster than any version of 3.5 that has been released.

---

### Post by mikewhatever on 2010-02-11
> **khelben1979 said:**
> If you download Firefox from the mozilla.org website and install it you can use Firefox 3.6 today on your Ubuntu.

I'm running Firefox 3.6 on my Debian Lenny over here. Works okay and feels faster than any version of 3.5 that has been released.

The OP will need to compile from source, since mozilla only provides 32bit binaries for Linux.

---

### Post by vickoxy on 2010-02-11
> **mikewhatever said:**
> Objekt, what add-ons do you have installed, Ghostery, by any chance? It should be comparable in speed to the Windows version, since you mentioned it. Not quite sure who told you Firefox for Linux is 32bit only, that's incorrect. In case you don't want to list all ad-ons, run firefox in safe mode:

firefox -safe-mode




Oh really?

[http://www.theregister.co.uk/2010/02/11/opera/](http://www.theregister.co.uk/2010/02/11/opera/)

Well, i am no power-user, but i have all browser installed and tried them-chrome is deffinitely the fastest one-works with multiple tabs perfect... Only comparable was to me midori-but, no java support makes it no choice for me.
As said, i am just normal-user-those tester can write what ever they want, but i know how it works on my computer.

P.S. on the other side-chrome for linux runs faster and better (fullscreen, etc.) in linux then in mac os-so ,i have nothing against firefox, i am using it on mac os-just linux version was really pleasant surprise for me.

---

### Post by Objekt on 2010-02-11
> **mikewhatever said:**
> The OP will need to compile from source, since mozilla only provides 32bit binaries for Linux.

Yes, this is why I used Ubuntuzilla.  I don't have the slightest idea how to compile Firefox (or anything else).  Ubuntuzilla handles the details automagically, except I did have to fix the Flash plugin manually.

---

### Post by lovinglinux on 2010-02-11
> **vickoxy said:**
> Install Chrome-the fastest browser definitely for linux. Even java and flash are working fine. Missing only moonlight 2.0...

That's not a solution. 

> **mikewhatever said:**
> The OP will need to compile from source, since mozilla only provides 32bit binaries for Linux.

Not really. Although Mozilla don't officially releases a 64bit version, you can get if from Mozilla's nightly repositories or from *ubuntu-mozilla-daily* or *mozillateam/firefox-stable* ppa. I use it and it works like a charm. Only takes 5 seconds to load, even with [ 50 extensions installed](https://addons.mozilla.org/en-US/firefox/collection/lovinglinux).

> **Objekt said:**
> Yes, this is why I used Ubuntuzilla.  I don't have the slightest idea how to compile Firefox (or anything else).  Ubuntuzilla handles the details automagically, except I did have to fix the Flash plugin manually.

Ubuntuzilla is one of my favorite methods of installation, but is not recommended for 64bit users.

@ Objekt

See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). I explains how to get and install the 64bit version of Firefox and will provide several tips on how to optimize it.

If it behaves the same after installing the 64bit version, then try to create a new profile with this command:

```
firefox -P
```

This will force Firefox to start with the Profile Manager, from where you can create a clean profile.

If the new profile solves the problem, then you might have a corrupted profile, sub-optimal settings or some extension that could be slowing Firefox. To check if it is an extension, start your old profile with this command:

```
firefox -safe-mode
```

This will disable all extensions. If it works perfectly, then you will know it is one of your add-ons.

Please feel free to ask for additional support here, on the indicated thread or on my blog, if you need.

---

### Post by lovinglinux on 2010-02-11
To complement my previous post....

> **Objekt said:**
> Is the Linux version of Firefox 3.6 supposed to be substantially faster?

20% according to Mozilla. I haven't benchmarked it yet.

> **Objekt said:**
> Could this be an inherent problem with running 64-bit Ubuntu?

The 64bit should run better than the 32bit, but not miraculously faster. I have tried the 32bit on my machine and couldn't see much difference, although I had problems with the theme integration. I use KDE.

> **Objekt said:**
> Also Firefox does not quit normally.  When I close the window, it goes away instantly, but the Firefox process almost always keeps running in the background.  I know this because I am almost always asked whether I want to terminate the Firefox process when I try to log out or restart the system.

I'm also experiencing this problem with Firefox 3.6 64bit. I suspect it could be caused by an extension, since I override compatibility of some of them. But I still need to further investigate this.

> **Objekt said:**
> To clarify, Firefox opens slowly, and general operations - opening menus, browsing, etc. - are noticeably slower than using the same version was under Windows XP.  Not sure why, and I'm open to suggestions on how to fix.

Also: I have desktop effects turned off.  My router is set to use the OpenDNS servers.  Anyway it's not so much a problem with how fast pages load, it's all the other things Firefox does which are slow: opening/closing tabs, drawing menus, etc.

Looks like you need to optimize Firefox databases (see tutorial link on my previous post).

---

### Post by Objekt on 2010-02-16
I haven't gotten to any of the optimization stuff yet, but I did upgrade to Firefox 3.6 in the meantime.  It might be a little faster, but I have no way to measure speed objectively.  Lately I've been running Win XP (ugh) a lot because of a game that I can't run in a Virtual XP machine.

The Firefox speed problem could be an add-ons problem, and not really a Firefox problem at all.  I need to create an alternate user profile with no add-ons to test that idea.

---

### Post by Objekt on 2010-02-20
Ran the database optimization.  I don't know how much it helped, but 3.6 does seem noticeably faster than 3.5.7.  I'm marking this one "solved."

---

### Post by Son of William on 2010-05-21
I had this problem with 9.10 and got it again when i installed 10.04.  I found the solution in this thread:

[http://ubuntuforums.org/showthread.php?t=1310366](http://ubuntuforums.org/showthread.php?t=1310366)

which directed me to: [https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

It solved the problem right away.

---

