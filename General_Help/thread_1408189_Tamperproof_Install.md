---
title: "Tamperproof Install"
date: 2010-02-16
forum: General Help
---

### Post by micromen on 2010-02-16
Hi,
We are complete Ubuntu novices (exclusively Windows experience) but wish to create a 'tamperproof' PC for general use in our canteen, ie facebook, Youtube. We want to prevent downloaded files/data/cookies etc on the PC.

We think running Ubuntu via the Live CD or USB is best but want to be able to create a tailored Live CD/USB that allows us to initially set the network settings (to keep our ISA firewall happy/not bypassed), install Flash etc addons in firefox before the final ISO/Burn.

Alternatively if we could install on the hard disk/USB and then easily rebuild the original config each day that would be a good alternative!
What is the easiest way to do this?
Thanks.

---

### Post by Jackzor on 2010-02-16
> **micromen said:**
> Hi,
We are complete Ubuntu novices (exclusively Windows experience) but wish to create a 'tamperproof' PC for general use in our canteen, ie facebook, Youtube. We want to prevent downloaded files/data/cookies etc on the PC.

We think running Ubuntu via the Live CD or USB is best but want to be able to create a tailored Live CD/USB that allows us to initially set the network settings (to keep our ISA firewall happy/not bypassed), install Flash etc addons in firefox before the final ISO/Burn.

Alternatively if we could install on the hard disk/USB and then easily rebuild the original config each day that would be a good alternative!
What is the easiest way to do this?
Thanks.

You could give this a try.

[http://www.webupd8.org/2009/07/deep-freeze-like-software-for-ubuntu.html](http://www.webupd8.org/2009/07/deep-freeze-like-software-for-ubuntu.html)

---

### Post by ironclaw on 2010-02-16
I think something that allows you take a snapshot of your system and restore quickly back to it would be best.

I believe [UnionFS]("http://www.filesystems.org/project-unionfs.html") allows that to be done by mounting a snapshot of your desired system as read-only and transparently overlaying an empty read-write file system on top of that so that applications can still run normally. I haven't used it, though, so hopefully someone else with more experience can join in here.

Personally, I use [Btrfs]("http://btrfs.wiki.kernel.org/index.php/Main_Page") to achieve the same effect on my netbook, and it's been without any problems so far, but I wouldn't recommend it since the latest release is still unstable.

---

### Post by ironclaw on 2010-02-16
> **Jackzor said:**
> You could give this a try.

[http://www.webupd8.org/2009/07/deep-freeze-like-software-for-ubuntu.html](http://www.webupd8.org/2009/07/deep-freeze-like-software-for-ubuntu.html)

Wow, Lethe looks like a very easy to implement solution. Nice!

---

### Post by mcduck on 2010-02-16
Another option is to simply make a normal install, setup automatic login to a normal (non-admin) user account and then lock down the desktop. Gnome has pretty good configuration options for locking down the system, including the possibiluíty of removing every panel/launcher/menu entry you wish to hide and then locking down menus and panel setup, and disabling any writes to disk...

---

### Post by 3rdalbum on 2010-02-16
Log in with the "guest" account - all the Gnome settings will be at default, the guest account is extremely unprivileged so they can't change settings, and the contents of the guest home directory is erased on logout.

Set the "login window" settings so that, after 10 seconds at the login screen, it will log into the guest account.

---

### Post by mcduck on 2010-02-16
> **3rdalbum said:**
> Log in with the "guest" account - all the Gnome settings will be at default, the guest account is extremely unprivileged so they can't change settings, and the contents of the guest home directory is erased on logout.

Set the "login window" settings so that, after 10 seconds at the login screen, it will log into the guest account.

I thought the guest account required confirmation from some "real" user, so you can only start it from some logged-in user's session, not directly from the login screen?

---

### Post by 3rdalbum on 2010-02-16
> **mcduck said:**
> I thought the guest account required confirmation from some "real" user, so you can only start it from some logged-in user's session, not directly from the login screen?

Ahh... maybe you're right. I'm sure it used to be accessible from the login screen last time I looked.

---

### Post by prshah on 2010-02-16
> **micromen said:**
> a 'tamperproof' PC for general use in our canteen, ie facebook, Youtube.
What is the easiest way to do this?


You are possibly looking for a "lockdown" procedure. [Here's a detailed thread]("http://ubuntuforums.org/showthread.php?t=707688") that outlines the steps you need to take.

You can also consider using a special ["kiosk" version of Ubuntu]("http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm") (Note that the link is a little dated, but will give you the general idea) or using [Opera's kiosk mode]("http://www.opera.com/support/mastering/kiosk/")

---

### Post by mcduck on 2010-02-16
> **3rdalbum said:**
> Ahh... maybe you're right. I'm sure it used to be accessible from the login screen last time I looked.

I just tried it, and the guest account that exists by default is indeed only accessible from logged-in user's session, trying to start it from login screen isn't possible.

I suppose that's because such user doesn't really exist on the system, it's only created at the time you start the guest session and destroyed afterwards.

---

