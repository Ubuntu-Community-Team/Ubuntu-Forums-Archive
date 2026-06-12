---
title: "Prep for delete &amp; re-install: couple of Q's"
date: 2012-09-11
forum: General Help
---

### Post by Ace..... on 2012-09-11
I've lost my launcher/menus & re-install seems the best way.
I don't have a /home partition, but it seems sensible for the new setup.

The idea being:

Clean up my usb hard drive, then copy across 'home dir' for backup 

create a new partition in unallocated space and lable it '/home'
Then copy my home directory to the partition.

Then boot from ubuntu cd - do something else - delete the '/' partition - grow the '/home' partition, leaving unallocated space for '/' 

**Q.** How much space I wonder?

**Q.**Leave the swap partition as is?

Install ubuntu.

Double click on thumbnail below, displays a good quality screenshot of my drive now.

**Q.** By simply labling the new partition /home does ubuntu install recognise it and register it as '/home'?

I think I can answer this Q after reading:
[http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html)

I can lable it'/home' and copy my 'home dir' to it, but it will only be recognised as '/home' if I use 'storage device manager'.

**Q.** Does anybody know the terminal launch name of it, as I have no launcher or menu? - it's 'sudo pysdm'

**Q.** Is the 'home dir' copy, drag and drop in Nautilus or is a special command in terminal required?

**Q.** Can I just forget about Grub ie. will 'install' deal with my current multi boot setup ok?

Q. Anything else I should do?

---

### Post by Ace..... on 2012-09-11
Hmm....

I've just been reading: 

[https://sites.google.com/site/easylinuxtipsproject/partitioning](https://sites.google.com/site/easylinuxtipsproject/partitioning)

Which implies that gparted can mount the 'home partition correctly as '/home', meaning no need for pysdm.

**Q.** Is this correct?

---

### Post by VCoolio on 2012-09-11
Backup only the useful part of your home dir, like docs and pics and stuff. Maybe some config files if you've edited them.

Then reinstall, choose custom partitions or what's it called during the install process. You can create a /home partition there and leave swap as is, if it suits you. Then when you enter your username e.g. ace, the home dir /home/ace will be created. Afterwards you can copy your backupped docs and stuff there. You can't backup your current /home/ace and copy that to the new /home. I mean, you can, but it won't 'work', because there won't be a user linked to that folder. 

Space: depends on hard disk size, if it's big, set 20 Gb for / so you can install whatever you like and keep the rest for /home. If it's small, take less for /, but something like 6 Gb is a minimum I'd say. 

Multiboot: as long as you don't screw up and delete/wipe partitions while reinstalling, it's fine. Leave them alone during reinstall, you only need /, /home and /swap. If grub doesn't autodetect other os'es you can repair that later.

---

### Post by Ace..... on 2012-09-11
Great - I now understand the /home partition thing vis a vis letting install create the home dir in my labled '/home' partition.

Then I copy into the home dir.

> Then when you enter your username e.g. ace, the home dir /home/ace will be created

**Q.** The name of the folder in my home dir is mark.

I guess during install, this is the name I should enter.
Hopefully my launchpad ID will be ok.

**Q.** I'm interested to know why not back up home dir completely?

I'll be installing 12.04 again, so everything should work no?

Re size I'll give it 20Gb

Re multi boot: I will leave alone the 48Gb unallocated
I can't create a partition now cos I'm upto 4.
Windows is greedy taking 3!

I may need some advice on what to do with it (can be seen on the graphic above)

---

### Post by AndyOpie150 on 2012-09-11
> **Ace..... said:**
> Great - I now understand the /home partition thing vis a vis letting install create the home dir in my labled '/home' partition.

Then I copy into the home dir.



**Q.** The name of the folder in my home dir is mark.

I guess during install, this is the name I should enter.
Hopefully my launchpad ID will be ok.

**Q.** I'm interested to know why not back up home dir completely?

I'll be installing 12.04 again, so everything should work no?

Re size I'll give it 20Gb

Re multi boot: I will leave alone the 48Gb unallocated
I can't create a partition now cos I'm upto 4.
Windows is greedy taking 3!

I may need some advice on what to do with it (can be seen on the graphic above)Why don't you just merge the unallocated partition to your Ubuntu partiton. You will have to make sure it's the same format. I go to my Windows OS for partitioning problems as I am fairly new to Ubuntu. I use both Mini Tool Partitioning Wizard and The Easus ( I think that's how it's spelled) partitioning tool.
The Easus is the best for merging partitions of the same format that are next to each other.

If a swap is in between I would merge it first then the unallocated partition. Usually if I select to delete the partition from the drop down menu it will auto merge with the one to the left of it (if they are the same format).

Make sure everything is the same format first, if not format using the Mini Tool partitioning Wizard (it is better at this than Easus)
If everything looks good then select Apply.

---

### Post by Ace..... on 2012-09-11
> **AndyOpie150 said:**
> Why don't you just merge the unallocated partition to your Ubuntu partiton. 

Yes, this may be the way forward.
However I was taking en board the warnings of vcoolio about messing with the current partitions.

I have 500Gb so am not desperate at the mo.
I'm well prepared to proceed, and then move left the linux partitions, once reinstall is done.... that is unless there is a body of opinion that this action is fine to do now.

Thing is... now or in the future is fine, but I do appreciate your vote for sorting the partitions upfront, as that is a good logical path to take. :p

---

### Post by AndyOpie150 on 2012-09-11
I deleted and reformatted all my partitions so I could merge them all back together with my Windows OS partition (I did nothing to this one). I did this so I could use Half of the whole hard disk for the Kubuntu install (thought I would see what it was like, but no option to wipe and install over the Ubuntu partion). To make a long story short, I (not knowingly) deleted my boot.img and grub. I was stuck in grub rescue. Then oldfred posted a link to a boot repair.img that you download and burn onto a CD. It worked great.

Anyway: I would suggest making this and keeping it handy whenever you do any partitioning work. I actually deliberately deleted those same partitions again (Xubuntu didn't have the option either) knowing I would be able to fix the boot.img with ease.

Here is the link:  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Ace..... on 2012-09-11
> **VCoolio said:**
> Then when you enter your username e.g. ace, the home dir /home/ace will be created. 

Okay I've looked at this some more..... really glad you highlighted this!

My log in is Mark Surname (uppercase M & S)
My home dir is mark (lowercase m)
My Terminal root is mark@mark-pcname:~$


I think perhaps I created a login with 1st name 2nd name and perhaps the home dir used 1st name lowercase.

The pcname was probably pulled from its ex factory settings.

Anyway, forewarned is forearmed and I'll get this right at installation. :)

What else... oh yes.... gparted.

Check out the image below... it shows a whole range of partition options including /home & /temp.


In truth, should we be creating a temp partition as well as a home partition?

As a thread that may be examined by others to come... would this be the best advice?

That would mean having partitions:
ubuntu (/) the O/S
home (/home) data and config and downloaded progs i think
swap (/swap) extra memory
temp (/temp) temporary files

sorry but im in tears..... ive just lost my qwerty keyboard.
Everything is gonna be hard now.

i dont know what i did... a bizarre key combination but its flipped to my laptop config ie french azerty.

i dont even know how to access some characters its so complex.
The french have 3 characters per key... effing nightmare.

Anybody know how to load the english keyboard in terminal?

normally it sits in the top menu which i dont have.

Ill try a reboot #-o

(edit - the reboot worked & I'm back with my english keyboard - phew!)

oh yeah, heres the image:

---

### Post by Ace..... on 2012-09-11
> **AndyOpie150 said:**
> I would be able to fix the boot.img with ease.

Here is the link:  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yes i need that on disc before making my move.;)

---

### Post by VCoolio on 2012-09-11
> **Ace..... said:**
> I think perhaps I created a login with 1st name 2nd name and perhaps the home dir used 1st name lowercase.

The pcname was probably pulled from its ex factory settings.
[...]
Check out the image below... it shows a whole range of partition options including /home & /temp.

In truth, should we be creating a temp partition as well as a home partition?


You give username and pc-name during install (like [here](http://howtoubuntu.org/wp-content/uploads/2012/04/7-Who.png)). It's converted to lowercase for username and the username-pcname part in the terminal is the prompt setting. You can change that, but nevermind.

You can make partitions for whatever you like, but it's not necessary, unless (1) you like to use other file systems, e.g. reiserfs used to be good for partitions with a lot of small files (don't bother) or (2) you have an ssd disk and wish to put folders that are often written to as partitions on a regular disk, like /tmp or /var. If these are not the case, just use /, /home and /swap.

---

### Post by YannBuntu on 2012-09-11
Hello
additional information:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

### Post by Ace..... on 2012-09-12
Okay, /home and /swap it is.

I'm almost ready to go.

just gonna test my 12.04 cd

Then I'll run a command that we test ran on the rebuild thread.

---

### Post by Ace..... on 2012-09-12
> **YannBuntu said:**
> Hello
additional information:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

Very interesting, especially ubuntureinstallation.

It states that install will conserve /home data.

well I'm backed up anyway, so we can give it a whirl.

---

### Post by Ace..... on 2012-09-12
It worked perfectly.... or as near as damn it.

chrome had to be downloaded again from their site (not software centre - don't know why) but when it installed it had all my bookmarks in place..... nice.

clearly there may be other packages that need downloading, but thats fine if user data is present.

eg. just tried gparted and its not installed.

THE KEY POINT IS THIS:

Ubuntu can now be reinstalled yet it does not overwrite home dir data.

It takes about an hour, and requires the prepping (discussed above) in advance, but it is very good, and my system is FAST again as a bonus!

What I'll do is tidy the prepping info and post it here as the solution.

Thanks to all contributors! 

:D:D:D:D:D

---

