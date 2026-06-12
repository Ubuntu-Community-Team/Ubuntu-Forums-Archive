---
title: "Unable to use PartitionManager"
date: 2012-06-05
forum: General Help
---

### Post by happyusers on 2012-06-05
I am a rather new user of Ubuntu. I had trouble with some nasty virus on a WXP station and wanted to format all my USB keys. I thought a good way was to do that on my Ubuntu station but.. after having installed PartitionManager, I cannot use it, it asks for a kdesu root password I dont know. I have a ubuntu password and it is the only one I have to use normally. What can I do to run PM?

---

### Post by Deepak J on 2012-06-05
While installing you must have entered a root password. Try recollecting it..

I don't know if there is another way, wait for other better experienced users to intervene..

---

### Post by dino99 on 2012-06-05
the password is your password user session

are you using kde or gnome ?

---

### Post by happyusers on 2012-06-05
Yes I have given a password for installation but it is associated to ny user name, not to root user. If I use that password, I get two message boxes, the first one says "Sorry Kde su" unable to run command "usr/bin/patitionmanaget --dontsu" and the second one says "no root privileges.. you can run partitionmanager without but...". Any clue? I dont know really if I use kde or gnome? Is it a way to know? I have installed native ubuntu. Thank you.
BTW I am using ubuntu 12.04 LTS

---

### Post by dino99 on 2012-06-05
if you have installed:
- ubuntu, then gnome is used
- kubuntu, then its kde
- xubuntu, xfce is used
- Lubuntu, fxce is used

so i suppose you have ubuntu and gnome. To partition with gnome install gparted (which is a gnome app), not partitionmanager (which is a kde app)

to do that:

sudo install synaptic
sudo synaptic

select partitionmanager for complete removal (and the dependencies too)

then about the usb formatting: note that you must first unmount them before to be able to format.

by default never open a root session for security reason, open a user session then use sudo or gksu (for graphical app)

---

### Post by coffeecat on 2012-06-05
> **happyusers said:**
> Yes I have given a password for installation but it is associated to ny user name, not to root user. If I use that password, I get two message boxes, the first one says "Sorry Kde su" unable to run command "usr/bin/patitionmanaget --dontsu" and the second one says "no root privileges.. you can run partitionmanager without but...". Any clue? I dont know really if I use kde or gnome? Is it a way to know? I have installed native ubuntu. Thank you.
BTW I am using ubuntu 12.04 LTS

You say Ubuntu in your OP, but partitionmanager is a KDE app. If you installed Ubuntu 12.04, you will have a purple wallpaper by default and a dock called the launcher on the left. Kubuntu/KDE will have a grey or blue theme and a taskbar at the bottom. Max/min/close buttons are on the left in Ubuntu/Unity (gnome) and on the right in Kubuntu/KDE.

I've tried installing partitionmanager in Ubuntu/Unity and get the same error. It may be a problem running this KDE app in gnome - possibly. If you are running Ubuntu, try installing Gparted. You should have no password problems with that - use your login password. You can install Gparted to KDE, but it will probably bring in a lot of gnome libraries as dependencies.


> **Deepak J said:**
> While installing you must have entered a root password. Try recollecting it..

No - you are asked for a password for your user account which has admin privileges during installation, not the root account. For more, see here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by happyusers on 2012-06-05
Thank you everybody. I am for the moment a little bit lost among all those environments. So I will uninstall partitionmanager and install gparted. Thanks a lot

---

### Post by oldfred on 2012-06-05
I always install gparted, but one of the reasons it is not installed is you cannot work on mounted partitions. And any logical partition mounted in effect mounts the extended partitions, so you cannot modify any other logical partitions.

Although you can reformat your USB keys from your install or edit any other drive or device, any partitioning task on your install hard drive should be from a liveCD. And from liveCD you usually have to swap-off to umount the swap partition as liveCD like to use swap to speed up activities.

---

