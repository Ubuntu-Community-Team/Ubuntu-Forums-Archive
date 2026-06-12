---
title: "Using USB drive at work and at home."
date: 2012-06-09
forum: General Help
---

### Post by Teddy_P on 2012-06-09
Hi Everyone.
I want to use a usb drive to run ubuntu on a couple different computers. I have it working on all the computers. I made my log in as an administrator. And it is storing all my information such as files and passwords for web sites. But I have to click "Try Ubuntu" every time I log in, and the start up would be a lot shorter with out that.
I have searched 2 days for information on useing a usb dive. All I find is how to install Ubuntu on to it. That part is working great for me. Is there any information about useing it as far as faster boot and being a defult user?


Thanks
Teddy

---

### Post by codemaniac on 2012-06-09
Unless you have created any other user , the default user is with administrative privileges in an persistent live usb .Just try adding an normal user after logging in with the default administrator login .

You can also consider an dedicated ubuntu install on your USB if it is >= 8 gb of space .

---

### Post by Teddy_P on 2012-06-09
I had an adminstratior account set up. I just made a standard user account and restarted the computer. I still get the "try ubuntu"or "Install ubuntu" page. But when I open a terminal the user name is on the comand line so I assume I am working as the standard user now.

I used the USB creator to install ubuntu on the usb hard drive. Is that what you ment?


Thanks
Teddy

---

### Post by codemaniac on 2012-06-09
You can try auto logging off .

[http://askubuntu.com/questions/106428/how-to-disable-automatic-login](http://askubuntu.com/questions/106428/how-to-disable-automatic-login)

---

### Post by rsjc852 on 2012-06-09
I think what he meant is to actually install, as in use a CD drive or other usb drive to install Ubuntu onto your flash drive.

I'm really time constricted, but you need to actually install ubuntu onto the flashdrive (making it more like a hard drive disk)

Consider using exfs2, as compared to exfs4, because journaling will kill the life of your flash drive.

just remember not to unplug it, otherwise you'll be looking at a mess of data corruption.

---

### Post by Teddy_P on 2012-06-09
I am going to try to # out this line and see what happens.
greeter-session=unity-greeter

And rsjc852, I will try that next I didn't think I could do that because I wanted to use this install on more then one computer. But I will try that next.


Teddy

---

### Post by Teddy_P on 2012-06-09
I tried to install to a usb drive and it did not work. But I haven't tried that before and might have not chosen the correct options for formating the drive correctly. I will do some research and try it again.
Thanks for helping.

Teddy

---

### Post by Ubun2to on 2012-06-09
I wouldn't bother doing an install on a flash drive without getting at least 32 GB on it so I could have a partial install and have room (or if I had >32 GB, I could do a full install and have room to spare).
I've been thinking about doing this for some time, and I am going to try it out as soon as I get a big USB drive (I like the idea of not having to lug around my laptop if there's one I can use where I'm going). I just ordered my USB drive, so I'm going to try and do this. If I can't figure out what to do, I'm not going to bother posting anything here. I'm pretty sure few people have done this before. But, this would be a great idea to include in the next release of Ubuntu (and I think there's time to build it).

---

### Post by Teddy_P on 2012-06-09
Ubun2to, I am using a 500gig usb hard drive. I thought it would be slow but it works pretty good. Maybe a flash drive would be quicker. When I did the install on the hard drive I partitioned 10gig's to exfs2 for the install and the rest to FAT.
I will keep playing with it this week end and post if I make progress.

Thanks
Teddy

---

### Post by Ubun2to on 2012-06-10
> **Teddy_P said:**
> Ubun2to, I am using a 500gig usb hard drive. I thought it would be slow but it works pretty good. Maybe a flash drive would be quicker. When I did the install on the hard drive I partitioned 10gig's to exfs2 for the install and the rest to FAT.
I will keep playing with it this week end and post if I make progress.

Thanks
Teddy

You're using an external hard drive? I thought you meant you were using a flash drive! Silly me!
I don't think flash drives go any faster than external hard drives because, although they run on flash memory, space is a huge factor in terms of how speedy they can be built (I wouldn't use a full fledged OS on a flash drive without USB 3.0).
Anyway, so, from what I understand, you used 490 GB of the drive (since you partitioned off 10 GB already) in the FAT file system-FAT is not very efficient once you are dealing with sizes over 32 GB. I recommend NTFS for sizes greater than 32 GB (or EFI/UEFI, although that's not supported very widely at the moment).
I am going to be experimenting with installing Ubuntu on a flash drive.
My current hypothesis is that you could somehow override installing on the hard drive if you installed from a DVD, so you might be able to get it onto a flash drive that way.

---

### Post by Teddy_P on 2012-06-15
Week end update.
All week I have used the 500gb USB hard drive and created 2 users. I still get asked if I want to install ubuntu at start up. But I have only restarted 3 times this week bacause I have left the hd at work. I ordered a 32 gb usb flash drive and I will install ubuntu on that.

Thanks
Teddy


Ubun2to, Have you loaded ubuntu on a flash drive yet?

---

### Post by Teddy_P on 2012-06-20
Ok. Its done and it works.
And sorry it took so long to finish this up but I had other things going on.
First I put ubuntu on a 8gig usb flash drive with the usb creator. Then I unplugged my hard drive from the computer. I only did this because its a work computer and I did not want to take a chance with loosing anything.
I bought a 32 gig usb flash drive. Plugged both in, started computer and the 8 gig asked to "try ubuntu" or "install". I installed it and it did every thing else.
After the install I restarted and unplugged the 8gig after it powered down.
I ran all the updates and am now just setting every thing up.
Performance is better then the old hard drive.

Thanks for everyones help.

Teddy_P

---

