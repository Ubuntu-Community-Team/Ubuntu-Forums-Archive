---
title: "How  to make mirror image of my hard drive on external hard drive"
date: 2012-06-10
forum: General Help
---

### Post by tc101 on 2012-06-10
I am running ubuntu 10.04 and plan to upgrade to 12.04 soon.  I would like to make a mirror image of my current system on an external hard drive just in case there is any problem.  After I install I would like to be able to boot to either drive.

Are there instructions on how to do this somewhere on line?

I am thinking about getting this external drive
[http://www.amazon.com/dp/B0041OSAZS](http://www.amazon.com/dp/B0041OSAZS)
Please tell me if that is a good choice.

---

### Post by wabbalee on 2012-06-10
Hi tc101, easypeasy if you use gparted, just copy paste action, i do that quite a bit myself. just run the system of live cd and run gparted and follow your intuition. then get the grub boot cd to boot into the clone and reinstall grub to get the bootloader on the clone. in case your clone is a usb device; stick it in any pc, boot from it and you will have your system back! once you get the hang of it it will take (depending on the size of your installation) approximately half an hour. try it, if you like, i'll guide you through as much as possible

btw, external drive looks good, go for it!

---

### Post by oldfred on 2012-06-10
Any drive or partion copy will also copy the UUID, and you cannot have the same UUID if still using both drives. You can change UUID, but then also have to reinstall grub2's boot loader and edit fstab.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by wabbalee on 2012-06-10
> **oldfred said:**
> Any drive or partion copy will also copy the UUID, and you cannot have the same UUID if still using both drives. You can change UUID, but then also have to reinstall grub2's boot loader and edit fstab.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

yes, that can lead to interesting situations if both clone and original are still in same system, had that happen yesterday, fstab was the first thing that came to mind..

---

### Post by tc101 on 2012-06-10
Thanks for the info.  I'll order the drive from Amazon and come back to ask more questions when it gets here.

---

### Post by wabbalee on 2012-06-11
no worries

---

### Post by tc101 on 2012-06-15
I got the external hard drive from Amazon, plugged it in to the computer and it works fine.  I can copy and paste files and folders just like it is part of my main hard drive.

Now I want to make a mirror image of my 10.04 system that I can boot to before I try to install 12.04.

Unfortunately the previous posts assume I knew more than I do.  I have been on this forum for a long time, but I just use Ubuntu in a very simple way.  For example in this post, I don't know what gparted, grub, bootloader or clone mean.

> Hi tc101, easypeasy if you use gparted, just copy paste action, i do that quite a bit myself. just run the system of live cd and run gparted and follow your intuition. then get the grub boot cd to boot into the clone and reinstall grub to get the bootloader on the clone. in case your clone is a usb device; stick it in any pc, boot from it and you will have your system back! once you get the hang of it it will take (depending on the size of your installation) approximately half an hour. try it, if you like, i'll guide you through as much as possible

If you are willing to guide me that is wonderful, but I don't want to take up a lot of your time, so if there are instructions on line  maybe I should read them first.

---

### Post by kanikilu on 2012-06-15
Is it a full moon or something? This at least the 3rd thread on cloning today, lol :P

Anyways, drive imaging/cloning isn't particularly hard, but also isn't necessarily trivial. You have several options:

Clonezilla Live CD (potentially more user-friendly way): [http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php)

Ubuntu Live CD + dd (the more manual way): [http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

---

### Post by wabbalee on 2012-06-15
Hi tc101,

let's start from the beginning and boot your system up with the ubuntu 12.04 cd, plug your new hard drive in and start gparted that you will find in system->gparted.

your internal hdd will come up as 'sda' in gparted, and respectively your usb drive as 'sdb'.

select your usb drive from the drop down selector somewhere near top right. assuming there is a partition on it where you already have some files stored, I need you to make the existing partition smaller by right clicking on it (unmount if mounted) and click 'resize' and create free space on the left of it big enough, at least the size of your old '/' partition on sda, bigger is probably advisable, and also keep into account that about 1gb of this new free space is going to be your new so called 'swap' partition, the equivalent of a windos 'page file'. you can do this simply by grabbing the handle on the left side and drag it to desired size.

then in the newly created space you right click and choose 'new'. drag the right handle a little to the left to leave 1gb or more for swap partition. set the file system (e.g. ext2, ext3, ext4 or some other fs) preferably the same as your old sda (10.04) root partition so it will format it to that.

make the remaining free space a swap partition in a similar manner as the previous partition, but choose to format it to 'linux-swap'

this would be a good time to click 'apply' button and let it do its thing.

now when it is done, you go back to that drop down selector and select your internal hdd called sda.

right click on the 10.04 partition, unmount (in case mounted) and choose 'copy'

go to drop down selector and choose you usb drive sdb and in newly created partition do paste. click 'apply' and sit back for a while as it will shift your gigabytes across.

I will let you play with this while I go and look for the link to download the 'superGrub2' iso.

to answer some of your other questions:
gparted = is a hard drive partitioning tool/proggie, on kubuntu it has a different 'front end' and called there 'kparted'; it is really the command line interface (cli) program called 'parted' (break down: **part**tition**ed**itor) the 'g' in gparted stands for 'gtk', a graphical front end maker, often but not always used in a 'gnome' desktop environment (ubuntu uses gnome per default).

clone = well, basically a carbon copy of an 'original', by having done the above you just made a clone.

grub = GRand Unified Bootloader, a boatloader helps you choose into what operating system (OS) you would like to boot. (we need to fix that on the clone, as it will not start at this stage yet) the grub super boot cd has this wonderful program on it and will help you boot the clone, and once booted in it I will guide you further. 

right now i am going to look up a working link for you to download this tool.

fire your questions should they arise..

---

### Post by jocefus on 2012-06-15
Assuming your external drive is as large or larger than the internal, I would just use dd from the terminal using the live cd.
 
For example, your internal drive is probably /dev/sda, and if the external is the only other drive connected, it should be /dev/sdb. So open terminal using live cd and run.
```
 
sudo dd if=/dev/sda of=/dev/sdb

```
 
That will mirror the whole drive, the master boot record, partition tables, filesystem, everything.

---

### Post by wabbalee on 2012-06-15
here is the link to the super grub boot cd:
[http://sourceforge.net/projects/supergrub.berlios/files/super_grub2_disk_hybrid_1.99b1.iso/download]("http://sourceforge.net/projects/supergrub.berlios/files/super_grub2_disk_hybrid_1.99b1.iso/download")

I just burned this iso myself, as the one I had was 'old' and right now running of my 1.5Tb external hdd with 12.04 cloned to it from a crappy old 40gb-converted-to-external-usb-disk, running perfectly.

the procedure after downloading this iso, which should only take a minute as the iso is just over a whole megabyte, is to start your preferred application for burning cd's, pop a blank cd in the drive and choose within your burn application 'burn image' just as you would when burning an Ubuntu iso, and let it do its thing. then when finished, leave the disc in the drive and reboot your system with your new usb drive plugged in that has the copy/clone of your original 10.04 system on it. make sure your system will boot of cd to enter into 'super grub' menu. choose 'detect any os' and a list of partitions from all drives that have an os on it will appear. the trick is now to choose the clone which should be on 'sdb'. select it and hit 'enter' to boot into it. no pretty splash screen during this boot.

once logged in, you should see your familiar system just how it was. 

so now to finish it off we must (re)install grub2, i use synaptic as the preferred package manager, but it should work with whatever is default package management in your 10.04 ubuntu system. so start your package manager and search for grub and also grub2. I then remove all grub and reinstall grub2 and wait for the prompt that always seems to come when you install Grub2. it asks you where to write the bootloader to. what you want to choose is your usb drive, choose 'sdb' not 'sdb1' or something (assuming still that is your usb drive, sdb).

when this has completed succesfully your usb drive should now be able to boot into your clone with the need for grub's super disk, and just about regardless what computer you plug it in, as long as the 'host' machine is set to boot off usb first.

you may run into a few prompts that I may have overlooked, I do this mostly from the top of my head you see. so if you run into something i did not cover here and you can't figure it out, don't hesitate to ask. we will see how we go with modifying '/etc/fstab', it may not be required in your case, as you where going to install 12.04 on sda now, right? this with regards to earlier in this thread by oldfred.

---

### Post by wabbalee on 2012-06-15
> **jocefus said:**
> Assuming your external drive is as large or larger than the internal, I would just use dd from the terminal using the live cd.
 
For example, your internal drive is probably /dev/sda, and if the external is the only other drive connected, it should be /dev/sdb. So open terminal using live cd and run.
```
 
sudo dd if=/dev/sda of=/dev/sdb

```
 
That will mirror the whole drive, the master boot record, partition tables, filesystem, everything.

thanks, that could be a workable solution, if you have nothing else on the target drive, right? will this command overwrite existing partition structure on the target drive? I personally place clone's into drives that have usually a lot of data on the target that I don't want to get deleted in the process.

---

### Post by NTL2009 on 2012-06-16
> **tc101 said:**
>  ... Now I want to make a mirror image of my 10.04 system that I can boot to before I try to install 12.04.

Unfortunately the previous posts assume I knew more than I do.  I have been on this forum for a long time, but I just use Ubuntu in a very simple way.  For example in this post, I don't know what gparted, grub, bootloader or clone mean. ...


> **kanikilu said:**
> Is it a full moon or something? This at least the 3rd thread on cloning today, lol :P

Anyways, drive imaging/cloning isn't particularly hard, but also isn't necessarily trivial.

First, let me commiserate with the OP. As kanikilu says, it isn't trivial. The fact that there are so many threads on the subject is a testament to how important this is, and that it is non-trivial. 

I don't want to discourage the OP, you definitely can get your system cloned, but the problem I ran into when I started down this path was, I didn't understand (and still get confused about) all the limitations of each of the methods. Some of these limitations thwarted me in what I was trying to do.

For example:

> **oldfred said:**
> Any drive or partion copy will also copy the UUID, and you cannot have the same UUID if still using both drives. You can change UUID, but then also have to reinstall grub2's boot loader and edit fstab. ...

For people who are new to this, "changing UUIDs" and "editing fstab" is a foreign language. What's an fstab? How do I edit it? What do I edit? How do I re-install a boot loader? It takes some digging to figure this out (and don't forget some file somewhere with 'resume' in the name if you expect to hibernate).
 
Here's a few things I have learned - 

1) UUIDs are the disk partition identifiers, and they are expected to be unique numbers for every partition (a long randomly generated hex number assigned when you partition a drive). Some of the cloning techniques copy the UUID to the clone. As oldfred said, if you try to boot a system with the same UUIDs on different partitions at the same time, it will get confused. 
[INDENT]
So a true clone, with duplicate UUIDs is OK if you do not need to boot with both the original drive and the clone connected at the same time.[/INDENT]


2) Many of the cloning techniques require that the destination partitions be the same size (or bigger) than your source partitions. This caused me headaches, as my source was fairly large, but only 20% used, but my destination had to be as big as the whole source drive, not just the 'used' portion. I wanted to back up two different systems, and this was going to take more disk space than I had. But I would have plenty of space if I only had to copy the 'used' space.

[INDENT]Not a problem if you have a destination drive with enough room to spare[/INDENT]


3) Some methods that people suggest create an image, but that image must be restored to be bootable. This might solve problem #2, but maybe still have problem #1.

4) Some people will suggest Remastersys, but AFAIK, this can only save to a CD/DVD, so if your install is larger than that, no-go.

5) I was also trying to clone to a drive with a clone of my other system, so dd on the whole drive and MBR would be a problem I think.


Since you describe yourself as more of a "user of Ubuntu" rather than someone who spends time "under the hood", let me throw out a few suggestions:

A) Can you remove the original hard drive after cloning? If so, this can simplify things (eliminates UUID conflicts).

B) Can you boot the clone on another system? Also eliminates UUID conflicts.

I'd also consider (KISS principal) - just purchase a new _internal_ hard drive, and do a fresh install of 12.04 on the new internal. The old drive is now your 'backup'. You really don't have to do anything (other than physically swap the drive). Once you are set on the new, you can re-purpose the old internal (they sell USB>SATA cable adapters for this ~ $20) if you want to use it for external storage.

-NTL2009

---

### Post by alphaamanitin on 2012-06-16
If you want a *TRUE, EXACT* copy of your drive, just like the concept of clonging things, you want the dd command.  DO NOT run the dd command as the previous poster mentioned, if you have a modern drive (above 20 gigabytes) that will take FOREVER.  

Again, assuming your internal drive is sda and your external drive is sdb
```
sudo dd if=/dev/sda/ of=/dev/sdb/ bs=32M conv=noerror
``` The bs says read 32 megabytes then write 32 megabytes.  If you have a bunch of ram you can go higher, if you don't have enough, it won't read that fast.  If you don't increase the bs size it will do it bit by bit.  If you want to check your progress [http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html](http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html).

If you don't want a exact clone, look up other things.  This method would be to back everything up and if you hate the new version, just reverse the if and of and you will have everything back to pre cloning.** [COLOR=Red]BTW, if means input file, of means output file.  NEVER CONFUSS THESE!!!! CONFUSE THEM AND YOU WILL NEVER RECOVER THE DATA THAT WAS OVER-WRITTEN!!!!!!![/COLOR]**

AlphaA

---

### Post by wabbalee on 2012-06-16
to NTL2009:
> 
2) Many of the cloning techniques require that the destination partitions be the same size (or bigger) than your source partitions. This caused me headaches, as my source was fairly large, but only 20% used, but my destination had to be as big as the whole source drive, not just the 'used' portion. I wanted to back up two different systems, and this was going to take more disk space than I had. But I would have plenty of space if I only had to copy the 'used' space.

interesting, i just had the same thing and as we speak I am copying a clone. the larger source and smaller target I mean, same problem; used space wise it would fit, but no go when trying to select 'paste'. solution/workaround: smallify your source to something that will definately fit, iow go smaller than target. in gparted this only takes a minute, then copy-paste to target and tada! and if you'd like to cross T's and dot i's then you can resize it back when you're done, again it will just take minute.

> For people who are new to this, "changing UUIDs" and "editing fstab" is a foreign language. What's an fstab? How do I edit it? What do I edit? How do I re-install a boot loader? It takes some digging to figure this out (and don't forget some file somewhere with 'resume' in the name if you expect to hibernate).

not sure about hibernation, i have practically no power management except when battery reaches critical it will shut down. and *that* seems to work on the  clones the same, but apart from that; one can always post one's /etc/fstab file for others to edit and copy paste it back into original. sure enough there are trust issues here but hey, we're trying to help right? besides, linux comes with absolutely no warranty.

---

### Post by tc101 on 2012-06-16
I asked a question and figured out the answer so this post is not needed. I see how to edit the post, but not how to delete it.

---

### Post by tc101 on 2012-06-16
> I'd also consider (KISS principal) - just purchase a new internal hard drive, and do a fresh install of 12.04 on the new internal. The old drive is now your 'backup'. You really don't have to do anything (other than physically swap the drive). Once you are set on the new, you can re-purpose the old internal (they sell USB>SATA cable adapters for this ~ $20) if you want to use it for external storage.

That sounds like the best idea.  I really appreciate all the time that people have taken here trying to explain this, but the truth is I feel sort of overwhelmed by the details.  A new internal hard drive that can be swapped out quickly and easily sounds like just the thing.  

When I bought the Western Digital Portable External Hard Drive that is what I had in mind, but now I understand it is not what I need.  I'll use it for backup though.

---

### Post by tc101 on 2012-06-16
Is there anything you can buy that makes swapping the internal hard drive easier?  For example some cable that would run to a hard drive case outside the main computer case?

---

### Post by NTL2009 on 2012-06-16
> **tc101 said:**
> Is there anything you can buy that makes swapping the internal hard drive easier?  For example some cable that would run to a hard drive case outside the main computer case?

You could try this:

[http://www.amazon.com/dp/B000UO6C5S/ref=pe_175190_21431760_B1_cs_sce_dp_1](http://www.amazon.com/dp/B000UO6C5S/ref=pe_175190_21431760_B1_cs_sce_dp_1)

That let me hook up internal drives (2.5" and/or 3.5") to a USB port. One caution - the drive I bought (A WD Blue Scorpion 320GB) uses 4096B sectors, where 512B is more typical. When hooked up with this cable, the Ubuntu installer did not see the drive correctly, it thought it was 1/8th the size. All other programs seem to access it OK. And the drive worked fine connected internally. I assume the drive works fine through the cable now that the installation is complete, but I have not pulled it out to try.

I had no problems installing to older drives with the typical 512B sectors with this cable.

Fortunately, the hard drive swaps out very easily on the laptop (eMachines E725), so I may try later tonight.

-NTL2009

---

### Post by tc101 on 2012-06-16
Is there some basic difference between an external drive hooked up through a usb port, and an internal drive and adapter hooked up through a usb port?

Is it possible to boot from an external drive like the one I bought?  That is what I would like to do.

This is what I have:
[http://www.amazon.com/dp/B0041OSAZS](http://www.amazon.com/dp/B0041OSAZS)

---

### Post by NTL2009 on 2012-06-16
> **tc101 said:**
> Is it possible to boot from an external drive like the one I bought?  That is what I would like to do.

This is what I have:
[http://www.amazon.com/dp/B0041OSAZS](http://www.amazon.com/dp/B0041OSAZS)

Absolutely. I've booted from a bunch of different USB external drives.

-NTL2009

---

### Post by tc101 on 2012-06-16
> Absolutely. I've booted from a bunch of different USB external drives.

Great.  So can I use the ubuntu 12.04 CD to set up 12.04 on the external drive and leave the internal drive with 10.04 untouched?  I guess I could just try it but I would hate to mess up my 10.04 system.

---

### Post by holycow131415 on 2012-06-16
You just need to make sure your bios supports booting from a usb hdd. Only difference is the rate of speed since usb is slower than sata.

---

### Post by wabbalee on 2012-06-16
> 
Is it possible to boot from an external drive like the one I bought? That is what I would like to do.

that is imho, exactly what I have explained in this post for you. follow it step by step and you will see..

oh and btw, if you take out/disconnect your 10.04 drive and just leave your external usb drive connected, there are no other locations than that usb drive for it to install itself to.

good luck!

---

### Post by NTL2009 on 2012-06-16
> **wabbalee said:**
>  ...

oh and btw, if you take out/disconnect your 10.04 drive and just leave your external usb drive connected, there are no other locations than that usb drive for it to install itself to.

good luck!

Good point - just to expand on that, when you are installing 12.04 to your external, removing the internal will help avoid a mistake and writing to your old set up. Also, you need to watch the installer - there will be a pull-down to select where to install the bootloader. You want to choose the root of the drive you are installing to. If you remove the internal, there will only be one choice (and the root will be sda - not sda1,sda2, etc). 

If you keep the internal connected, it will most likely be called sda, and your external will be called sdb (but check this). I that case, you want to choose sdb as the bootloader location. But removing the internal is safest.

-NTL2009

---

