---
title: "i broke it"
date: 2012-09-12
forum: General Help
---

### Post by eldonkr on 2012-09-12
Having to post this from my phone so I'll be brief. Decided to remove Linux partition because I don't use it anymore and wanted the disk space back. Friend told me to use disk management to erase the partition and make a new one. Upon reboot
 I get this:

Error: unknown file system.
Grub rescue>


What do I do?

---

### Post by Wim Sturkenboom on 2012-09-12
May we assume you were dual booting? If so
Windows has somewhere an option for recovery of the MBR; as far as I know it requires the installation media (windows cd).

```

menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
[B][COLOR="Red"][I]        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos1)'[/I][/COLOR][/B]
        search --no-floppy --fs-uuid --set=root E05A431C5A42EEBA
**[COLOR="Red"]*        chainloader +1*[/COLOR]**
}
```
The following might work to boot Windows; enter the red lines above at the 'grub>' prompt and press <ctrl>x to boot

---

### Post by coffeecat on 2012-09-12
You are getting that error message because you still have grub installed to the mbr, and it is looking for the now-deleted partition for the grub menu. What you do depends on what you have on that machine now and how you want it configured.

Do you still have Windows and just want Windows? If so, you need to re-install the Windows mbr. This can be done with either the Microsoft installation Disc (not a manufacturer's restore disc usually) or it can also be done with an Ubuntu live CD if you don't have a Microsoft disc. I can post some links if this is what you want. Do you have either/or a Microsoft installation disc or Ubuntu live CD of the same version as the one you deleted? What version of Windows do you have?

---

### Post by eldonkr on 2012-09-12
I had win 7 ultimate 64 and ocelot 64 bit. I erased the Linux part and repartitioned the resulting unallocated space into a new volume for storage. I want to be able to power the machine on and have it boot straight into windows. How do I go about doing this?

---

### Post by coffeecat on 2012-09-12
Well - you didn't answer the rest of my questions, so...

If you have a Windows 7 installation DVD (it **must** be a Microsoft disc), **or** a Windows 7 repair CD (you can create a repair CD from any Windows 7 system, which must be 64-bit to match yours), run bootrec /fixmbr as described here:

[http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html](http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html)

If you don't have either, use an Ubuntu live CD with one of the three methods in code tags here:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

They all install code to the mbr functionally equivalent to the Windows mbr. My choice would be the third/last, but be careful with that one. One typo with dd and you can do a lot of damage. The advantage is that you don't have to be connected to the internet, so "sudo apt-get install syslinux" is unnecessary. The file /usr/lib/syslinux/mbr.bin is already in the live system.

---

### Post by jerome1232 on 2012-09-12
> **coffeecat said:**
> 

They all install code to the mbr functionally equivalent to the Windows mbr. My choice would be the third/last, but be careful with that one. One typo with dd and you can do a lot of damage. 

Partition tables are over rated anyways. :D

> **coffeecat said:**
> 
The advantage is that you don't have to be connected to the internet, so "sudo apt-get install syslinux" is unnecessary. The file /usr/lib/syslinux/mbr.bin is already in the live system.
 
That last method, it installs a bootloader similar to the Windows one? Does it just "work" with no configuration?

I ask because this would be a very handy thing to know for all of those people have broken their mbr but have no Windows recovery disks.

---

### Post by coffeecat on 2012-09-12
> **jerome1232 said:**
> Partition tables are over rated anyways. :D


:)
 
> **jerome1232 said:**
> That last method, it installs a bootloader similar to the Windows one? Does it just "work" with no configuration?

I ask because this would be a very handy thing to know for all of those people have broken their mbr but have no Windows recovery disks.

Agreed. It should be more widely known, although by utilising dd it does need to come with a health warning! Which is perhaps why many people on this forum recommend the lilo method, which works just fine too. Short answer - if you have an Ubuntu live CD you can repair the Windows mbr.

I don't know when /usr/lib/syslinux/mbr.bin was included in default systems, but it's been in recent versions, and in the live session, at least the ones I've checked. In my Precise installation, properties tells me it's exactly 440 bytes long. It's simply the 440 bytes of code that needs to go into the first 440 bytes of the hard drive. If it's not a byte-for-byte copy of the code bootrec /fixmbr installs, then it's certainly functionally identical. It's worked for me.

Does it just "work"? Yes, but you need to check that the Windows C: partition or boot ("system") partition in Windows if you have one has the boot flag set.

@eldonkr, that last is one thing I forgot to mention. If you install the mbr code and Windows still doesn't boot, that's one thing we can check and fix.

---

### Post by eldonkr on 2012-09-12
I was dual booting 7 ultimate and ocelot. Both 64. All of my windows and Linux stuff was in ISO format on a 2tb external that failed a month ago. My computer.    only has USB ports. The only friend who can help me is too busy to and I have no other computers with internet or DVD support. Can someone upload something on here for me to put on a flash drive with instructions on how to fix this please?

---

### Post by AndyOpie150 on 2012-09-12
I was stuck in grub rescue just a week ago. oldfred saved the day. Go here: [http://ubuntuforums.org/showpost.php?p=12217150&postcount=2](http://ubuntuforums.org/showpost.php?p=12217150&postcount=2)
Go to the boot repair link.

EDIT: In order for this to work you will have to use a utility program that will install the iso and make the USB drive bootable. I used a cd for this, but I just re-read your last post and realized you have no cd drive. Must have been sleeping when I first read it, sorry. I'll help and try to find a utility program that will work for this purpose.

Note: grub commands didn't work while I was stuck in grub rescue

---

### Post by coffeecat on 2012-09-13
> **eldonkr said:**
> My computer.    only has USB ports.

I've already posted a link for three different methods for installing the Windows mbr from a live Ubuntu session. It will work equally well from an Ubuntu live USB as from an Ubuntu live CD. Do you have an Ubuntu ISO? Do you have a system where you can write that ISO to a USB stick to create a live Ubuntu ISO?

I could upload a 440 bytes file for you to write to the mbr of your machine, but you would need a Linux system so to do. Which means that you would need to run Linux/Ubuntu from the machine you are trying to repair, which means running a live USB or CD. So we go round in circles.

You are clearly not posting from the machine that needs repairing because you can't boot it. What operating system are you posting from?

---

### Post by AndyOpie150 on 2012-09-13
I also found this: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) if you need another option.

Wasn't trying to step on your toes coffeecat, just know from experience the stress involved in seeing "grub rescue", thought I could help.

---

### Post by eldonkr on 2012-09-13
I have been posting from my phone this whole time.

---

### Post by coffeecat on 2012-09-14
> **eldonkr said:**
> I have been posting from my phone this whole time.

Apologies for missing that in your first post.

Let me summarise your problem as I see it. You need to rewrite the Windows mbr (or equivalent) to the first 440 bytes of the hard drive. You may also need to reset the boot flag on the Windows boot partition, although this is unlikely.

Without a way of booting a Windows 7 Installation DVD, Windows 7 rescue CD or Ubuntu live CD I don't know of any way of doing this, except for removing the hard drive from your computer and attaching it to another machine. Since you don't have an internal optical drive, you need to create and boot either a USB flash drive or use an external USB optical drive. Without another computer to create the bootable USB or CD, I don't see any way around this. If someone else does, I'd be interested to hear.

---

### Post by Scott Harrison on 2012-09-14
Any update on this, OP?

---

### Post by eldonkr on 2012-09-14
Pulled the hard development out to back up the files on a friends computer. The next step is to format the drive and put it back in the computer to reinstall windows but my friend can't find the 7 disc.

---

