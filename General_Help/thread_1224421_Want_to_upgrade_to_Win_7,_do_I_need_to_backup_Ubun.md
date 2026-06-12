---
title: "Want to upgrade to Win 7, do I need to backup Ubuntu Partition?"
date: 2009-07-27
forum: General Help
---

### Post by PsychedelicWonders on 2009-07-27
Ok I want to upgrade to Windows 7.
 
I currently have an 80g hdd that has 50g for XP Pro currently & 20g partition for Ubuntu.
 
Now I've really customized Ubuntu for many many months and I dont want to lose all the work I've done.
 
So will the Ubuntu partition be safe?  Or should I back it up?
 
I have another 500g hdd on the same machine that is already mounted... so hopefully it will just be an easy backup then.
 
suggestions?

---

### Post by TeoBigusGeekus on 2009-07-27
You should do a backup whenever you change something in your system in case something goes wrong.
In your case, use gparted to create a new ntfs partition and install win7 there. Your only problem will be how to restore grub after the installation (windows will overwrite it).
This link will help you
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by PsychedelicWonders on 2009-07-27
> **TeoBigusGeekus said:**
> You should do a backup whenever you change something in your system in case something goes wrong.
In your case, use gparted to create a new ntfs partition and install win7 there. Your only problem will be how to restore grub after the installation (windows will overwrite it).
This link will help you
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
I dont have room to make a new partition, I have to over-write the XP Pro partition.
 
So how would I back up just the ubuntu partition onto my 500g media hdd?

---

### Post by merlinus on 2009-07-27
You can install win7 into your current xp partition, and it will not touch ubuntu.  Make very sure not to select use entire disk, or something like then, when installing.

Obviously things can go wrong, but I have never lost data this way.  But if there are some critical files, then back them up.  You can easily copy /home to your 500G hdd, for example.

---

### Post by TeoBigusGeekus on 2009-07-27
Someone correct me if I'm wrong, but I think you need only to backup your home folder.
IF something goes wrong with the windows installation, you can do a fresh install of ubuntu and add your old home folder's files in your new one.

---

### Post by PsychedelicWonders on 2009-07-27
> **TeoBigusGeekus said:**
> Someone correct me if I'm wrong, but I think you need only to backup your home folder.
IF something goes wrong with the windows installation, you can do a fresh install of ubuntu and add your old home folder's files in your new one.
 
ya just to be safe I might as well back it up...
 
Can I just drag n drop the home folder?
 
Will that transfer all of the customization I've done to Ubuntu?

---

### Post by TeoBigusGeekus on 2009-07-27
1)Yes you can drag and drop and
2)Yes, though it won't keep your installed programs. These you're gonna have to install again.

---

### Post by merlinus on 2009-07-27
Drag-and-drop should work, but make sure that you have set nautilus to show hidden files (Ctrl+H).  Your configurations, settings, bookmarks, passwords and email are in folder that begin with a dot (.)

And of course do check to ensure the copying went as planned.

---

### Post by PsychedelicWonders on 2009-07-27
> **TeoBigusGeekus said:**
> 1)Yes you can drag and drop and
2)Yes, though it won't keep your installed programs. These you're gonna have to install again.
 
I've installed countless programs... how can I backup to make sure I get everything?

---

### Post by TeoBigusGeekus on 2009-07-27
Then I hope this will help you (mind you, I've never tried it)
[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by PsychedelicWonders on 2009-07-27
> **TeoBigusGeekus said:**
> Then I hope this will help you (mind you, I've never tried it)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
 
 
```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```
 
That code just creates the .tar back up file, how exactly do I then get it to save on the 500g hdd?

---

### Post by brunog on 2009-07-27
I want to create a partition on my HDD. I have run gparted, but it does not allow me to make any changes.  Administrator password required when I launch gparted.
What am I doing wrong here?

---

### Post by merlinus on 2009-07-27
Best to create a separate thread rather than add something different to an existing one.  You will get more assistance that way.

---

### Post by TeoBigusGeekus on 2009-07-27
> **PsychedelicWonders said:**
> ```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```
 
That code just creates the .tar back up file, how exactly do I then get it to save on the 500g hdd?
Just copy and then paste it on your hd.

---

### Post by oldfred on 2009-07-27
You can also list all your installed packages and then reinstall them in a new copy of ubuntu. Copy your /home hidden files for all the configurations.

[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

You may also have to check if you have added any PPAs or other sources and add them first.

---

### Post by PsychedelicWonders on 2009-09-10
So there is no way to just copy/backup the entire Ubuntu partition as is with all of my tweaks & programs I've installed & dl'd instead of having to list them & re-download?

I guess I havent gotten the straight answer yet.

---

### Post by chinoy on 2009-09-10
Here is your straight answer after doing an install of win7 /xp / ubuntu 30 times in the last month.

a. Download the beta testers copy of Acronis True Image backup. It will allow you to create an image of your complete disk including boot and partition table. Run it under XP and back up your disk.

b. Get the Package that scans your complete Ubuntu system it finds all your customs packages and backs them up to a CD-ROM /DVD

Ubuntu 9.x is smart it will find XP / Vista / WIn7 partitions and add them to its menu system when installed.

Cant say the same for Win7.
You didnt mention if you want to run XP and WIn7 or just win7
When you install win7 if you try to install to the same partition where you have XP it will over write your XP install so do what I did which is first back up your XP Part.
Then re-create two parts one for XP and one for Win7.

My 2 cents Win7 is another bloatware version of Vista its not worth the effort.

---

### Post by PsychedelicWonders on 2009-09-11
> **chinoy said:**
> Here is your straight answer after doing an install of win7 /xp / ubuntu 30 times in the last month.

a. Download the beta testers copy of Acronis True Image backup. It will allow you to create an image of your complete disk including boot and partition table. Run it under XP and back up your disk.

b. Get the Package that scans your complete Ubuntu system it finds all your customs packages and backs them up to a CD-ROM /DVD

Ubuntu 9.x is smart it will find XP / Vista / WIn7 partitions and add them to its menu system when installed.

Cant say the same for Win7.
You didnt mention if you want to run XP and WIn7 or just win7
When you install win7 if you try to install to the same partition where you have XP it will over write your XP install so do what I did which is first back up your XP Part.
Then re-create two parts one for XP and one for Win7.

My 2 cents Win7 is another bloatware version of Vista its not worth the effort.

So where/what package do I get to add on to Acronis in order to get a full scan & backup of my Ubuntu partition?

Can I do this all in windows, or do I need to run this Acronis program in Ubuntu also?

Instead of burning it to a disc, can I just save it to a external HDD?

---

### Post by chinoy on 2009-09-12
see [http://www.acronis.com/](http://www.acronis.com/)
Its a windowze pkg.
For Linux run Synaptic pkg manager and look for the app that allows you to backup all your apps.
I have a 500 GB Maxtor External HDD 
Split your project into 2 parts
a. Backing up your XP partition
b. Backing up your Linux Part.
You can format your external HDD USB Drive under NTFS and copy your Linux backup onto it.

True Image has an option to back up your complete HDD sector by sector look into it.
You will need a seprate partition for Win7.
Or you could load WIn 7 to your external HDD it should work.
But you cant have win7 on the same part as your XP.

---

### Post by PsychedelicWonders on 2009-09-24
> **chinoy said:**
> see [http://www.acronis.com/](http://www.acronis.com/)
Its a windowze pkg.
For Linux run Synaptic pkg manager and look for the app that allows you to backup all your apps.
I have a 500 GB Maxtor External HDD 
Split your project into 2 parts
a. Backing up your XP partition
b. Backing up your Linux Part.
You can format your external HDD USB Drive under NTFS and copy your Linux backup onto it.

True Image has an option to back up your complete HDD sector by sector look into it.
You will need a seprate partition for Win7.
Or you could load WIn 7 to your external HDD it should work.
But you cant have win7 on the same part as your XP.

Ok so I need to run Acronis in Ubuntu & then also Synaptic pkg manager? (where do I find this exactly?) What does it do, create a separate file on my HDD just for all of the bells & whistles?

---

### Post by PsychedelicWonders on 2009-09-27
Does Acronis work in Ubuntu too?

---

### Post by oldfred on 2009-09-27
I see a lot of recommendations for this Remastersys

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

It allows you to make a full system copy  to a live cd or DVD.

---

### Post by ram2500 on 2009-09-28
Someone said that you only had to back up /home, but if anything went wrong, you would have to install Ubuntu again (not a big deal) BUT then, especially with users who had a lot of time put into customization, packages, drivers for Wi-Fi (a _major_ headache), so backing up the whole install is probably a good idea. After the Wi-Fi configuration alone, it makes me sick to my stomach thinking about re-doing it. And then, hunting down all the 200 or so packages that I have installed over the past year! 

I like the idea about using the external HDD though, so although you'd maybe have to reinstall Ubuntu, you can just copy over the folders containing the packages and your personal data and write over what the new install of Ubuntu installed.

---

### Post by Bigneil on 2009-09-28
just to add my tuppence here. why not install 7 onto a partition on the 500gig hdd. you can then select in bios whitch disk to boot from.. either the xp/ubuntu 80 gig disk or the windows 7 partition on the 500 gig.  it won't mess up anything and if 7 turns out to be a crock you can just delete it again without ever going near you nice stable fully cutomized xp/ubuntu disk.

---

### Post by aysiu on 2009-09-28
> **oldfred said:**
> I see a lot of recommendations for this Remastersys

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

It allows you to make a full system copy  to a live cd or DVD.
I'd second Remastersys:
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

It can be used to back up your settings and installed programs... or absolutely everything (programs, settings, and personal files).

---

### Post by PsychedelicWonders on 2009-10-21
> **aysiu said:**
> I'd second Remastersys:
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

It can be used to back up your settings and installed programs... or absolutely everything (programs, settings, and personal files).

Ok so this is the best way to completley back up Ubuntu & all of the mods & changes I've done to it over the last year?

I'll be able to save it to my external HDD right?

---

### Post by PsychedelicWonders on 2009-10-22
Alright I'm currently in the process of downloading the Win 7 Pro version.  I've already used 2nd copy to back up my main media HDD in case something goes wrong.

Now I just need to make sure I totally save my Ubuntu on the Passport exactly how I've customized it.

I checked out REmasterys and it said this:

This will not have any of your personal user data in it

I want my personal user data in this instance, and I want to save it to my Passport externdal HDD, not a dvd.

So what are my options for that?

Does Acronis work in Ubuntu?

---

### Post by PsychedelicWonders on 2009-10-23
Bump I need to find a solution for this in the next hour or two as I'm ready to upgrade to win 7.

---

### Post by PsychedelicWonders on 2009-10-24
Bump

---

