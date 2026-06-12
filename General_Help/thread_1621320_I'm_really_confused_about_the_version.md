---
title: "I'm really confused about the version"
date: 2010-11-14
forum: General Help
---

### Post by leinad177 on 2010-11-14
Ok, i was running karmic. Then i went to the update manage thingy and updated all. now it says im running 10.04.
I just wanted to get it ready for an upgrade to 10.10 via disk

I have the 10.10 disk and now im wondering how in the world i'm meant to install 10.10.

The disk is Labeled "Ubuntu 10.10 i386".
I downloaded an iso from a file mirror because my internet has a quota which i cant exceed.

Selecting the disk just opens it up like a folder.

EDIT: i tried gksu "sh /cdrom/cdromupgrade" and it didn't work

---

### Post by Quackers on 2010-11-14
Effectively, upgrading using an Ubuntu cd is the same as installing fresh. All old setting and programs will be lost (unless you have backed up several files/folders). To do it you would boot from the Ubuntu cd.
If you just want to upgrade your present system to Maverick Meerkat (v 10.10) you can do that with update manager which should show you that an upgrade is available.

---

### Post by leinad177 on 2010-11-14
The update manager said that my system is up to date.

---

### Post by Monotoko on 2010-11-14
The only way to do it then is to get all your things off the computer then reinstall using the 10.10 disk.

---

### Post by matt_symes on 2010-11-14
Hi

This is older but it may help. See section three. It seems you used to be able to do it. Maybe you still can.

[http://ubuntu.igameilive.com/2009/04/3-ways-to-upgrade-to-ubuntu-904.html](http://ubuntu.igameilive.com/2009/04/3-ways-to-upgrade-to-ubuntu-904.html)

This is newer.

[http://askubuntu.com/questions/12818/can-i-upgrade-my-ubuntu-10-04-to-10-10-using-livecd-bcoz-dont-have-stable-conn](http://askubuntu.com/questions/12818/can-i-upgrade-my-ubuntu-10-04-to-10-10-using-livecd-bcoz-dont-have-stable-conn)

and this

[https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)

It seems you need the alternative CD. If you dont have that i would do a fresh install after backing up your data.

Kind regards

---

### Post by StarLab on 2010-11-14
> **leinad177 said:**
> The update manager said that my system is up to date.

At the bottom of the Update Manager, click the settings button. At the bottom of the setting screen is an upgrade option. By default it's set to get LTS releases only. Change this to Normal releases and you should get an upgrade button when back on the main update screen. 

HTH

---

