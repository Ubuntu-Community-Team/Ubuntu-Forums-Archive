---
title: "how to create ubuntu system restore....or something"
date: 2010-08-11
forum: General Help
---

### Post by jackheart on 2010-08-11
First off, Ubuntu 10.4 is working great on my new laptop and I really enjoy it. And it is super fast.

My question is now that i have everything all set up, all my packages, my windows settings, and my ATI driver, my updates, etc., I want to be able to keep it all.

Maybe somebody could point me in the right direction or give me some better terminology. Would love to learn more about distros in the future. For now I just don't want to have to do all this updating again.

There are a few things I have found like Clonezilla and others, but they seem to be a bit advanced and more for servers. Thanks for the help, you people are great on these forums.

---

### Post by deserthowler on 2010-08-11
I use remastersys available from [http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html).  It makes a live install DVD of your system.  Read about it and see what you think.

You might also want to read this thread.  If you decide to use remastersys, it might still need this hack I reported to make it work.  [http://www.remastersys.com/forums/index.php?topic=742.0](http://www.remastersys.com/forums/index.php?topic=742.0)

I have had real good luck with it on Ubuntu and Linux Mint. I make a backup DVD before I do a kernel update, or at least make the iso and store it on another machine until I see if the update breaks the install.

Earl

---

### Post by Drenriza on 2010-08-11
I use hirens boot cd
[http://soft.softoogle.com/ap/hiren-s-bootcd-download-6916.shtml](http://soft.softoogle.com/ap/hiren-s-bootcd-download-6916.shtml)

I then use norton ghost to take a image file of my HDD. I save it to a external HDD/CD. If i ever need it i just again pop in hirens boot cd, and restore that image from norton ghost.

It's simple, easy to work with and effective.

---

### Post by john newbuntu on 2010-08-11
Clonezilla can also be used for desktop imaging.  Granted it does not have a very intuitive interface.  The reason I recommend it is that I have used this several times to clone Linux and Windows.  I have also restored them back with no problems. (except of course changing UUID/fstab etc on a different disk)

[http://www.makeuseof.com/tag/free-advanced-hard-drive-cloning-solution-from-clonezilla/](http://www.makeuseof.com/tag/free-advanced-hard-drive-cloning-solution-from-clonezilla/)

If you are a CLI guy, use the 'tar' command to compress and backup your system.  This is my preferred method. ddrescue is another option.

---

### Post by indytim on 2010-08-11
It has been my experience over the years that the most reliable backup is a full image backup of your ops and /home partition(s).  When combined with a regimented update schedule, you can pretty much be assured of recovery from "bad updates" etc.

My personal app of choice these days is fsarchiver.  It can effectively do partition level image backups on NTFS, ext3, ext4 etc.  
[http://www.fsarchiver.org/Main_Page]("http://www.fsarchiver.org/Main_Page")

I use it as an app run from System Rescue LiveCD
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

The limitation on all of this is that you need a location other that the partition(s) you are backing up to store the image files in.

Hope this helps,

IndyTim / DataMan

---

### Post by HermanAB on 2010-08-11
Howdy,

It is pointless to backup the whole system, since all the code is kept at many FTP servers around the world, for example mirrors.kernel.org.

Usually, all you need to keep is a backup of /etc:
$ sudo tar -zcvf etc.tgz /etc

---

### Post by jackheart on 2010-08-12
Thanks for all the info. I will look into it and check reply if I get it to work.

And i do realize that their are a lot of repositories of all the packages, it would just be nice to not have to DL and reinstall all that over again.

---

### Post by jackheart on 2010-08-12
> **deserthowler said:**
> I use remastersys available from [http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html).  It makes a live install DVD of your system.  Read about it and see what you think.

You might also want to read this thread.  If you decide to use remastersys, it might still need this hack I reported to make it work.  [http://www.remastersys.com/forums/index.php?topic=742.0](http://www.remastersys.com/forums/index.php?topic=742.0)

I have had real good luck with it on Ubuntu and Linux Mint. I make a backup DVD before I do a kernel update, or at least make the iso and store it on another machine until I see if the update breaks the install.

Earl

Thanks Earl for the info. I used this to make a backup, but now I am at a little bit of a loss of what to do. I chose the live CD option as a test, but I am not sure of how to burn it. It created a folder called remastersys in my home dir with 10 different thigns, includeing the .iso How do I burn all this so it will run as a live CD? Sorry if this is a silly question.

---

### Post by jackheart on 2010-08-15
Thanks again all. remastersys seemed to work. Now I just need to deal with my other issues.

---

### Post by Karl1982 on 2010-08-15
Disk imaging is the ultimate solution as far as full system backup/restore... the downsides being 1.) it's time consuming, 2.) you need a place to store it (external hard drive is a great idea), and 3.) depending on the solution you use, should you decide to restore only certain files instead of the whole thing (like your home folder), that can be easy or it can be a task depending on your software of choice.  Norton Ghost is very good about that in the Windows world because you can take an image, open the image file, and restore individual files.  I don't know if it can do that with EXT4, though.  I know it certainly can't with HFS+.

Just thought I'd throw this out there too as an alternative.  If you have an external/spare hard drive you can devote to this, you can also use a GParted LiveCD or Parted Magic LiveCD to simply copy and paste your Ubuntu partition.  In most cases, you could simply drop it back onto your drive if some unrecoverable disaster befell you, and this also gets you individual file recovery should you decide you just want your home folder back instead of the whole system.

Parted Magic's live CD also has a ghost4linux or something on it that I've never tried.  Might be worth looking into.

---

