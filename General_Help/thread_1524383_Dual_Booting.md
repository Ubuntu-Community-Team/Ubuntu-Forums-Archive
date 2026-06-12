---
title: "Dual Booting"
date: 2010-07-05
forum: General Help
---

### Post by the_lego_box on 2010-07-05
Hey guys, I recently just attempted to install windows 7 on a friend's system that runs Ubuntu 9.1.0 (I think) in a dual boot set-up. However, now the machine cannot find an operating system at all. I am trying to find a way to restore Ubuntu, so I can re-attempt to set up dual booting. I was following [this guide]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") from lifehacker.

I have tried to set grub back up, but I get a warning that I will need to use blocklists as the HDD is partitioned. It gives me warnings that doing this is unreliable and is highly discouraged.

I'm sorry for just coming on and asking for help, but I cannot find a way to get it working again

---

### Post by Trust-No-1 on 2010-07-05
I would suggest, reformat, re-install windows 7, shrink that partition, run Ubuntu install, select "largest continuous free space" for the partitioning.
Thats how I did it with Vista, should work with 7 though

---

### Post by the_lego_box on 2010-07-05
> **Trust-No-1 said:**
> I would suggest, reformat, re-install windows 7, shrink that partition, run Ubuntu install, select "largest continuous free space" for the partitioning.
Thats how I did it with Vista, should work with 7 though

Thank for the reply, it is good advice other than the fact that I am looking to save the data off the old linux install. Some of the data won't copy over using the live cd and I don't know how to unlock the data so it can be read and copied over. I have the admin password of the Ubuntu install, but I don't know how to access the locked data and back it up

---

### Post by E=mc² on 2010-07-05
Insert the installation disk and select the option try ubuntu without installing. In this way you can access all drives and backup data.

There is another way if you want to restore your OS without reinstalling

open the drive in which linux is installed. In computer see drive properties search for an option uuid(a very long weird number).

relpace that with this highlighted number

sudo grub-setup -d /media/[COLOR="Red"]**[B]0aa8588a-e676-47e0-b3a9-ea0d761080d8**[/B][/COLOR]/boot/grub -m /media/[COLOR="Red"]0aa8588a-e676-47e0-b3a9-ea0d761080d8[/COLOR]/boot/grub/device.map /dev/sda

and paste this in terminal and press enter and it is over!!!

---

### Post by the_lego_box on 2010-07-05
Thanks for your help! I'm going to have to try and restore, there is data I cannot access to save as much as I wish I could

---

### Post by the_lego_box on 2010-07-05
How can I find the UUID? I can't find it in properties anywhere, nor are any of the terminal commands helping (admittedly they were just acquired using google). There seems to be no boot files left of the HDD

---

### Post by ajgreeny on 2010-07-05
I am sure you should be able to save the data files to a usb disk, but you may need to use root privileges to do so.

Run the Ubuntu live CD, open Computer from the desktop by double clicking on the icon, then in the file manager that opens, double click on the partition where the data files reside.  That should "mount" the partition and you can then navigate to see them and check you are in the correct partition.

As you are running the system from a CD you can not, unfortunately use a CD-R to burn the files, or not unless you have two CD drives on the machine, anyway.  You should, however be able to copy them to a usb drive without too much problem.

If you try to do that but are told you don't have the correct permissions, open the file manager with root privileges by hitting Alt+F2 and in the box that appears enter ```
gksudo nautilus
```Another file manager window will appear and you should now be able to copy across all the data files you want from the currently installed ubuntu to the usb disk.

Now you can go ahead and try to get the dual boot setup as you wish, with Windows first, then shrink the windows partition with its own disk management system, then install ubuntu.  I suggest you put grub bootmanager on the MBR of the main disk, if and when asked.  Grub is excellent as a boot system for windows, and I personally think it causes too many problems when users try to be clever and keep their original windows MBR and put grubon a partition, then realise they can figure out how to access their Ubuntu.

Also, just in case you already have a salvagable dual boot system, you could download and run the bootinfoscript from the live CD, using the directions on this site.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by the_lego_box on 2010-07-05
Wow! Thanks for that, never knew that was there (I have never used linux myself, although I am going to begin dual booting myself after I have finished with this Machine). Just moving the files over now, everything looks liked it has been saved. Thank you so much for your help ajgreeny and E=mc², I'd be lost without you

---

### Post by ajgreeny on 2010-07-05
You're very welcome.

Let me know how it all goes; and welcome to the wonder of Ubuntu and Linux.

---

