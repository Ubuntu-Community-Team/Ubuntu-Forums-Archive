---
title: "VirtualBox: moving a &quot;hard disk&quot;?"
date: 2009-10-21
forum: General Help
---

### Post by t0p on 2009-10-21
I installed XP in VirtualBox today.  That's a couple of personal firsts: first time I installed XP, and first time I made a virtual box.  No real surprises with the XP install; but I'm impressed by VirtualBox.  It's just like a "real" XP, but I can use Ubuntu at the same time!

But I've created a problem for myself.  Because this was the first time I'd done a virtual install, I followed a tutorial and didn't really know what I was doing.  I was just going with default settings for everything.  This included letting VirtualBox create the hard disk 6GB in size at /home/t0p/.VirtualBox/HardDisks/windows-xp1.vdi.  Now, my (real) computer has a hard disk of just 20GB.  I also have a 400GB external HDD, mounted at /media/disk.  I'd like to move the virtual XP's disk to the external HDD.  But I don't know how to do it.  I know you can change some settings in Settings, but I can't see a way to move the virtual disk.  Can anyone help?

One other thing:  My (real) computer has 1GB of RAM.  How much RAM would it be good for me to give to the virtual XP?  So XP runs as well as possible without problems elsewhere.

---

### Post by Muscovy on 2009-10-21
I'm not sure what you should do about changing the vdi's location. I'll throw symbolic links out there.
  As for ram, I'd say giving XP 512 ram or a bit more. In my experience Windows is painful with less than that. Be sure that whatever number you chose can be divided by 8.

---

### Post by t0p on 2009-10-21
> **Muscovy said:**
> I'm not sure what you should do about changing the vdi's location. I'll throw symbolic links out there.
  As for ram, I'd say giving XP 512 ram or a bit more. In my experience Windows is painful with less than that. Be sure that whatever number you chose can be divided by 8.

Would making a link help?  I want to move the vdi from my internal HDD to the external one because I've got plenty of space on the external but not much on the internal.  If I create a link, but the vdi remains on the internal HDD, won't the storage constraints still exist?  Or am I misunderstanding something?

Thanks for the RAM advice.

---

### Post by howefield on 2009-10-21
You could just move it, copy/paste. Many people say it works, I prefer to use the terminal command... 

```
VBoxManage clonehd source destination
```

There is also the "Export Appliance" function you can find in the File Menu

You can delete your vm/settings from Virtualbox and recreate another using the moved virtual machine, or simply remove the existing hard disk from your existing vm and add the new location.

If it complains about the UUID change it with,

```
VBoxManage internalcommands setvdiuuid <filename>
```

---

### Post by marshmallow1304 on 2009-10-21
I believe you can just move the hard drive where you want it.  Then you'd go into Hard Disks Settings in VBox, remove the hard drive that no longer exists (because you moved it) and add the hard drive from the new location.

---

### Post by howefield on 2009-10-21
> **marshmallow1304 said:**
> I believe you can just move the hard drive where you want it.

As I say, many people do this and it seems to work, the people at Virtualbox say this though...

*"You can duplicate hard disk image files on the same host to quickly produce a second virtual machine with the same operating system setup. However, you should only make copies of virtual disk images using the utility supplied with VirtualBox; see chapter 8.16, VBoxManage clonehd, page 118. This is because VirtualBox assigns a unique identity number (UUID) to each disk image, which is also stored inside the image, and VirtualBox will refuse to work with two images that use the same number."*

---

### Post by Eberbachl on 2009-10-21
You should be able to simply move the vdi file to where you want it, then change the reference to it's location in the Virtual Media manager.

Cloning using:

*VBoxManage clonevdi [oldname] [newname]*

Should only be necessary when making a backup of your image or if you're transferring your virtual hard drive image to another virtual machine.

;)

---

### Post by t0p on 2009-10-21
Thank you everyone for your input.  I'm not at the computer with VirtualBox on it at the moment.  When I get to it, I shall try your advice.

Cheers ppl!

---

### Post by t0p on 2009-10-22
Yep, I was able to just move the vdi.  Thank you all!

---

