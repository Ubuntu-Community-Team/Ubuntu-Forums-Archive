---
title: "Changes revert back to normal after restarting"
date: 2011-11-23
forum: General Help
---

### Post by ubuntuforums on 2011-11-23
I'm running a live usb of Ubuntu 10.10 provided to me by my employer to work from home.

The problem is it doesn't recognize my graphics card so I'm stuck using 800x600 resolution (rather than 1920x1080) and I have no access to anything. The account I can login to has no privileges, so I cannot fix my graphics. Not only this but there is something like DeepFreeze installed so any changes I make however little they are, are reverted back to default after a restart. I can't even make a folder without it disappearing after a restart.

The grub menu is actually a "Unetbootin" menu, obviously what they used to create the live usb. There is only one menu option to which I edited to add "rw init=/bin/bash", I then proceeded to change the root account password, then added my account to sudoers. However upon reboot, the menu option was edited back itself, and none of my changes were done.

I converted the USB to a VDI file so I can run it through a virtual machine. Now what can I do to remove this "DeepFreeze" like "feature", so I can get my graphics card working and be able to work with a decent resolution?

I would really appreciate any help!

---

### Post by bluexrider on 2011-11-23
This is some documentation for Live Disks 

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

Good Luck

---

### Post by camaron1 on 2011-11-23
My sugestion:
 
Create your own usb ubuntu installation with Unebotin. (You can do this from windows, and it is very easy). Choose a persistent option and give is some space (say 2 gigas). In this installation any change would be persistent and you can save documents to it. You could, of course, install the proprietary graphic driver to solve your issues. 
 
Good luck

---

### Post by ubuntuforums on 2011-11-23
Thank you for the link bluexrider.

@camaron1: The problem is that I need access to the pre-installed applications on the live usb they provided. A couple of these applications are not available anywhere because they were written for my employer. So I need to use the provided live usb, unless there is a way I can backup the pre-installed applications and install them on my own Ubuntu install.

---

### Post by efflandt on 2011-11-23
Not sure if you really have a DeepFreeze of some sort, or just that everything is fixed with no "persistent data" to write anything or save settings.

Creating a bootable iso on USB with "persistent data" can allow certain settings, like timezone or adding programs that run after boot.  However, you cannot easily update or change things that happen during initial boot (like kernel or video drivers) since that is on a fixed squashfs filesystem that boots before persistent data is mounted.

This explains how to add persistent data [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

Then see [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) to see if xrandr can add and enable the resolution you want (especially the part about adding undetected resolutions).  If you can figure that out, you could put the xrandr commands in a script in the persistent filesystem.

---

