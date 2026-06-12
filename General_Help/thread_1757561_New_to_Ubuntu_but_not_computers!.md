---
title: "New to Ubuntu but not computers!"
date: 2011-05-13
forum: General Help
---

### Post by Deaf Smith on 2011-05-13
Hi guys,
 
I work at a major hospital. MVS, CICS, COBOL, etc.... for something like 30 years.
 
I have been slowly getting into servers (besides programmer/analyst I'm a adminstrator on one of our servers and have done some ASP.NET with Visual Web Developer 2005.)
 
Now we are heading to servers for one of our major systems. Big system. $60 million bucks worth. 
 
The servers will be UNIX. They want skills such as Unix, Citrix, and catche Database. So I decided Linux would be the way to self-teach myself Unix.
 
Today I bought an old Dell, 1.3 Gh, 80 GB drive, etc... I have it loaded with an older 6.1 versioin of Ubuntu.
 
Now I need skills to run a Unix server. Besides such as Bash/Borne shell script what would you suggest to get better at this? And where would I get the software to practice on.
 
Thanks for any help.
 
Deaf

---

### Post by luckyu on 2011-05-13
Hello,
I am not sure what you are asking for but I have some suggestions that might help steer in the right direction of your endeavor of learning a Unix System. For the most part a UNIX system is extremely stable, and does exactly what you ask of it. In terms of getting better with a UNIX system try messing around with settings and install software via Synaptic Package Manager and deploying services like Samba, SSH and Apache, then learn how to configure them. There is tons of documentation offline and online to learn how todo this. Also servers don't usually have a desktop interface for efficiency and is not necessary, so learn how todo all your installing, configuring, and editing though the command line and learn how to use SSH and commands.
---
Lucky

---

### Post by dragonfly41 on 2011-05-13
>  I have it loaded with an **[COLOR=DarkRed]older 6.1 versioin[/COLOR]** of Ubuntu.Might be sensible to ditch that version and go for at least 10.10.

You will then soon be up to speed with other posters here.

---

### Post by Deaf Smith on 2011-05-13
Ok dragonfly,
 
Then if I download 10.10 from ny home PC (Windows Vista) can I just burn a CD and use it to boot from and then install?
 
Thanks,
 
Deaf

---

### Post by aphatak on 2011-05-13
You certainly can.

Although I am sure 10.10 will work very well, I would try 10.04 LTS (The LTS says this version will be supported at least until the next LTS version is released in 2013.)
If you want to install a server, make sure you download the server version, though, not the desktop version.

(And MVS - COBOL - CICS, eh?  Well, that brings back memories!  Eighteen years ago, *I* used to work on an IBM 3090 that ran MVS - CICS - COBOL - DB/2.  However, the application I was looking after was written in IBM Assembler.  Ah, the good old days, when computers were mainframes and men were men!)

---

### Post by dragonfly41 on 2011-05-13
You can download ubuntu and burn onto either a CD or USB.

This is the "LiveCD".

Since you are at the start with no data to backup there seems no reason why you can't just purge your drive and partition to install ubuntu 10.10 - or if you are brave Natty version 11 - which I have not yet installed.

You will need to do some downloading first before repartitioning.

Minimum is ubuntu LiveCD which can run from a bootable CD.

And you might need some rescue discs .. plenty advice in threads on those.

One I like is parted magic.

[http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)


But Hiren's BootCD is also recommended by others in this forum.

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

Burn these iso's onto CD's while you have a working ubuntu.

Good luck.  Plenty of advice available if you search this forum.

[EDIT]
My post crossed with aphatak.   I only have newbie experience on 10.10 and I note that it is not available now on the download options.   I started on ubuntu a couple of months ago myself.


[FURTHER EDIT]

Since you are still on Vista (as I am) you might consider installing on Windows **[COLOR=DarkRed]unetbootin[/COLOR]** which is a utility for creating bootable CD's or USB's.

You can also find unetbootin on ubuntu.

---

### Post by Deaf Smith on 2011-05-16
Ok gang... I got The Offical Ubuntu Server Book!
 
Gonna load 10.04 server today!

---

### Post by Deaf Smith on 2011-05-16
Now the question.
 
My PC I bought is a Dell™ OptiPlex™ GX270.
 
It has a 64 bit data bus but a 32 bit address bus width.
 
So can the 64 bit PC server work or do I use the 32 bit server?
 
Thanks!

---

### Post by The Cog on 2011-05-16
You can try the 64-bit version if you like. If the PC doesn't support the proper 64-bit instruction set, then the installer will tell you so and refuse to install (or even start). But the 32-bit version will work fine on 64-bit hardware, so it may be easier to just go with the 32-bit version. You won't see a difference once they're installed.

I agree with earlier posts that you really need to concentrate on the text/command-line side of things if you're trying to learn unix. You really must learn to navigate round directories, list their contents, copy/move/delete files etc. I was advised many years ago to learn just enough of the vi editor to be able to edit and save text configuration files. I don't like using vi very much, but it is universally available and knowing just a little has saved my hide a few times.

Lots of the unix basics are the same in linux so learning linux is a good start. But there are differences when you get deeper, so bear that in mind.

---

