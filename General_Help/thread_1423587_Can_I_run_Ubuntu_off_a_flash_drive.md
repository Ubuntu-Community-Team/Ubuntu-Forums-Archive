---
title: "Can I run Ubuntu off a flash drive?"
date: 2010-03-06
forum: General Help
---

### Post by savyboy24 on 2010-03-06
Can I run Ubuntu off of a flash drive?

Lets say I have a laptop with windows and I cannot get access to my files any more or it has a bad virus. Can I run Ubuntu from a flash drive and then access my windows files from Ubuntu?

---

### Post by DawieS on 2010-03-06
Yes you can. It works the same as the Live CD, and will give you the option to try Ubuntu without installing.

You will need a flash drive which you have made boot-able, and loaded with an Ubuntu installation image (ISO) by using the **System - Administration - USB Startup Disk Creator** tab.

Insert the flash drive in a USB port, switch on and select USB in the **BIOS** Boot Sequence.

---

### Post by howefield on 2010-03-07
Just to add that it is not quite the same as the Live CD, as you can customise, install applications and save files to your flash drive, so they will still be there on your next boot.

---

### Post by savyboy24 on 2010-03-08
So can I access and read windows files from Ubuntu?

---

### Post by jocko on 2010-03-08
> **savyboy24 said:**
> So can I access and read windows files from Ubuntu?
Yes.

---

### Post by rahilm on 2010-03-08
Can we update the kernel???

---

### Post by savyboy24 on 2010-03-08
So, I can run Ubuntu from a flash drive on a Win system and I can access the files. 

1) So does this mean I can use a program to scan and remove viruses from an infected Windows system?

2) From what I understand when I have this Ubuntu flash it will be in ISO format? Does this mean that the computer i am trying to run it on needs and ISO player?

---

### Post by sikander3786 on 2010-03-08
> **savyboy24 said:**
> So, I can run Ubuntu from a flash drive on a Win system and I can access the files. 

1) So does this mean I can use a program to scan and remove viruses from an infected Windows system?

2) From what I understand when I have this Ubuntu flash it will be in ISO format? Does this mean that the computer i am trying to run it on needs and ISO player?

Yes you will be able to mount NTFS partitions and could be able to scan for viruses (I don't know how much that will help cause I have never done that).

You don't need any ISO player. Just plug in your USB and set the computer to boot from USB Drive and off you go.

Regards.

Sikander.

---

### Post by howefield on 2010-03-08
> **savyboy24 said:**
> So, I can run Ubuntu from a flash drive on a Win system and I can access the files. 

1) So does this mean I can use a program to scan and remove viruses from an infected Windows system?

2) From what I understand when I have this Ubuntu flash it will be in ISO format? Does this mean that the computer i am trying to run it on needs and ISO player?

When you boot from your flash drive, it will behave just like a "real" install on a hard disk. You will be able to update, save and run scans on a windows partition/drive. 

Your computer will need to be able to boot from the flash drive, some computers may not be able to do this, although if it is a relatively recent one, it should.

---

### Post by wojox on 2010-03-08
> **savyboy24 said:**
> 
Lets say I have a laptop with windows and I cannot get access to my files any more or it has a bad virus. Can I run Ubuntu from a flash drive and then access my windows files from Ubuntu?

You can always boot into safe mode F8 and access your files, even with a virus usually.

---

### Post by 3rdalbum on 2010-03-08
Viruses (usually?) still let you access your files, they just don't let you access the Internet or the Task Manager. But yes, I have removed viruses manually from Ubuntu. I don't know how up-to-date the ClamAV database is.

If your Windows system won't boot up, and the problem is filesystem corruption, it's probably quite unlikely that you'll be able to mount the Windows partition normally on Ubuntu. You'd need to look up how to manually mount it "read-only", and even then you might not be successful.

In short, Ubuntu is designed to be an operating system in its own right; it's not a Windows repair toolkit, although it can sometimes be used for this in some situations.

---

### Post by savyboy24 on 2010-03-08
How big of a flash is recommended?

"Windows repair toolkit" lol. Ya I was just doing some thinking about the ways in which I can use this amazing software. I was thinking that  a) if I have a friend who has a badly infected comp I could save them some money and try to remove the virus through Ubuntu flash or disk and b) if i need to do something on a public computer and do not have the program I could run from a flash or live Cd to bypass this.

---

### Post by mk1w86 on 2010-03-08
> How big of a flash is recommended?

I think the minimum size is 1GB but you will probably want more if you are going to install more applications or want to store any data. ;)

---

### Post by Herman on 2010-03-08
I prefer to have a normal Ubuntu installation in a USB stick but you need a slightly larger flash memory for that, say a 4GB minimum, or better an 8 or 16 GB flash memory.
Flash memory is getting cheaper and available in larger capacities, I recently bought some 16 GB sticks for less that $60 each.

Ubuntu is designed to replace Windows, not as a Windows utility.
Consider replacing the infected Windows operating system with Ubuntu.
Ubuntu is immune to viruses.

I have used Ubuntu to fix infected Windows computers though, sometimes they can be fixed and sometimes it's a waste of time. If the computer owner has an install CD or if the recovery partition will work it's normally faster and better to re-install.

[FONT=Arial]I used to use this and I liked it but I haven't tried it recently, [/FONT][HOWTO: Install AVG free anti-virus]("http://ubuntuforums.org/showthread.php?t=136064&highlight=virus+detection").

You can install a program called '[chntpw]("http://home.eunet.no/pnordahl/ntpasswd/")', and edit the Windows registry (if you know what you're doing), to get a disabled Windows computer working again.

You can test your hardware to make sure it's okay, [memtest86+]("http://members.iinet.net.au/%7Eherman546/p15.html#Memtest86"), [memtest86+]("http://members.iinet.net.au/%7Eherman546/p15.html#Memtest86") , [Hardware Detection and Testing]("http://members.iinet.net.au/%7Eherman546/p8.html#Hardware_Detection_and_Testing")[FONT=Arial].


[/FONT]

---

### Post by iamaynard on 2011-08-18
I would like to dig more into this topic if we can.  I have a bad virus as well and want to run a virus scanner from flash drive with Ubuntu.  I understand how to setup the USB, but are there any recommendations to a virus scanner that can run with Ubuntu on Flash.....how about Stinger from McAfee?

---

