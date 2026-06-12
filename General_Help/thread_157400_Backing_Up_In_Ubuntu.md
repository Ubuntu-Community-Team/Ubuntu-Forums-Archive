---
title: "Backing Up In Ubuntu?"
date: 2006-04-09
forum: General Help
---

### Post by flatline on 2006-04-09
Hi, me again.  Now that I've gotten everything set up and configured the way I like it (besides that pesky KVM switch), I want to make sure that it stays this way.  

Coming from a Mac and Windows background, I am used to just backing up my documents and maybe bookmarks.  However, now that I made the jump to Linux, I want to make sure that all of these extra packages that I have installed and configured get backed up too.  If I have to restore my system, I don't want to have to do all this again!

Can anyone out there go over the options I have, whether it is setting up a program to periodically do this for me or creating a big backup image now and then?

Now that I think about it, is it difficult to restore a copy of Ubuntu running the way I like it, say if my hard drive dies and I need to use a new one?

---

### Post by ksudbury on 2006-04-09
You could use rsync, bacula, ot image the drive with partimaged. 

TBH i would only backup important data the OS after all can be install again your data cant be. 

Keith

---

### Post by bscbrit on 2006-04-09
There are various options that you can adopt and I'll try to briefly give you my views on them (others will have their own opinion - this is not a black or white subject).

Under windows it is relatively easy to back up an entire system because it all resides (usually) in one partition.  That is how 'Recovery Disks' are created.  All the data at a given snapshot in time is backed up to be restored at a later date.  But there are disadvantages with this method. Firstly, you are backing up all your original binaries (e.g. .exe, .com, .dll) which you often already have on your windows CD or software installation master CD i.e. you are backing up un-necessary information.  Secondly, you may have updated your system so the original backup will now be wrong. Therefore you have to create another backup, again of duplicated data.

Linux is different (Hurrah!).  It typically uses at least 2 partitions and many people also place /etc and /home on their own partitions. The reason is that most of the configuration data is kept in the first directory, and most of your personal files in the second.  The remaining data on the other partitions (and I'm talking broad brush here) originates from the installation CD or subsequent updates, or is created by a running system and has limited value if backed up.  So if you re-install your system, or even change distros, it is easy to keep the settings and all of your data from your previous installation. :-D 

Therefore to recreate your system exactly as it is now, one method is to carrying a brand new install from CD, update it from the 'net, and then restore your /etc and /home directories.  

However, you _can_ back up each partition (in effect, reproducing what would take place under Windows but with a bit more hassle) but I do not know many people who do that.  With a 6 monthly Ubuntu update cycle, many do not want to restore to what they had but to use the latest software only configured just the way they like it.

So, my suggestion, is to back up /etc and /home and leave the rest for fresh installs.  It might take longer than using a simple Windows recovery disk but you have the latest software, all the bug fixes and security updates, and your preferred configuration.

---

### Post by Herman on 2006-04-09
My favourite method is to resize the partition to as small a size as possible with GParted livecd and copy and paste it to the last three or four GB of free space at the end of the disk. That won't help if the hard disk fails, but it could be handy if I try some wierd experiment that goes wrong and 'bork' my install.  It's fast and easy tp copy and past it back there again with GParted, completely set up and ready to go. I don't have a large amount of data, but if I did I'd back it up on CD or DVD seperately. Then if a hard disk failed I'd just re-install from scratch, I like re-installing anyway. 
I made a web-page with some info on backing up in Ubuntu, there might be something there you would be interested in: [http://www.users.bigpond.net.au/hermanzone/p13.htm]("http://www.users.bigpond.net.au/hermanzone/p13.htm")
Regards, Herman

---

### Post by flatline on 2006-04-13
Thanks for the information guys.  I understand about not needing to backup all of the data from the OS.  I guess I am still getting used to the Linux world, coming over mostly from Mac/Windoz.  

What you're saying is that most people don't backup the extra packages and applications they have installed, right?  I have downloaded various packages like Revelation, Automatix, etc.  Obviously, I am going to backup my password file from Revelation, but I probably don't need to backup Revelation itself.  Likewise, I would backup my individual MP3s, but not the software to play them.  

However, even though I am not backing up this software, I want to make sure that I can get it all back if I need to (that is, not forget a package).  Is it possible then to get a snapshot of your system configuration?  Something like a running tally of the various packages you have installed, maybe itemized/grouped by type.  Like I said, I'm pretty new, so I wouldn't want to reinstall Ubuntu and not be able to remember that great package I was using to do x before my system crashed.

---

### Post by ReelExterminator on 2006-06-04
If all you want is a list of packages that you have installed, you can type
```
dpkg -l
```
at a terminal prompt. To save that list somewhere, typing
```
dpkg -l > list_of_packages
```
will save it to a file named list_of_packages.

I also came across [this]("http://www.linuxquestions.org/questions/showthread.php?t=393191"), which explains how you would be able to restore all of your installed packages automatically. That is for the Debian distribution , and although I think it would work for Ubuntu, I'm not 100% sure. The first method in my post saves descriptions of each package, so if you're worried about not remembering the name of a really neat program, then it should be sufficient.

---

