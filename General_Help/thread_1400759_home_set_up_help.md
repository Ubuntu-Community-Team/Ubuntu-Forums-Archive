---
title: "/home set up help"
date: 2010-02-07
forum: General Help
---

### Post by gabreal2k on 2010-02-07
Hi all, I am setting up a desktop system and I have 2 (20gb) HDD's. HDD1= 5gb /
2gb swap rest /home

HDD2= 16gb ext4, 2gb puppy linux install. My question is: I want to utilize the remaining 12gb of HDD1 for music, pictures,docs and the 16gb of HDD2 for videos. 

So what is the best way to do this? I'm not opposed to using LVM but some have suggested it's easier to just make HDD2 mount to my videos folder. 

Any help on this would be greatly appreciated as I'm not exactly sure how to get ubuntu to do this if in fact this is a good way to do this.

If I can, I would like to avoid having an icon on my desktop for videos/sdb1 etc.

Thank you for taking the time to help.

---

### Post by c9-3Rr0r on 2010-02-07
So you simply want mount that partition into your home folder smth like that.

> 
/home/{yourusername}/Videos


You can do that by simply mount command.

```

sudo mount /dev/{pardition} /home/{yourusername}/Videos

```

To make it automatic mount after reboot edit /etc/fstab and add all information about with partition where shall be mounted.

I hope that helps

---

### Post by oldfred on 2010-02-07
I do what c9-3Rr0r for my NTFS partition, but for all my data I followed this link.

[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

from /home/fred - I deleted the (empty) existing folders in home.
ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Videos
etc for all folders in data 

fstab entry, 
# Entry for /dev/sda7 :
UUID=defec4d7-3e36-4938-b5de-b2016b2dee27  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  

Should be set by mount in fstab but this may have helped.
sudo chmod -R 777 /usr/local/fred/data
sudo chown -R fred:fred /usr/local/fred/data

---

### Post by gabreal2k on 2010-02-07
(I think) what I want is to open "places" on my top panel, open MUSIC (/dev/sda3/home/music/)...do WHATEVER (read,write,copy to, paste from, etc) then open VIDEOS(/dev/sdb2/home???/videos). 

To do this do I need to simply put videos on sdb2 and make my /home/videos/ folder a link to /dev/sdb2/, or do I need to create a mnt point for /dev/sdb2/videos?

 I don't mind "experimenting" for my self but I really dont wanna mess anything up as I have just reinstalled ubuntu to run with my nvidia graphics card (it was a nightmare).

---

### Post by oldfred on 2010-02-07
You have to create a mount point and add to to fstab so it mounts on every boot. I put mine where it is so I do not see it in places but only thru the links. 
I experimented with mount points and links then removed them and finalized on my version which is exactly like one of the comments in the web link in my previous post. I think it did not work right until I chowned and chmoded the mount point. I created one data partition with all my folders, if you have your data in two different partitions you will have to mount them separately and link them separately, but then both should look just like folder in /home.

After you edit fstab you can 
mount -a 
will reload fstab without rebooting.
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by gabreal2k on 2010-02-07
These options arent working for me. 

If I simply make sdb2 a mount point for /home/user/Videos then it shows up on the desktop. 

Then I need to edit gconf to get rid of that. 

This is so simple to do in windows. 

Apparently I need to setup LVM so that all remaining free space is used for /home.

I also dont have a /usr/local/myusername/

---

### Post by oldfred on 2010-02-07
If you want to create new directories your have to use mkdir.

I used the command history to list what I had done to save it to a file:

   21  sudo mkdir /usr/local/fred
   22  sudo mkdir /usr/local/fred/data
I edited fstab and then used this to remount it:
   23  sudo mount -a
   64  sudo chown fred:fred /usr/local/fred/data
   72  sudo chown fred:fred /usr/local/fred
   47  sudo chmod 766 /usr/local/fred/data
This was just a test:
   24  sudo mkdir /usr/local/fred/data/Documents
   92  ln -s /usr/local/fred/data/Music
   93  ln -s /usr/local/fred/data/Documents
   94  ln -s /usr/local/fred/data/Pictures
   95  ln -s /usr/local/fred/data/Videos
   96  ln -s /usr/local/fred/data/Downloads
   97  ln -s /usr/local/fred/data/Videos

---

### Post by gabreal2k on 2010-02-08
I may have to give that a trial run.

 I reinstalled XP then Ubuntu.

 Ubuntu took FOREVER to install and would show me stuff like: 

*setting up kerneloops, 
*enabling cryptodisks
...etc

I dont know, maybe the live CD is finally dying (I've used it a million times)?

I also dont get any image in a file transfer box, though the box is there and window border is there but no text or progress bar.

Anyway, I will have to play around a bit more to fully grasp what I'm doing/what linux can do. 

Hopefully everything will work out, maybe I should stop being so cheap and just buy a 160gb Hdd.

---

### Post by oldfred on 2010-02-08
Ubuntu usually installs pretty quick? Is hard drive ok?

I had the luxury of a new larger hard drive so I added data partitions and two partitions for Ubuntu clean installs, so I can alternate back and forth. My data and home are linked in so that is why I saved my history so I can just rerun it on the next install to semi-auto link my data in.

---

### Post by gabreal2k on 2010-02-08
I'm assuming the HDD is ok as I haven't had any problems with stuff crashing or anything but who knows. 

I may have to reinstall ubuntu (yet again). 

I lost the text/progress bar in file transfer windows too. 

Maybe I should've left XP off, but I need it for some online job sites. Either way this install has issues...lol.

---

### Post by gabreal2k on 2010-03-25
Sorry I've been gone so long, I got really busy.

 I had thought that part of the problem was with my install of ubuntu as well as trying to span multiple HDD's. So I have done a clean install on my netbook with only 1 HDD and am having the same issues. 

If I follow this: [http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508) I get a "permission denied" error.

If I follow c9-3Rr0rs' method above when I click on 'videos' it opens the Media partition and I see everything My Pictures, My Music, My Videos etc.

If I modify his method a bit: sudo "mount /dev/sda8/Media/My Pictures"  /home/g2k/Pictures

I get a "/Media/My Pictures is not a directory" error. I must be doing something VERY wrong.

---

### Post by gabreal2k on 2010-03-31
Ok I figured it out, for the solution please see this thread:

[http://ubuntuforums.org/showthread.php?t=1443373](http://ubuntuforums.org/showthread.php?t=1443373)

---

