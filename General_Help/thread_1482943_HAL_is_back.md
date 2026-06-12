---
title: "HAL is back???"
date: 2010-05-14
forum: General Help
---

### Post by lviggiani on 2010-05-14
Hi guys,
I have a big doubt... I have upgraded from Karmic to Lucid.
Reading the release notes of Lucid, I've seen the Lucid has completely removed HAL for a faster boot. However this morning the update manager proposed me an update for the HAL package. This means that it is still installed on my system.
So, is my computer still using HAL? Can I get rid of it?
Thanks, Luca.

---

### Post by lviggiani on 2010-05-14
> **lviggiani said:**
> Hi guys,
I have a big doubt... I have upgraded from Karmic to Lucid.
Reading the release notes of Lucid, I've seen the Lucid has completely removed HAL for a faster boot. However this morning the update manager proposed me an update for the HAL package. This means that it is still installed on my system.
So, is my computer still using HAL? Can I get rid of it?
Thanks, Luca.

I think I found the answer here:
[http://federicomoretti.name/article/hal-is-still-on-ubuntulucid/]("http://federicomoretti.name/article/hal-is-still-on-ubuntulucid/")

Does anyone have more info?

---

### Post by Georgia boy on 2010-05-14
So, we should go ahead and do the updates for Hal also then right? I too thought that I had read it had been removed from Lucid and a lot of people were upset about it. Guess it's still here and needs the updates?

I didn't do any updates yet until I make sure.


Also, what is the unattended upgrades about? Has that always been going on in the background without us knowing or is it something new?


Thanks
Tom

---

### Post by mcduck on 2010-05-14
HAL was removed from the base Ubuntu install, but it's still used if you use any drivers or other stuff that needs it.

(in other words, *Ubuntu* doesn't need HAL any longer, but *you* might.. ;))

If you are offered update for a package that means that you already have it installed (you'll never see updates for packages you don't have!), so you should of course install the update for it as well. Probably your hardware needs some driver that still uses HAL.

What comes to unattended updates, yes, that has always been an option. It simply allows to download and/or install security updates in the background instead of asking you when to install them.

---

### Post by Copernicus1234 on 2010-05-14
Arch Linux has Xorg 1.8 in testing and that version doesnt require Hal at all. Many Arch users were happy to get rid of it during April. Here is a link to their forum discussions: [http://bbs.archlinux.org/viewtopic.php?pid=756445]("http://bbs.archlinux.org/viewtopic.php?pid=756445")

But there are some issues still with certain applications needing it, so thats probably why Ubuntu devs are choosing to run a very old version of Xorg that still needs hal. Its more stable. Im also still running the older version on my Arch machine since I think its more stable at the moment.

Some info from one of my current systems:

Name           : hal
Version        : 0.5.14-2
URL            : [http://www.freedesktop.org/wiki/Software/hal](http://www.freedesktop.org/wiki/Software/hal)
Licenses       : GPL  custom  
Groups         : None
Provides       : None
Depends On     : dbus-glib>=0.82  libusb>=0.1.12  udev>=146  filesystem>=0.7.1-5  hal-info>=0.20090716  eject  dmidecode  pciutils>=3.0.2  usbutils>=0.73-5  pm-utils>=1.2.5  
                 consolekit>=0.4.1  util-linux-ng>=2.16  
Optional Deps  : None
**Required By    : exo  gnome-vfs  podsleuth  thunar  xorg-server  **
Conflicts With : None
Replaces       : None
Installed Size : 2220.00 K
Packager       : Jan de Groot <jgc@archlinux.org>
Architecture   : i686
Build Date     : Sun 07 Mar 2010 02:40:25 PM CET
Install Date   : Thu 13 May 2010 01:36:26 PM CEST
Install Reason : Installed as a dependency for another package
Install Script : Yes
Description    : Hardware Abstraction Layer

---

### Post by philinux on 2010-05-14
If I mark hal for removal nothing else needs to be removed. Therefore it is installed and will get updates but currently nothing on my system uses/depends on it.

---

### Post by psusi on 2010-05-14
> **philinux said:**
> If I mark hal for removal nothing else needs to be removed. Therefore it is installed and will get updates but currently nothing on my system uses/depends on it.

Bingo... if you don't want it, uninstall it like any other package you don't want.  It is no longer required in lucid, but if you upgrade from karmic, you already have it and upgrades don't go removing software you already have if they don't have to.

---

### Post by philinux on 2010-05-14
> **psusi said:**
> Bingo... if you don't want it, uninstall it like any other package you don't want.  It is no longer required in lucid, but if you upgrade from karmic, you already have it and upgrades don't go removing software you already have if they don't have to.

This was a clean lucid install by the way, for anyone following this thread.

---

### Post by mcduck on 2010-05-14
> **philinux said:**
> This was a clean lucid install by the way, for anyone following this thread.

Same for me, a fresh install of the final 10.04 release and HAL is installed.

I just checked in Synaptic, and removing *hal* and *hal-info* doesn't remove anything else, but removing *libhal* on the other hand would remove most of the desktop stuff.

---

### Post by timgood on 2010-05-14
I installed Arista Transcoder from Ubuntu Software Centre - this seems to have installed hal as it is only arista that will be removed if I remove hal.

---

### Post by Georgia boy on 2010-05-14
I too have a clean install. Completely got rid of 8.04 and Windows. So what's showing is what was installed when I put Lucid on. So, guess I'll go ahead and do all the updates tomorrow. Might even have more to do along with what came out today knowing the way things go right? 

Thanks for the information. Didn't know what was going on. I know that my system is set up to ask before updating so if I go ahead and install the updates for the automatic updating will anything change or just what is already there?

Have a great day and a wonderful weekend eveyone!!

Thanks

Tom

---

### Post by theozzlives on 2010-05-14
Interesting discussion. In the A+ course they lead you to believe that the Hardware Abstraction Layer is a necessary part of the OS. I guess I'll have to wait for the Linux+ course.

---

### Post by mcduck on 2010-05-14
> **Georgia boy said:**
> I know that my system is set up to ask before updating so if I go ahead and install the updates for the automatic updating will anything change or just what is already there?
After release Ubuntu versions only get updates for security reasons and to fix more serious bugs, never just to add new features.

So updates will never add new stuff or change ho things work, the only replace a package you already have installed with a new version of the same package. So yes, you'll definitely want to install the updates, and no, nothing is supposed to change when you install the updates (apart from the security holes getting fixed and some bugs disappearing).

Unless you are running some third-party software or drivers that you know to only work with some exact versions of some packages, there really isn't any need to even think about if you should install updates or not. They are just fixed versions of the stuff you already have so you'll definitely want to install them. :)

---

