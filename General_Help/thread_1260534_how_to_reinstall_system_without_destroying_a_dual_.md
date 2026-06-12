---
title: "how to reinstall system without destroying a dual boot."
date: 2009-09-07
forum: General Help
---

### Post by hockey97 on 2009-09-07
Hi, I want to know how I can reinstall ubuntu without destroying a dual boot. I currently have grub at a dual boot for ubuntu and windows xp. I don't want to wipe clean my windows xp partician. I just want to reinstall my ubuntu system. 

How do you do this?

---

### Post by mike555 on 2009-09-07
when you reinstall Ubuntu don't just click default, pick manual partition , just be sure to install it to where you want (the ext3 one), it will pick up the swap partition automatically ........

---

### Post by orlox on 2009-09-07
You need to go through the traditional install, but when you get to partitioning, DONT choose "use entire disc", or "install side by side" (or something like that..). Instead, choose the option to manually define partitions.

From there, you must be sure what partition corresponds to ubuntu and which corresponds to windows. Most probably, the windows partition will be NTFS, and the linux one will be extSomething (where something probably is 3, but might be 4). Also, there might be another partition that is a SWAP.

Now, you will need to choose the linux partition, choose to format it, and set it to be mounted at "/", and BE SURE that the filesystem is set to ext3 (or ext4).

Next, If you have a SWAP partition, select it, and choose it to be linux-swap (all the other options should be disabled after you do this).

And, DO NOT touch the NTFS partition.

After setting this up, proceed with the installation, and, in the end, GRUB will be setted correctly. Remember however, that this will wipe your linux partition, so you have to back up if there's anything important.

---

### Post by j_arquimbau on 2009-09-07
I selecte the swap partition myself in the manual mode. Might work that way... Just be sure of NOT CHOOSING the default option!

---

### Post by Sidewinder1 on 2009-09-07
Just curious why you want to reinstall.

---

### Post by hockey97 on 2009-09-11
ok, thanks. I reinstalled before and knew their is a way to only resintall the ubuntu partician and not the windows xp one. 

I need to reinstall the system because I was stupid. I was in the process of backing up my server system. well when my external usb hd got plugged in I got permission errors saying I don't got  write access. I then got errors saying the hard drive is cruppted. So I booted into windows and formatted the external hd as a ntfs so now the backups I had on the hard drive is gone. So I thought that I could just make new backups. So I booted back into ubuntu. I tried again and it gave me some trouble with writing permissions to the external hard drive. So I thought maybe the media folder area didn't have the proper permissions. 

So what I did which was stupid of me. I went into root. I then did a chmod and a chown and a chgrp change for the external hard drive well that is what I wanted to do instead I had a keyboard lag so it only showed /  instead of  /media/disk   disk is the name I gave to my external hard drive. Well now since those permission changes ran on / and not /media/disk. when I relaised what I did. I went here asking for help. Someone gave me some commands to try and then reboot. So I treid them and rebooted. I then found myself locked out of the system. the session-X and gnome gave me permission problems and was told that it would be easier and quicker to backup everything and reinstall. 

So I backed up everything and now going to do a reinstall. I have reinstalled before many times. It's just been a while and I can't afford to mess up my windows xp partician since I am in college and need to use microsoft office for home work assignments.

I also got to keep  my external hard drive with the ntfs format since I will need it for college to transfer documents for presentations for my classes. 

Thanks. I know remeber what to do. I just wanted to make sure so I don't mess up my windows partician. 

Also does anyone know a good way to backup a system? 

I already made a backup but when I start to work on it some more I want to make sure I can easily make a backup of the stuff.

Also is their a way I can quickly and easily transfer a partician to another computer?

I plan to buy a server in the months ahead. I am currently using a computer just to develope my website. I will transfer not just the website but also the server software like mysql and apache. 

I want to just quickly dump the partician or files on my external hard drive and just to place those files on the other computers hard drive and be able to boot into the system that is an exact copy of the first computer system. 

I don't want to spend time configurating server software and reinstalling all the software I already installed the first time. Since this takes time. I want a quick solution to transfer a os sytem copy to another computer to make all computers have the same exact software and setup installed.

I was told to try partimage. I want my server software and my website and the software installed on ubumtu to be mobile meaning If I buy new computers I can easily just transfer the files to the new computer and be able to boot up into the os and see the samve exact setup and software installed as the old computer had. So I don't need to waste time reinstalling software and cofigurating software to make them work.

I remeber getting mysql,apache,bind9,postfix to work was a hassel and same was with the graphics driver etc. 

I know hardware will be different. I want to spend less time installing stuff that I don't really need to spend that time.

---

