---
title: "Virtuabox Problem!"
date: 2010-09-11
forum: General Help
---

### Post by serdar132 on 2010-09-11
Hello!
I can not see my usb drives on the guest system
My host is ubuntu 10.4
Guest is XP

I guess i have done everything right! I have enabled USD usage from the settings, added the specific usb flashes and tried with and without filters.

When i use the guest OS (XP) I can see on the little usb image that it sees the usbs (in the virtualbox's screen) but XP doesnt really see it, so i cant use it.


I want to use XP to be able to prepare a bootable flash disk. I have made some research to make bootable usd on ubuntu but all I came up with how to use the usb to install ubuntu. 

Please help!

---

### Post by ronnielsen1 on 2010-09-11
> I want to use XP to be able to prepare a bootable flash disk. I have  made some research to make bootable usd on ubuntu but all I came up with  how to use the usb to install ubuntu. 
I'm not sure about using an usb in virtualbox but what are you trying to boot from the flash drive? Have you tried unetbootin?

[IMG]http://sourceforge.net/dbimage.php?id=167328[/IMG]
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by plucky on 2010-09-11
> **serdar132 said:**
> Hello!
I can not see my usb drives on the guest system
My host is ubuntu 10.4
Guest is XP

I guess i have done everything right! I have enabled USD usage from the settings, added the specific usb flashes and tried with and without filters.

When i use the guest OS (XP) I can see on the little usb image that it sees the usbs (in the virtualbox's screen) but XP doesnt really see it, so i cant use it.


I want to use XP to be able to prepare a bootable flash disk. I have made some research to make bootable usd on ubuntu but all I came up with how to use the usb to install ubuntu. 

Please help!

How did you install Virtualbox?

If you used Synaptic Package Manager,that doesn't support using USB devices,you have to download the version from the Virtualbox website for USB support.


Good Luck

---

### Post by MooPi on 2010-09-11
I have found that an ugly work around for lack of usb support is to utilize the shared folders option. I know it's not the same but works for simple file tranfers. It just involves an extra step. The only reason I mention this is the non-repository version wasn't as easy to use in my experience.

---

### Post by howefield on 2010-09-11
> **serdar132 said:**
> I can not see my usb drives on the guest system

Just to check that you have added your user to the vbox users group ?

---

### Post by Gunman1982 on 2010-09-11
> **howefield said:**
> Just to check that you have added your user to the vbox users group ?

Doesn't help if he uses the virtualbox-ose version. That one doesn't provide usb.

---

### Post by howefield on 2010-09-11
> **Gunman1982 said:**
> Doesn't help if he uses the virtualbox-ose version. That one doesn't provide usb.

I guess that'll be why plucky already mentioned that then...

---

### Post by serdar132 on 2010-09-11
I have closed source one. Which has the usb support.
But the all thing is wrong, because I have AMD Sempron, but i was using the one for i386, when i downloaded the amd version it said wrong structure, but the intel one worked fine (except the usb thing)


Well I want to prepare a bootable usb to test windows 7 for a while.

I didnt try the program u told me [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I will check it and later tell u if it worked or not

---

### Post by Capt_Scribble on 2010-09-11
Try making another group called "usb" with a group ID of 85 and add yourself to it. This will give you permission to USB devices.

---

### Post by ronnielsen1 on 2010-09-12
> Well I want to prepare a bootable usb to test windows 7 for a while.

If you have the windows iso, it will work but don't expect a live dvd of windows. It will be just like a regular Windows 7 DVD - only on USB

---

### Post by serdar132 on 2010-09-12
Yeah thats what I want anyway.

	 		**Re: Virtuabox Problem!**
 		Try making another group called "usb" with a group ID of 85 and add  yourself to it. This will give you permission to USB devices. 	

=S I ddint really understand that.

And couldnt get unetbootin to work out for me for some reason!

---

### Post by Capt_Scribble on 2010-09-12
Click on System > Administration > Users and Groups. Then click Manage Groups. Create a new group. Type "usb" for the name and type "85" for the ID number. Then check the box to add yourself to the group. If you can see the USB devices in vbox but they're grayed out, then that might help. While you're there you can double check that you're still a member of the vboxusers group too.

---

