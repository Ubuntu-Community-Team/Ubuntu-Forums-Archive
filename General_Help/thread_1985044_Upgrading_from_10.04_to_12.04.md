---
title: "Upgrading from 10.04 to 12.04"
date: 2012-05-22
forum: General Help
---

### Post by TheUnwiseman on 2012-05-22
I'm a novice-to-intermediate Ubuntu user, and I've been on 10.04 since it came out. I've seen the Unity desktop and it looks pretty cool, and frankly, I'm tired of some of the problems my ASUS laptop has with 10.04. I'd like some help upgrading to 12.04.

I'm aware that I'll probably want to do a clean installation. I already have the .iso burned to a CD, so that's taken care of. What I'd really like help with is making the transition as seamless as possible. How do I back up everything I want to keep? How do I know where everything I want to keep is stored? I know I'll obviously want my /home and /var/www directories saved (because I'm a web developer and do test work on localhost), but what else is important?

Please let me know any information I can give you to help.

---

### Post by mikewhatever on 2012-05-22
Depends on what you want to keep. Do you have a list? In most cases, backing up the home folder would be enough.

---

### Post by TheUnwiseman on 2012-05-22
Well I'd definitely like to back up my home folder, and I definitely want to keep the stuff in /var/www. But I don't know about anything else. I don't know what folders hold what things. It would be nice if I could keep all the applications I currently have installed.

---

### Post by mikewhatever on 2012-05-23
There is no real need to know what's in every single folder. Just backup stuff that you know about, like config files you've been editing, personal files, etc. Backing up installed application wouldn't work, because most of the packages for Precise had been upgraded, and the old ones won't work.
For packages from the repositories, you can make a list of everything installed, and then use that list to reinstall the same (new) packages.
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

Everything else, like software from third party repositories or stuff compiled from source, will have to be redone.

---

### Post by forbajato on 2012-05-23
A lot of the configuration files will be in your home directory so they will follow you when you upgrade.  Another place Ubuntu stores configuration files is the /etc tree, if nothing else you may want to back that up too.

What I have done for years is set up my hard drive with at least two partitions to install the OS to as well as one for my /home directory.  I don't do web development but it seems like you may benefit from having a separate /var/www partition as well.  

So, say my current Xubuntu is installed to /dev/sda1 and I have an empty /dev/sda2 (/home being somewhere else).  Then I install the new OS to /dev/sda2, set the /dev/sda1 to mount as /media/sda1 and make sure I tell the partition manager (during install you are asked about partitions, if you choose the advanced option you can set up your own partitions) where my /home is.  That way I still have access to my old files from the old OS while able to use the new OS with my data.  I can even boot into the old OS if something goes horribly wrong (see my question regarding TLS and claws-mail!).

HTH,

thomas

---

### Post by zero2xiii on 2012-05-23
Hay,

When I upgraded directly from 10.04-32 to 12.04-64 I just did the "upgrade" option when you boot up the live CD. Since I am connected to the internet, it automaticaly installed most applications I previously had on. And most of the compatible settings have been kept. Just make sure not to format anything. Then backing up the files should not really be necessary but still adviced.

Cherz

---

### Post by tumutanzi.com on 2012-05-23
> **mikewhatever said:**
> Depends on what you want to keep. Do you have a list? In most cases, backing up the home folder would be enough.

Yep, at least backing up the whole /home folder should be a nice idea.

---

### Post by schmutztaucher on 2012-05-24
This is how I backup my system

```
cd / 
``````

tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev / 
```Take a look at this and it will explain how to back up and restore your system [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)
It doesn't take long and is a very good idea in case things go bad.

---

### Post by steve7777777 on 2012-05-24
> **forbajato said:**
> A lot of the configuration files will be in your home directory so they will follow you when you upgrade.  Another place Ubuntu stores configuration files is the /etc tree, if nothing else you may want to back that up too.

[B]What I have done for years is set up my hard drive with at least two partitions to install the OS to as well as one for my /home directory.  I don't do web development but it seems like you may benefit from having a separate /var/www partition as well.  

So, say my current Xubuntu is installed to /dev/sda1 and I have an empty /dev/sda2 (/home being somewhere else).  Then I install the new OS to /dev/sda2, set the /dev/sda1 to mount as /media/sda1 and make sure I tell the partition manager (during install you are asked about partitions, if you choose the advanced option you can set up your own partitions) where my /home is.  That way I still have access to my old files from the old OS while able to use the new OS with my data.  I can even boot into the old OS if something goes horribly wrong[/B] (see my question regarding TLS and claws-mail!).
HTH,
thomas

I have a spare partition on the primary hard drive - and that's what I'm planning on doing for the 12.04 install. But I'll have one partition for the OS and /home.  Once things are working 100%, grow the new partition shrink the "old" one.

---

### Post by steve7777777 on 2012-05-24
> **TheUnwiseman said:**
> I'm a novice-to-intermediate Ubuntu user, and I've been on 10.04 since it came out. I've seen the Unity desktop and it looks pretty cool, and frankly, I'm tired of some of the problems my ASUS laptop has with 10.04. I'd like some help upgrading to 12.04.

I'm aware that I'll probably want to do a clean installation. I already have the .iso burned to a CD, so that's taken care of. What I'd really like help with is making the transition as seamless as possible...

Also backup your entire drive to a single image using Clonezilla - just in case! Works great, I've restored for testing purposes several times.

---

### Post by mikewhatever on 2012-05-25
> **schmutztaucher said:**
> This is how I backup my system

```
cd / 
``````

tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev / 
```Take a look at this and it will explain how to back up and restore your system [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)
It doesn't take long and is a very good idea in case things go bad.

That command will archive everything, which is not what the OS wants. The time it takes to complete depends on the amount of data to archive. In certain scenarios, it would take hours, and a huge amount of disk space.

IMHO, in this particular case, archiving everything is an overkill.

---

