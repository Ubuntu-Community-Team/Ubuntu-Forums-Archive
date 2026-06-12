---
title: "Unable to access USB devices in Virtualbox 3.0.6"
date: 2009-09-22
forum: General Help
---

### Post by azzronulation on 2009-09-22
Hey, I recently had an accident with formatting windows,and completely removed it, so as a result i decided to go to Ubuntu, I've tried it many times before but never found a decent use for it purely because iTunes deosnt support linux, and iTunes is a big part of my life (iPhones & iPods).. anyway enough of the drabble.

I've got the latest PUEL version of VirtualBox (3.0.6) I've managed to get Vista Home to run on it, but the only problem i'm having is getting my external hard drive (where all my music is) to enable, in the devices it IS there, but it has been greyed out. can anyone help me with a solution?

Thanksss.
(new linux user)

---

### Post by cjbuchmann on 2009-09-28
I've got the same problem here. Running Virtual Box 3.0.6 (obviously the closed src version), and I can't seem to get the USB's running. When I plug in a USB and Virtualbox is running, right clicking the USB icon at the bottom will show a list of greyed out checkboxes, each corresponding to the different USB devices I have. Also, when I try to mount my external HDD via USB, it mounts directly to my UBUNTU Jaunty Distro, even when focus is given to the Guest OS.

Here's my setup :

Running Ubuntu Jaunty (GNOME)
Virtual Box 3.0.6 (Closed Src, USB Supported)
Win XP Professional as the Guest OS (the V-PC)

Any help here would be greatly appreciated.

thanks!

---

### Post by cjbuchmann on 2009-09-28
Okay, so a little update. This is apparently ONLY a permissions problem.

According to [http://en.gentoo-wiki.com/wiki/VirtualBox#USB_Devices_Grayed_Out](http://en.gentoo-wiki.com/wiki/VirtualBox#USB_Devices_Grayed_Out)

"If you can see your devices, but they are greyed out it is a permission problem:"

they recommended using "getent group usb" to get the Group ID (GID) for your USB, however, I don't have a usb group id, because I didn't have usb group. 

Going to "System -> Administration -> Users and Group -> Mange Groups, I looked for a usb group but didn't find one. I proceeded to add one, and made both the root and myself a member of it (just to see what would happen) 

Then I edited my fstab file "sudo gedit /etc/fstab" with the following entry :
none /proc/bus/usb usbfs devgid=85,devmode=664 0 0

My usb (the group I just created) had a GID of 1001 so I replaced the
"devgid" of 85 with that.

Doing a quick log out and logging back in, I tested it only to find that
it still didn't work. 

So, if it's a permission error, then how do I go about giving it the
proper permissions?

thanks!

---

### Post by cjbuchmann on 2009-09-28
Okay, so in the end this is what worked for me. 

Under System -> Administration -> Users and Groups -> [Your User] -> User Privileges

Check "Use Virtualbox".

Log out, and log back in. Voila!

Hope this helps for anyone else out there having the same problem.

Note - I did this only after doing the steps described in my previous post, so I'm not positive if it was the combination of them that worked or if it was just this step.

---

### Post by Verzweifler on 2009-10-21
> **cjbuchmann said:**
> 
Note - I did this only after doing the steps described in my previous post, so I'm not positive if it was the combination of them that worked or if it was just this step.

I can positively confirm that simply checking "Use Virtualbox" and logout/login fixed it for me.

Thanks a lot

---

### Post by prop99 on 2010-01-01
I have had all these problems too. Read a lot of forums but none has been really helpful. 

It seemed to be a permissions problem so I looked into the udev rules. I got hopeful when I noticed a few Virtualbox rules that were to set the group to "vboxusers" on usb devices BUT the permissions (in /dev/...) listed root as group. Strange...

After some thinking and more reading, I issued the command:

[INDENT]**sudo udevadm control --reload-rules**[/INDENT]

and now it works!

Maybe it will work until I reboot, or forever, I don't know.

Fyi, I am running vbox 3.1.2 with ubuntu 9.10 host and xp sp2 guest.

PS. Shouldn't udevd reload the rules automagically as they change? I thought this was done with the "inotify" thingy...

---

### Post by Uncle Spellbinder on 2010-01-01
> **cjbuchmann said:**
> Okay, so in the end this is what worked for me. 

Under System -> Administration -> Users and Groups -> [Your User] -> User Privileges

Check "Use Virtualbox".

Log out, and log back in. Voila!

All the selections under System -> Administration -> Users and Groups -> [Your User] -> User Privileges are grayed out. :-?


And there is no "use virtualbox" there anyway. :-k

---

### Post by prop99 on 2010-01-05
> **Uncle Spellbinder said:**
> All the selections under System -> Administration -> Users and Groups -> [Your User] -> User Privileges are grayed out. :-?

You need to have root privileges. Click the key symbol to make changes.

> **Uncle Spellbinder said:**
> And there is no "use virtualbox" there anyway. :-k
Virtualbox sometimes does not create the vboxusers group, it seems. Try reinstalling Virtualbox. That did it for me (when I was trying the OSE version).

---

