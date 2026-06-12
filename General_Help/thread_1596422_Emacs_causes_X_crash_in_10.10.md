---
title: "Emacs causes X crash in 10.10"
date: 2010-10-14
forum: General Help
---

### Post by rodders on 2010-10-14
Hi,

Since upgrading to Ubuntu 10.10 I have been unable to use Emacs23. Upon starting Emacs, it immediately causes X to crash and I am returned to the login screen.

I thought of looking for a log file and providing it here or in a Launchpad post to shed some light on the problem, but I don't know which log I could provide (if there is one). Could someone suggest one?

FYI, this also happens in Awesome WM.

Any help would be much appreciated... I really need my Emacs :)

---

### Post by rodders on 2010-10-14
After going away and simmering for a while, I returned and got on with work, until another application caused the same crash, this time Skype 2.1.

I have a dual monitor set-up, so I logged in with only a single screen active and everything worked. I tried switching from Xinerama to TwinView in the NVidia settings app, and since then, Emacs and Skype work OK on my dual-monitor set-up.

So it seems Xinerama could be the problem candidate...

---

### Post by bjtuna on 2010-10-14
Trigger the crash and when you log back in, immediately check /var/log/Xorg.0.log and /var/log/Xorg.0.log.old and see if there is a segfault down near the bottom.  If so, post the segfault part here.

---

### Post by yojimbo-San on 2010-10-14
Sounds like you are being bitten by [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539)

Please subscribe to that bug, and post any details that will be helpful.

---

### Post by sstvinc2 on 2010-12-28
Apparently the bug is known and fixed, but we're just waiting for the fix to get integrated into the system.  In the meantime, you can install the fixed version.

Here's a quick how-to from the bug page.

1. Add the developer's repository

```
sudo add-apt-repository ppa:jared-bunting/xorg-xserver-650539
```2. Update your respositories

```
sudo apt-get update
```3. Upgrade your packages

```
sudo apt-get upgrade
```This should upgrade the xserver-xorg-core and xserver-common packages.  Restart X (log out or restart) and you should be good to go.  I was having the same problem (couldn't run emacs) and this fixed it right up.

---

