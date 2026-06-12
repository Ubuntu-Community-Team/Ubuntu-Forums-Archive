---
title: "EXT4 to EXT3 Conversion"
date: 2010-01-10
forum: General Help
---

### Post by motsteve on 2010-01-10
I had a smoothly running multiboot system until Karmic came along with grub2.  My backups then became ext4 filesystem because I foolishly backed up Karmic.  My smooth system then turned into a can of worms.  I've now poofed everything but my backups which still are in ext4, but  I went back to 9.04 with the intent that all future installs will be bootloader free.  Is there a way I can convert my ext4 backups back to ext3 so I can get restarted?

Don't get me wrong I love Karmic, but grub2 is not prime ready.;)
Yes, I see the potential in grub2.

---

### Post by The Cog on 2010-01-10
I don't think it's possible to downgrade from ext4 to ext3. I think the best bet is to copy all the content off the ext4 drive using a live CD, reformat it to ext3, and copy all the content back again.

It may be worth trying 9.10 on an ext3 system though. I am convinced that ext4 is responsible for causing crashes on a couple of my PCs, and that ext4 can make a right royal mess of the filesystem when this happens.

---

### Post by falconindy on 2010-01-10
Hmmm...

1) You say you backed up Karmic and now your drive is Ext4? If the drive was Ext3 before you copied files there, the only way it would become Ext4 in the process would be if you rewrote the superblocks and partition table using DD. Copying files across to a different file system doesn't change the format of that partition.
2) Regardless of the above, what's preventing you from installing grub-legacy on a 9.10 install? It's entirely possible to roll back and pin the package so it isn't upgraded.

As for the actual question, yes it IS possible to convert an ext4 formatted partition to ext2 using tune2fs to disable the features that separate the two filesystems (Ext4 is just Ext3 with some extra goodies). However, because of difference in the way that Ext4 stores data compared to Ext3 (using a feature called extents) I believe that the resulting partition, mounted as ext3, will not be able to be read.

---

### Post by motsteve on 2010-01-11
Thanks for all the help.  As it turns out, I was so hacked that I was just trying to poof anything that looked like Karmic.  In order to reestablish Windoz on my first drive which now was a SATA along with my two IDE's I forgot that my drives would be renumbered. DUH!  I ended up poofing everything including my backups.  I had a wonderful sheet on there with all kinds of Linux tips. Looks like I'll have to start over.  As mad as I get, I don't get in the way of progress, which I should, I'm 61, so I went through a 4 hour process of putting on Windoz that I never use and then put Karmic on the back of a 80G drive.  That's more than enough room for both.  I've resigned to myself to my loses and have changed my backup plan to one that includes a periodic backup to DVD.  Just changing the external firewire drive is insufficient.  I use fwbackups because it creates tar files so I can easily extract them with Linux even though I lose the app.

Thanks again for the help.  BTW, I even went along with the ext4, I try hard to not be considered a reactionary. :)


Steve

---

### Post by hhoyt on 2010-06-13
[QUOTE=motsteve;8646372]Thanks for all the help.  As it turns out, I was so hacked that I was just trying to poof anything that looked like Karmic. 

Note: Very easy to convert from ext4 to ext3 , or many other FS changes. REF: [http://www.fsarchiver.org](http://www.fsarchiver.org)

Howard

---

### Post by gawie.kellerman@gmail.com on 2010-10-13
Hi,

Yes... my IMac 24' definitely also have issues booting into an EXT4 file system (this after a successful partitioning and install).  What makes my situation even funnier is that I am completely unable to install Windows or a Linux distro after wards - it goes 'halfway' down and then freezes.

The only way to fix this is by repartitioning and reformatting with the OS X DVD upon which I then can install any operating system.  (with any EXT4 system leaving me to redo the whole process again).  Not Windows XP, 7 or Linux gets past this freezing!

I did not have these issues with EXT3 on IMAC - This however does not bode well for me for running Ubuntu on IMac - for with the older versions of Ubuntu the Broadcom Wireless driver give me many issues...  And the KDE 4 older versions of Kubuntu (apart from the wireless issues) were just too buggy for me - especially since I run a dual view system.

Anybody who can shed light or solution on this will be my hero for a day ;-)... Just note I am NOT dual booting OS X and Linux; I want the whole IMac to have Ubuntu running on it.

Gawie

---

