---
title: "Need help copying linux partition to new hard drive..."
date: 2006-06-30
forum: General Help
---

### Post by JetaKing on 2006-06-30
I just got a new hard drive, and I need to copy my linux partition over somehow (while keeping dual-boot with Windows XP). I tried using Norton Ghost to just copy my entire hard drive (all the partitions), but somehow it got screwed up horribly, and starting up the computer just brought up an infinite loop of GRUB...

So, I had to totally wipe everything off (;_;) and reinstall Windows anew. Now, what should I do to recopy Ubuntu without any problems?

Thanks in advance!

---

### Post by BitTorrentBuddha on 2006-06-30
I would suggest taking a look at [this](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/), following those instructions and making changes where you see fit (if you are unfamiliar with what the commands do, post back here and I'll give you more detailed instructions), but given the fact that you are moving partitions I'll assume you know your way around, good luck and I hope it works for you ;).

---

### Post by Irony on 2006-06-30
To copy Ubuntu from one partition to another do the following. Assume here that Ubuntu is on hda3 and you are copying it onto another partition on another drive hdb2;

[php]sudo mkfs.ext3 /dev/hdb2

sudo mkdir /mnt/hda3_Ubuntu
sudo mkdir /mnt/hdb2_Ubuntu

sudo mount /dev/hda3 /mnt/hda3_Ubuntu
sudo mount /dev/hdb2 /mnt/hdb2_Ubuntu

sudo cp -ax /mnt/hda3_Ubuntu/. /mnt/hdb2_Ubuntu/.

gksudo gedit /mnt/hdb2_Ubuntu/etc/fstab
gksudo gedit /mnt/hda3_Ubuntu/boot/grub/menu.lst[/php]

Thus you first format the partition as ext 3, then make 2 directories then mount the directories, then copy hda3 to hdb2. You can do this from a live CD.

Then you edit fstab in hdb2 and replace root hda3 with hdb2.

You may need to reinstall grub - it depends whether you are adding the drive or replacing your old drive. You might also need to change the grub menu list.

Note that /. means the root partition.

---

### Post by JetaKing on 2006-06-30
Hmm... I'm not sure of those instructions will work for me.

You see, the problem is that this is on a laptop, and I can't have more than one hard drive in a laptop. I got a bigger harddrive for it, and now I want to copy everything over. 

Is there anyway that I can just install Ubuntu fresh on my new hard drive, put all my files from my old hard drive on a server, and then pull those files down onto my new one?

---

### Post by Irony on 2006-06-30
[http://www.gentoo.org/doc/en/articles/partitioning-p1.xml](http://www.gentoo.org/doc/en/articles/partitioning-p1.xml)
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

I'd imagine you would use the rsync command to copy your home partition to a server, but I haven't tried it;

[php]sudo init 1 (wait, wait... until; root@ubuntu:~#)

cd /home
rsync -aS * /path_to_server_dir

Wait until its copied then do Ctrl+D to go back to graphical mode.[/php]

What this does is put you into single user mode (text only screen) and copies the contents (*) of your home directory to another directory - you can do this from your current Ubuntu install, i.e. just boot up as normal.

---

### Post by PandorsBox on 2006-06-30
Since you cannot mount both hard drives at the same time, you'll need an external location to hold your files that you can both read and write to when booting off the Desktop CD of Ubuntu (aka LiveCD).

This is very similar to how I do backups.

You've mentioned a "Server" you have access to.  That should be fine, as long as you can read and write on that filesystem.  

USB External Hard Disks using FAT32 would work as well (and is what I use to backup my WinXP and Linux OSes)

Just make sure you have somewhere to put the files when using the Desktop CD, and then you can mount, cp/tar your way through.  Like another poster said, you'll need to rerun grub, and most likely hand edit edit /boot/grub/menu.lst (atleast that's where mine is) if your partitions on the new drive vary 'enough'.)

You can check out the fakeraidhowto Ubuntu Wiki (just google those words), for examples of how to mount/edit grub that work.  

Maybe there's better sources of information in how to do this, but everything you need is in that wiki -- you just disregard some areas that don't apply to you.

---

### Post by JetaKing on 2006-07-05
OK, thanks guys!

Now, which folders exactly would I need to copy over? My home folder, obviously... but what else? I spent *HOURS* figuring out my wireless and installing my Broadcom drivers and getting all the working... so I'd rather not have to go through that again... >.> Also, I have a few other settings (saa7134 tv card driver installed... that wasn't much fun either) that I need to keep. 

Thanks again!

---

### Post by Cynical on 2006-07-05
try sbackup, its in the repos

---

