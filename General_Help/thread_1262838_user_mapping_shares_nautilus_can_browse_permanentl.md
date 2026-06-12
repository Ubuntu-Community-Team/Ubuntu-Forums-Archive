---
title: "user mapping shares nautilus can browse permanently"
date: 2009-09-10
forum: General Help
---

### Post by linuxcss on 2009-09-10
I am looking for an  automated way to mount shares from a windows XP machine and soon windows server, that provides the following:

1) when mounted the share icon appears on the desktop
2) user without superuser privileges can unmount them (** without issue below)
3) if user can browse them through places->network->server they can map them permanently without having superuser privileges. By permanently I mean on reboots they do not have to click on anything to remap. Example: So if one was to reboot machine and use openOffice open dialog they would see the share there and would be able to browse or open and change files within the openOffice environment.
 
  I have found a few ways but NONE that fulfill all 3 above.
 
 Mounting the drive in /media folder satisfies number 1, number 2 (**) can be had though dangerous in having user mount in their home directory space, by doing that it allows user to also potentially remove the mountpoint and blow away everything too easily.
 

 Ideally If one could make the mounted shares via nautilus browsing method permanent that would satisfy all my needs and allow the user to map and unmap whenever they have the privilege of browsing the server shares.
 

 I thought about creating a launcher with  'nautilus [smb://server/sharename](smb://server/sharename)' and placing it in startup, but I do not want the browser window opened at startup and having  multiple shares each with a launcher makes more Desktop clutter.
 

 Is there a way to call the underlying code that nautilus employs to mount shares without nautilus being invoked? Or a call to nautilus to browse but immediately exit [which leaves share mounted].

I am running ubuntu 9.04

---

### Post by Penguin Guy on 2009-09-10
Try adding an fstab entry, you can do that by adding a line to [COLOR="Green"]/etc/fstab[/COLOR] which tells the system what it should mount at startup. You can edit this file by running [COLOR="Green"]gksu gedit /etc/fstab[/COLOR]. Add the line: [COLOR="Green"]//**server/folder** /media/**name** smbfs username=**username**,password=**password** 0 0[/COLOR] to the end.

Source: [http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/)

---

### Post by linuxcss on 2009-09-10
I already have that working that way but that does NOT give a user the capability to mount and unmount shares one can browse on servers all by them self.

---

### Post by wentzr on 2009-09-10
There is a wiki that *should* be able to get you from here to there.. [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Just know (you probably do but just to point out the "why do i have to tell it to do this" part many linux users face with things from xorg to fstab entries) - what you are asking linux to do is not considered secure in any way shape or form. There's a reason network volumes aren't accessible via the desktop w/o manual fstab entries and some finagling and there is good reason for it. :) automount in general is considered a backdoor. . fortunately the absolute beauty of linux is that if you are in the driver's seat, you can make it do whatever you want, with a little digging and asking around. . . linux has never proved me wrong there! ! !

good luck and post back if you have any more problems.

---

