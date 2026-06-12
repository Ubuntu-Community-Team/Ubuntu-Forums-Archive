---
title: "System Restore for Ubuntu? (serious problems)"
date: 2009-10-15
forum: General Help
---

### Post by CD27 on 2009-10-15
So I was skimming through the possible applications I could install through the applications installer in every ubuntu OS. I saw one called "Remove Orphaned Packages". I was like, "Ok, hmmm....maybe this would help me keep my system clean after i install software and can't figure out how to get it to work." So ran it, and it got rid of a butt-load of stuff...which happened to be used ALL THE TIME, daily. Now my system is practically useless to me, because I can't figure out how to revert what I did. Does ubuntu have a system restore feature? If not, then why not? Why isn't there one automatically built into the system? This is a MUST with any operating system; the ability to revert back to a previous time.

If I install software and don't intent to use it or am having conflicts with it, I should be able to revert back to just before it was installed. I can't remember all the commands I ran in terminal in a 24 hour period, much less what commands THOSE commands ran. And even if I could, I just don't know enough about the system to figure out which one is causing the problems or which one is missing.

So does anyone know of any kind of system restore option already in ubuntu or one I can download after I reinstall the OS (looks like I'm going to have to reinstall the OS because I have no idea of knowing what was removed and how to get it back).

Thanks!!!

---

### Post by skillllllz on 2009-10-15
Open a terminal and run this command:

```
sudo apt-get remove ubuntu-desktop
```Then run this command:

```
 sudo apt-get install ubuntu-desktop
```This will reinstall the "ubuntu-desktop" meta-package, which will invoke the installation of any default packages you may have removed. 

;-)

---

### Post by oldfred on 2009-10-16
It may be possible to get your system working but I do not know if any of the history or logfiles will show what you have installed. I quickly looked an dpkg.log in /var/log may have some info.

I do not know which orphan program you ran but this scares the heck out of me:
Frontend for deborphan
GtkOrphan will report as "orphaned" all those installed packages that are not dependencies for any other. In this way, for instance, packages such as gparted, ubuntu-desktop, wine will be listed too, as they are "top-level" packages and no other package depends on them. Now you can traverse this list and right-click->hibernate each package you want to keep and that you don't want to be reported as orphaned anymore.

If you do not know what to save you delete way too much!:(

Did you do any backups? Backups are a regular topic here. I separately export to another drive a packages list and most system config files that I may have edited. Packages is a list of all installed programs, you can get it from synaptic or command:
dpkg --get-selections | grep -v deinstall > ubuntu-files

You can go back into your system with a chroot command from a liveCD and do all the updates to probably get it working again.

I copied this from another post:
Seldom necessary, you can just mount and chroot the broken *buntu from a Live CD and then use apt to reinstall parts and pieces - apt-get update, apt-get upgrade, etc.

Of course you must first know what partition you want to mount, in this example I'm using sda5:

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf (may or may not be necessary to establish an internet connection)
sudo chroot /mnt
apt-get update
apt-get upgrade
And then run whatever else commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by skillllllz on 2009-10-16
Whoa! Let's not overwhelm him, I'm not sure he's ready for all that just yet. If his Internet connection still works, reinstalling the ubuntu-desktop meta-package ought to do the trick.

---

### Post by CD27 on 2009-10-16
well ubuntu works fine. I'm doing all of this right now straight from the same OS. It's just that alot of my software, like gyachi, firestarter, compiz, and several others no longer function. In fact, I'm even missing the icons for them on the system bar, it just shows a black box with the "no" sign (circle with a line through it) in it. I'll try the first one, and yes, you're right, I really don't have a clue what you just said lol. 

I AM a computer technician for the military though, but we work on windows based computers, not linux, so this is a whole new breed for me.

---

### Post by skillllllz on 2009-10-16
Well,  the commands I gave you will put back all the default software that was there when you first installed Ubuntu. Any additional software you installed after that will need to be installed again.

The good news is that all your preferences and settings for most of your applications should still be intact and upon installing your apps, you should be able to pick up right where you left off in them.

Let me know how it all goes.

---

### Post by CD27 on 2009-10-16
Eh, I'm just going to reinstall 9.04. I'm running a beta right now anyways. I did what you said and it really didn't do anything, everything still looks all messed up.

---

