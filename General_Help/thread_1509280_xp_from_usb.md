---
title: "xp from usb"
date: 2010-06-14
forum: General Help
---

### Post by scoots on 2010-06-14
Hi all, i am new to ubuntu and linux in general, iv'e been using it for about a week and i like it very much. The only problem is that i have an ipod touch and i purchase music and video from the itunes store from the device. I can import music but not the items purchased as it is encrypted so i need to use itunes. I installed virtualbox so that i could use xp( only to allow me to use itunes)  but as i have a netbook with no disk drive i want to boot from a usb memory stick. Virtualbox doesn't appear to allow this so i am a bit stuck, any help would be greatly appreciated, thanks.

---

### Post by John Bean on 2010-06-14
> **scoots said:**
> Hi all, i am new to ubuntu and linux in general, iv'e been using it for about a week and i like it very much. The only problem is that i have an ipod touch and i purchase music and video from the itunes store from the device. I can import music but not the items purchased as it is encrypted so i need to use itunes. I installed virtualbox so that i could use xp( only to allow me to use itunes)  but as i have a netbook with no disk drive i want to boot from a usb memory stick. Virtualbox doesn't appear to allow this so i am a bit stuck, any help would be greatly appreciated, thanks.

VirtualBox needs either a real CD or any .iso file to use as a CD. Use another computer with a CD drive to make a .iso copy of your XP CD and mount it as a CD in VirtualBox.

---

### Post by scoots on 2010-06-14
Thanks for the quick reply, i have the iso. on the usb stick but can't seem to find it in virtualbox.
Does this mean i need to use a usb external cd drive with the .iso file on it?

---

### Post by scoots on 2010-06-14
Any ideas/

---

### Post by ronnielsen1 on 2010-06-14
If I plug a flash drive in, I can access it in virtualbox  by first creating a new virtual machine and then clicking on the settings. Once you're in the settings, go to Storage tab 
There are 2 + signs by the IDE Controller. If you hover over them, one will say Add CD/DVD Device and the other one will say Add Hard Disk. Choose Add CD/DVD Device and it should give you yhe option of adding your flash drive. If you run across problems installing from iso here's a link for installing xp
[http://bootableusb.lichy.ca/](http://bootableusb.lichy.ca/)

---

### Post by John Bean on 2010-06-14
> **scoots said:**
> Thanks for the quick reply, i have the iso. on the usb stick but can't seem to find it in virtualbox.
Does this mean i need to use a usb external cd drive with the .iso file on it?

No. Make sure your settings for the virtual XP includes a CD device then just point it at the .iso file. I'd be inclined to copy it to somewhere on the PC first to avoid any confusion; you can always delete it later.

---

### Post by scoots on 2010-06-14
Thanks John that worked a treat, i just needed it explained in laymans terms. Your a star mate.

---

### Post by John Bean on 2010-06-14
> **scoots said:**
> Thanks John that worked a treat, i just needed it explained in laymans terms. Your a star mate.

My pleasure. You might want to mark this thread as "SOLVED" (see the "thread tools" menu) if you have no other questions on this subject. Keeps things tidy :-)

---

