---
title: "uninstalling python screwed up my system. Need to reinstall whole ubuntu.. help"
date: 2011-01-23
forum: General Help
---

### Post by mmistroni on 2011-01-23
Hello all
 yesterday evening i screwed up my Ubuntu 10.04 completely by accidentally removing python 2.5.6 (i wanted to install 3.1.. got a lot of notification of deletion and reinstallation and naively thought it was ok).
Now i tried to boot from commandline and run sudo apt-get --fix-broken but i cannot connect to network as i keep on get error message like 'cannot find site [http://archive.ubuntu.com](http://archive.ubuntu.com) or something like that.
I guess my only option will be to do a 10.04 reinstallation (i copied the ISO file on my USB).  THe only problem i have is will i have lost all the data in my home directory if i do an installation?

will the new installation detect the existing one, or allow me to do a copy of the data?

any suggestions are welcomed....

w/kindest regards
 marco

---

### Post by coffeecat on 2011-01-23
If your home directory is in your root partition and you reformat that when you reinstall, then yes it will be lost. However, I remember reading that if you select the manual/advanced option at the partitioning stage of the installer, select your root partition for install but deselect the format option, then the installer will delete everything except /home (and contents) and do an installation without you losing your home. I have not tested this for myself so I don't know how reliable this is.

There is another option, though. If you can connect to the internet in the live CD session, you could boot up the live CD, chroot into your HD Ubuntu and do your apt-get commands in a chroot environment, hopefully repairing your hard drive installation. If you would like to try that, post back and I'll give you the commands necessary.

---

### Post by mmistroni on 2011-01-23
Hello
 ys pls, send me the instruction.. i want to try to save as much as i canf rom my existing linux

thanks and regards
 marco

---

### Post by coffeecat on 2011-01-23
@mmistroni, removing python has broken a lot of applications as you've discovered. The following relies on apt-get being still unbroken. I've checked apt's dependencies and python doesn't seem to be a necessary dependency so I'm fairly confident this will work. Let's see. Post back if it doesn't.

OK, here goes. Chroot-ing from a live CD. Boot up the Ubuntu live CD and select 'try Ubuntu', not the installer, to get to the live desktop. Make sure you are connected to the internet otherwise you won't be able to download the python packages necessary to repair your system.

You need to know which partition on your hard drive your Ubuntu root partition is. I'll assume it's /dev/sda5, but you need to change this as necessary. If you are not sure which it is, post the terminal output (from the live CD) of these commands and we'll take it from there.

```
sudo fdisk -lu
df -Th
```Now to the chroot. First mount your Ubuntu root partition:

```
sudo mount /dev/sda5 /mnt
```Remember to change sda5 as appropriate.

Now change to root for convenience:

```
sudo -i
```The prompt will change to '#'. Be careful from now on. You will have full root powers and will not have to use sudo.

First we need to be sure that you can access the internet from the chroot environment:

```
cp -L /etc/resolv.conf /mnt/etc/
```Now for the chroot. Do each of these commands one after the other and check for typos before hitting enter.

```
mount --bind /dev  /mnt/dev
mount --bind /dev/pts  /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys  /mnt/sys
chroot /mnt /bin/bash
```You are now "in" your Ubuntu root partition, but to remind you:

```
export PS1="(chroot) $PS1"
```Your terminal prompt now reminds you where you are.

To repair your installation, try what you tried to do before:

```
apt-get --fix-broken
```Note that you do not have to use sudo. If you get errors, or it doesn't seem to work, or you don't see any python being installed, try this:

```
apt-get install --reinstall ubuntu-desktop
```The package ubuntu-desktop is a metapackage which depends on everything that makes up the Ubuntu gnome GUI. Several dependent apps have python as dependencies so that should also fix things.

Once that's all finished:

```
exit
exit
exit
```That's right: three times. Now reboot and see if your Ubuntu is fixed.

---

### Post by mmistroni on 2011-01-24
Thanks a lot coffeecat!!
you saved my day :)

Now, how can i upgrade to python 3.1 without messing up system again? is it safe to upgrade using Synaptic package manager?

regards
 marco

---

### Post by coffeecat on 2011-01-24
Do you have a particular reason for wanting to upgrade to python 3? Python is needed by so many things that it is safer to stick with the version that comes with the package manager. I think you'll probably enter dependency hell if you try to upgrade Python in Ubuntu 10.04 with results you've already experienced. Natty Alpha is only on Python 2.7, and it was a rocky ride during the upgrade from 2.6 a couple of weeks or so ago.

---

### Post by cgroza on 2011-01-24
> **mmistroni said:**
> Thanks a lot coffeecat!!
you saved my day :)

Now, how can i upgrade to python 3.1 without messing up system again? is it safe to upgrade using Synaptic package manager?

regards
 marco

You can install it, but whatever you do, DO NOT REMOVE THE ONE YOU HAVE NOW! To run python 3.1
after the install you can run python3.1 from a terminal or install IDLE that uses python3.1.

---

