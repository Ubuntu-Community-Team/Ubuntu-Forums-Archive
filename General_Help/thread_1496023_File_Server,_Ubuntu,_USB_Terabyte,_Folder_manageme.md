---
title: "File Server, Ubuntu, USB Terabyte, Folder management"
date: 2010-05-28
forum: General Help
---

### Post by Drake2k on 2010-05-28
So here's my question.  I setup a file server using Ubuntu Server edition following the guid by Xam @ howtoforge.com.  With only a few exceptions to minor tweaks the guide worked perfectly.  

The difference is I use a USB terabyte for data storage but that's not an issue.  It works FANTASTIC right now.  I can manage files from any computer in the house (vista xp linuxmint, ubuntu etc).  

The USB is mounted as /dev/sdb1 /media/store ntfs 0 0 in my fstab file.  It's sharing the root directory of the disk and users have access to the entire thing.  Now that it's all working, I want to know if anyone knows a way I can not let the entire disk be shared but only select folders off the root for example  /media/store/Music or /media/store/Videos.

Please keep in mind this server is command line only and I use Putty to administer it.

I was searching around using google for answers and got a lot of information I didn't feel was pertinent to my situation. I know I'm not the only one that's done this but with so much out there about everything, it's hard to filter through it.  So I'm appealing to the ubuntu forums for assistance.

---

### Post by Drake2k on 2010-05-28
Did I also mention I installed ventrilo and CUPS servers and they're working perfectly?  *giggidy* Having fun.

---

### Post by Drake2k on 2010-05-30
I understand that what I was asking may not have been very clear and with all the chatter going on with the new ubunutu versions I'm sure my post probably got lost in the shuffle.  I'm answering my own post in case anyone else wants to do something very similar.

OK, What I have:
Ubuntu Server (latest version 10.something)
1 Tera byte external USB drive.

I used this guide by Xan as the primary source for the steps taken.
[http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver")

Ok, when he gets all the way down to the mounting stuff and the fstab stuff, here is what I did differently.

First, I mounted my Tera byte drive in the fstab file.
/dev/sdb1 /media/terabyte ntfs defaults 0 0

Restarted the server since the command they gave to just restart fstab didn't work.  

The folder on my terabyte that I wanted to share was called 'Shared' so I created a symbolic link like this

cd /
ls -s /media/terabye/Shared /

This created /Shared.  When i cd into Shared it showed me all the files that were REALLY on /media/terabye/Shared

So then I changed the permissions for link using chmode 777.  Then in the step of the guide where you have to add some stuff to the end of fstab I did it like this

[Shared Folder]
comment = Random Comments
path = /Shared
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
guest = ok

then I rebooted and....

PRESTO, it worked beautifully.

I hope this helps someone.

---

