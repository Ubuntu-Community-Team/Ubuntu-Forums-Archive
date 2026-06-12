---
title: "Is it possible to replace an Ubuntu version with a new one?"
date: 2011-01-17
forum: General Help
---

### Post by zuheyr on 2011-01-17
Hello,

Is there a way to replace my Ubuntu 9.04 with the latest version?

I have backups, so all I need is to be able to reformat all the present partitions and install the new version. I will recopy my useful files from external disk. 

*) I am using Windows Vista in dual boot.  
*) Unfortunately I do not have home on a separate partition.

Many thanks for reading, Zuheyr

---

### Post by Hippytaff on 2011-01-17
If you want to do a fresh install it's a simple as burning the iso and installing it, or you can update, but you have to do it in the right sequence, ie can't jump from 9.04 to 10.10.

---

### Post by lithopsian on 2011-01-17
You have already said one way.  Reformat your existing partition (the install will do that for you) and install the new version.  /home and everything else will be wiped.

You can also upgrade in steps by pressing the upgrade button.  You will go to 9.10, then 10.04, then 10.10.  Existing data will be preserved.  There is the possibility that you will run into glitches if you have installed non-repository software, proprietary drivers, etc, but you will always have the option to wipe it and install from scratch.  You'll need a good internet connection and some patience while all the packages download.

---

### Post by MARP1961 on 2011-01-17
You have to update your 9.04 to 9.10 first, then update that to 10.04 and if you want the very latest, you will need yet another version update to the current 10.10 Maverick Meerkat! Apparently this is all possible through the Update Manager but it takes ages and might produce problems!

By far the best way is to back up all your data files to CD (since you have no separate Home Partition, then download the latest Ubuntu iso file from the Ubuntu website. You can then burn a new install disk and boot from it and have a fresh install over the old Ubuntu partitions. Make sure you leave your Windows partition untouched (if you really want to keep Windows).

---

### Post by zuheyr on 2011-01-17
Hello,

Thanks for the replies. Will the new installation respect the Windows partitions?
This is my problem.

I cannot upgrade. In fact the reason I am doing this is because update manager proposed me to upgrade and the process failed irreversibly...

Many thanks again, Zuheyr

---

### Post by MARP1961 on 2011-01-17
When you boot with the newly burnt CD and click 'Install' it should guide you through. It should identify the partitions already on your Hard Drive. You can delete all the old Ubuntu ones then install on all the free space created. Just be really careful and make sure you do not allow Ubuntu to use the whole of the HDD. Leave any NTFS Windows partition alone! The installer should give you warnings about anything you are proposing to do. You can always proceed through the install then back out of it until you really know what is about to happen. Once you are sure, just follow the directions carefully and get clicking.

I did once delete my Windows installation by mistake! However, I don't miss it anymore. Good luck!

---

### Post by theDaveTheRave on 2011-01-17
The advice to 'start from a fresh intal' is, for me, an excellent one.

You already state that you have backups of everything, so you shouldn't loose any 'important' data.

On your backups, if you have ensured you have copied your < /home > directory (including the hidden files / folders, these begin with a . (a period) in linux) onto an external HDD you are well set.

Go through the install and when asked create separate partitions for /root /swap (if you have >5gig memory you may not really need this) and for /home then you can just copy over your backed up /home straight onto your new partition and hey presto, everything will be how you had it set up previously (well I say that, mostly you should be good, but sometimes user config files have deprecated settings and your old one is no longer recognised!)

With luck you haven't got any software you had to install from source, which means you should be able to grab everything off of the ubuntu repo's.

One extra piece of advice, install a 'minimum' system, before getting your extra software that you previously had instaled. This will mean that as you select the extra software it should pick up on any setting in your newly copied over /home directory and if anything is non-compatible with the newer version you should get warnings about the files, I say should!

So your steps could be...

Backup - particularly all of the /home (be sure to check you have the hidden files).

Clean ***minimal*** install - watch out for the windows partition.
partition as desired (check the forums for how much space to give to the different partitions.

Copy over your old /home (that you had backed up) -  copy it all into your nice shiny new /home partition that you have just created.

Use the package installer, and select the extra software that you need (previously had installed) - this should then cause Ubuntu (or whatever flavour of linux you are installing) to find your local user settings files, and prompt you if any need updating.

David

ps. This will take a while... so cakes and coffee are likely to be required in good supply - or an evening watching CSI / New York 'special victims unit' / re-runs of blackadder, Fawlty Towers, Monty Python... (or your prefered TV viewing) whilst your computer sits there humming at you.

---

### Post by zuheyr on 2011-01-17
Thank you! I really appreciate it. Zuheyr

---

### Post by zuheyr on 2011-01-17
Thank you for your excellent reply. 

Perfect advise, I dont think I backed up the hidden files.

With the minimal install, you mean whatever the installer installs. I do not know any other way of installing anyway?! I install my favorite programs, like xemacs etc, myself. 

I will let you know the result. Till I see the result, I do not call it "resolved" yet.

Many many thanks, Zuheyr

---

### Post by Vaphell on 2011-01-17
1. back up anything of value

2. run live cd of lucid or maverick or whatever and go with installation

3. in the partitioning phase of installation choose 'manual' so you get to fine-tune things. I highly recommend separate /home, it makes a clean installation a breeze (1. during reinstall set partition as /home 2. set 'format' checkbox to unmarked 3 ??? 4. profit). Stay away from any NTFS partition, wipe only extX and swap partitions.

4. in the freed space create
* let's say 10-20 GB partition for the system files (type=ext4, mount point = /)
* swap being 1-2x your RAM (type=swap)
* the rest goes to /home partition (type=ext4, mount point = /home)
5. proceed with installation and enjoy your system/user space separation plus untouched windows when it's complete

edit: too late :)

---

### Post by zuheyr on 2011-01-17
Thank you very much. I really appreciate. 
I will do a seperate /home partition this time... I should have done this before. 

Many many thanks, Zuheyr

---

### Post by zuheyr on 2011-01-17
Thank you very much. I really appreciate. 
I will do a seperate /home partition this time... I should have done this before. 

Many many thanks, Zuheyr

---

### Post by theDaveTheRave on 2011-01-17
minimal install will be just the 'core' of the system.

So only basic networking - so as you can catch the updates.

No office software, no browser, etc etc, almost a 'server' install (but without MySQL or Apache or PHP). If you really want to go 'mad' you can install without a desktop manager (ie no gnome / kde / open box blah blah blah). But that can be a bit infuriating, as then you can't get to the forums if you have a problem! - I normally only do this type of install if I have access to a second pc that I can use to google solutions to my problems.

But if you didn't catch your hidden files when you did the backup, it is a bit incidental to not install these during the process. In which case just select the extra software you want during the process.

It does make the whole thing take a little longer, but then it would probably take just as long if you where to do each item separately after the fact.

Which ever way you do it, you are on for a fun bit of learning. Give yourself a good few days to iron out all the wrinkles (they will be there waiting for you).

At least you'll be able to boot into your window partition to get your email / internet and Ubuntuforums.org fix.

have fun.

David

---

### Post by zuheyr on 2011-01-18
Hi David, many thanks. In fact I have another PC to dolve my problems, so the only worry is not to erase the Windows partitions, and time. 

Linux is like sailing and chess. There is always something new to learn and there are many new different ways to err. Thanks again, Zuheyr

---

### Post by theDaveTheRave on 2011-01-18
I like your annalogy of

'linux is like sailing and chess'

But I would say it is more like playing chess on a boat, just when you think you have everything working a big wave comes along (updates) and all the pieces move around and change how the game looks ;)

David

---

### Post by zuheyr on 2011-01-18
Very good :-) This is exactly what has happened! 
Fine, I will visit some new places. Thanks toyou and the other friends who replied. Thank you all!

Zuheyr

---

