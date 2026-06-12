---
title: "Replacing ubuntu files"
date: 2010-08-22
forum: General Help
---

### Post by OpressedCalamity on 2010-08-22
Hello,
So heres the story. I was messing around and ****ed up ubuntu, and nothing functions properly now..
Is there a way I can reinstall ubuntu and keep my current configuration and files.. drivers and such.
because backups not a option..
thanks :D

---

### Post by Ginsu543 on 2010-08-22
When you installed Ubuntu the first time, did you set up a separate /home partition, or did you install Ubuntu into one partition? If you have a separate /home partition, all you have to do is reinstall the OS into the / partition without formatting the /home partition. This will keep all your config and data files (you will have to reinstall all the programs for which you have config files, of course).

If you didn't set up separate / and /home partitions, my recommendation is to use this opportunity to just start from scratch and reinstall Ubuntu with separate / and /home partitions.

---

### Post by OpressedCalamity on 2010-08-22
> **Ginsu543 said:**
> When you installed Ubuntu the first time, did you set up a separate /home partition, or did you install Ubuntu into one partition? If you have a separate /home partition, all you have to do is reinstall the OS into the / partition without formatting the /home partition. This will keep all your config and data files (you will have to reinstall all the programs for which you have config files, of course).

If you didn't set up separate / and /home partitions, my recommendation is to use this opportunity to just start from scratch and reinstall Ubuntu with separate / and /home partitions.

uhh..
Now to think of it.. don't remember, how to find out?

---

### Post by rtimai on 2010-08-23
Oppressed, what does "nothing works now" mean? You can't boot up and using another machine to post, or are logging in to the desktop, but getting error messages? If it's the second, MAYBE... you could run Synaptic Package Manager and from the menu select Edit > Repair Broken Packages. 

If your $HOME is on a different logical partition it will appear as on a separate drive in Nautilus. The installation default in system and user in one partition, I'm afraid.

---

### Post by OpressedCalamity on 2010-08-23
> **rtimai said:**
> Oppressed, what does "nothing works now" mean? You can't boot up and using another machine to post, or are logging in to the desktop, but getting error messages? If it's the second, MAYBE... you could run Synaptic Package Manager and from the menu select Edit > Repair Broken Packages. 

If your $HOME is on a different logical partition it will appear as on a separate drive in Nautilus. The installation default in system and user in one partition, I'm afraid.

Hey good idea thanks, my retardation is something you have to live with..

---

### Post by OpressedCalamity on 2010-08-23
Alright, so I tried reinstalling broken packages.
But in synaptics whenever I try to install any packages at all I get the following error, "E: yiff-server: subprocess installed post-installation script returned error exit status 1"

---

### Post by Ginsu543 on 2010-08-23
> **OpressedCalamity said:**
> 
uhh..
Now to think of it.. don't remember, how to find out?

If you haven't already, fire up Synaptic and install GParted (**G**nome **Part**ition **ed**itor). GParted will tell you exactly what drives you have installed and how each drive is partitioned. If you have / and /home on the same partition, GParted will show that you only have one partition. If you have it on separate partitions, GParted will show that you have two.

Most likely you only have one, since having a separate /home partition is not the default setting.

This is what my partition scheme looks like under GParted:

---

### Post by rtimai on 2010-08-23
Sorry. You could try re-installing Synaptic Package Manager

The package name is synptic. Enter apt-get --help if you need to review the command syntax. Good luck...

Well, your case, and Ginsu543's comments, I'm looking into learning myself how to move the home folders to a separate partition. Kind of scary procedure, however...

---

### Post by Ginsu543 on 2010-08-23
Yes, it can be somewhat daunting when you're learning to do something for the first time, but just back up your data and give it a go. It's actually not as difficult as it might at first seem, and learning to do things like this really makes running a Linux box a great fun and learning experience.

The best time to set up separate / and /home partitions is when you first install. When you run the installer, you'll get to the partition manager. It will ask you to choose how to partition your drive(s). One option is to let the installer do the partitioning for you. The last option is to do it manually.

Select manual, and it will take you to a window showing you the hard drives you have installed in your system. Simply click on the drive and delete all the partitions you have (for now). Now, you can set up each partition the way you want. Right click the drive and select "Add." Select "Primary." Change the partition size from entire drive to (let's say) 20000 (20 GB). Select the file format (ext4 is the best for most situations). Check "format." Select "/" for the drive point. That should do for the / partition.

Now, you should have the / partition and the rest should be unformatted. Right click on the unformatted portion and select "Add." Just repeat the above steps except set the drive point to "/home." and the partition size to what you want.

Continue the install.

---

### Post by sgosnell on 2010-08-24
Boot from a liveCD (or USB), and you should be able to access the drive.  Copy the /home folder to another drive, then reinstall Ubuntu, with a separate /home partition this time, and then copy the /home folder to the /home partition.  As long as you can boot from an external drive of some sort, you should be able to recover your settings, or at least most of them.  You probably want to copy /etc also, and restore that, because many configurations are there instead of in /home.

---

### Post by Ginsu543 on 2010-08-24
^^ That's a good idea, but remember to hit Ctrl+H to see all the hidden files inside your /home folder. You need to copy everything inside the /home folder.

---

### Post by rtimai on 2010-08-24
Ginsu543 and sgosnell,

Thanks for your suggestions, but I was looking to shrink my current 40GB single partition, then to create a second logical partition with the resulting unallocated space, then to move the /home folder to the second drive. There are instructions for doing that, except it doesn't say how to shrink the existing partition and to add a second partition. That's where the "scary" /home-migration shell commands come in that I mentioned. 

I tried booting from a live Ubuntu CD, but it doesn't offer a "shrink partition" option, repartitioning looks like it's going to be a destructive operation. I burned a GParted boot disk and tried booting that, but with the same result. And I don't have a lot of experience with live repartitioning either. 

I need a total hardware upgrade anyway. When I get a new system, I'll choose manual repartiton and select /home as the mount point for the second drive. (I hope I see the way to do that then.) 

FWIW, my system is an ancient 933Mhz CPU, 512 MB RAM, 40GB HD, RIVA TNT2 (only partially supported by the nouveau driver now.) Ubuntu Lucid runs faster on it than Windows XP on 486s at work. My very first system was a 20MHz 80386 with 1MB RAM, 40MB HD. Anyway, it's time to get back in step with the rest of the world.

---

### Post by castrojo on 2010-08-24
> **Ginsu543 said:**
> When you installed Ubuntu the first time, did you set up a separate /home partition, or did you install Ubuntu into one partition? If you have a separate /home partition, all you have to do is reinstall the OS into the / partition without formatting the /home partition. This will keep all your config and data files (you will have to reinstall all the programs for which you have config files, of course).

If you didn't set up separate / and /home partitions, my recommendation is to use this opportunity to just start from scratch and reinstall Ubuntu with separate / and /home partitions.

Why? He can just reinstall over his broken install and the installer will preserve his information in /home. (Unless by ****ed up he means he deleted everying in ~ too)

---

### Post by rtimai on 2010-08-24
Whiprush,

If you perform a live version update (e.g. online) your user settings and installations are preserved. But in my experience, re-installing Ubuntu from an installation CD over an existing Linux installation overwrites everything, including the /home folder if it's on the same partition. I tried a reinstall once and ended up having to re-install all my user-selected applications, and I'm glad I archived my Documents folder to CDs.

---

### Post by castrojo on 2010-08-24
The installer doesn't do this by default (and hasn't done this in a long time) unless you check the format box on the partition to format explicitly when you reinstall.

(I do have seperate / and /home, but that's because I have 2 drives, there's no real advantage to having them separated if you have only one drive, which is why it's the default behavior.)

---

### Post by rtimai on 2010-08-24
whiprush,

The Ubuntu guide page below kind of implies that reinstalling Linux will preserve the /home settings if they're on a separate physical -- as well as logical -- partition.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

However, really, it's not clear to me why that should be true. Even if the system were on a separate physical drive, I don't see how a system re-installation would detect and integrate a pre-existing /home folder on a separate drive. I probably should reconsider all this. By all means, please free to drop here any links to reports of actual experiences with having separate system and /home partitions. (I haven't found any so far.) Or direct me to an appropriate discussion. This discussion is off-topic here. (Apologies to OppressedCalamity and Ginsu543.)

---

### Post by sgosnell on 2010-08-25
The installer won't automatically detect a /home partition, you have to tell it which one to use.  If /home is on the same partition, it's just another folder, and I think it will be overwritten when the OS is reinstalled.  You can tell the installer not to format a partition, but AFAIK not a folder.  That's why having /home on a separate partition is a good idea, IMO.  

To shrink a partition, you can do it in gparted by just dragging the partition boundary to where you want it, than clicking on Apply.  You can then add a new partition in the unallocated space.  Gparted is pretty straightforward, and nothing happens until you click on the Apply button.  Just make sure you have things as you really want them before you make that click.

---

### Post by Ginsu543 on 2010-08-25
My understanding has always been that, if you have / and /home on the same partition and you reinstall the OS, the installation process will format the partition to set up the file structure for the new OS which will erase the file structure of the previous OS. Since in a single partition install /home is a sub-folder under /, /home will get erased when / is erased. However, when you designate a separate partition as /home, it is no longer physically under / although it remains logically under /. So this gives you the option of setting up a new file structure under / without having to erase /home.

---

### Post by castrojo on 2010-08-25
Nope, all you have to do is make sure that the format box is not checked. Also, it'll keep around /usr/src, /usr/local, and /var/local too, so if you have installed/built your own stuff it doesn't get removed.

It's a nice time saver!

See this answer from one of the installer developers: [http://ubuntu.stackexchange.com/questions/96/is-there-a-way-to-reset-all-packages-sources-and-start-from-scratch/179#179](http://ubuntu.stackexchange.com/questions/96/is-there-a-way-to-reset-all-packages-sources-and-start-from-scratch/179#179)

---

### Post by Miljet on 2010-08-25
Whiprush is absolutely correct. I accidently forgot to mark format before a new install once and it preserved all my /home settings.
I later tried installing a later version over an existing one without formatting and it worked the same way. Using this method, there is no reason to maintain a separate /home partition.
Try it yourself and see.

---

### Post by rtimai on 2010-08-25
All, this is developing into a great thread. OppressedC, thanks for your original request. Great installation-options information here that I haven't seen elsewhere (I'll have to perform more searches...)

So, correct me if this summary is mistaken: It is possible to preserve /home (as well as /usr/src, /usr/local, and /var/local) on the same logical partition as /, simply by unchecking the Format Partition option when installing Ubuntu OVER an existing installation. If, so that's EXCITING! -- Linux installation has caught up to Windows. In fact, that's been the only complaint I'd ever had about Ubuntu. I'm sorry I missed it in my Lucid re-install, and I'll be looking forward to taking advantage of it with my next desktop system.

---

### Post by castrojo on 2010-08-25
> So, correct me if this summary is mistaken: It is possible to preserve /home (as well as /usr/src, /usr/local, and /var/local) on the same logical partition as /, simply by unchecking the Format Partition option when installing Ubuntu OVER an existing installation.

Yep!

It's not over yet, someone needs to update [https://help.ubuntu.com/community/Partitioning/](https://help.ubuntu.com/community/Partitioning/)

Normally I'd do this myself but I am going on a trip, but this would be a great contribution from someone interested!

---

