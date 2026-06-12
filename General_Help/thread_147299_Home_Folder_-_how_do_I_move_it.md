---
title: "Home Folder - how do I move it?"
date: 2006-03-19
forum: General Help
---

### Post by teasum on 2006-03-19
Newbie here.  I dual boot Ubuntu and XP on my Dell Inspiron 8600.  I have a question about how to move my home folder from one partition to another, and about browsing to my home folder.  

First, here's my partition table, FYI:
          Start      End      Blocks       Id  System
hda1         1     1958    15727603+   7  NTFS  (XP)
hda2    1959     3525    12586927+   5  Extended
hda3    3526    12161    69368670    b  FAT32  (docs and media files)
hda5    1959     2611     5245191    83  Linux  (Ubuntu)
hda6    2612     3329     5767303+  83  Linux  (/home)
hda7    3330     3525     1574338+  82  Linux swap

1) /XP  -  NTFS  -  15G  -  (this is my XP OS and all programs)
2) /  -  ext3  -  5G  (Ubuntu camps out here)
3) /home  -  ext3  -  5.5G  (Home folder all alone...)
4) /documents  -  Fat32  (all my documents, media files, etc., are kept here)

I want to know how I can move /home back to the Ubuntu partition.  Since I don't keep any files (besides all my hidden application settings, of course) in /home, I don't see the reason to keep it in a seperate partition.  Perhaps I'm wrong?  A secondary reason is that I can use the 5.5G partition to try out Dapper (or, god forbid, another OS... I'm just saying *maybe*....:D).  In either case I'd rather not break my installation, so I'd appreciate some guidance.  In XP I usually move special folders like "My Documents" or "Shared Documents" to seperate partitions, and I'd like to do something similar here.

Thanks!

---

### Post by cilynx on 2006-03-19
People often separate /home so that if they reinstall or upgrade or whatnot that their home settings are safe.  Also, many people keep movies / music / source code in their home and that tends to take up a lot of space.

To move your /home back onto your / partition:

Log out everything.  Drop to single user mode if possible.
Log in on a console (not graphically) as root.
Unmount /home
Mount your /dev/hda6 on /mnt
If you look at /home, you'll see that it's empty
If you look in /mnt, you'll see your home directories
'cp -r' everything from /mnt into /home
Remove the /dev/hda6 /home line from your /etc/fstab

That's about it.  Make sure you understand everything before trying to do it.  You don't want to accidently nuke your home directories.

Good Luck.

---

### Post by uopjohnson on 2006-03-19
Its easy to move your home folder.  This is linux after all.  First you really need to know your root password.  if you don't know it already you can do a 
```

sudo su
passwd

```
and enter a new password
now you should log out of ubuntu and go to a terminal cntrl-alt-1 will get you there.  now log in as root and do this:
```

init 1 

```
(takes you to single user mode ensuring that noe can access a home folder while you are messing with it.)
now put in your root password
```

cp -rp /home /home.new
vi /etc/fstab (put a # in front of the line with /home on it, you can insert by pressing i and exit by pressing esc and then :wq  thats a colon there)
umount /home
rmdir /home
sudo mv /home.New /home
init 2

```
now you shoul be able to log back in a be happy.  as long as you umounted /home when I told you too all of your data shoudl still be there.  So if you mess up you can go back easily.  rmdir should nto return an error because /home should be un mounted.  If you get an error then you probably did somethign wrong.  
If you don't # your fstab then when you reboot all bad things will happen...
Cool?

---

### Post by teasum on 2006-03-20
Success!  

Of course, now that you both point it out, it seems simple enough, but before doing something that can potentially 'nuke' my system, as you say, I like to check first.  Now I think I'll give Dapper a try on my now empty partition.

One small bug though... after I went into console mode, I noticed that the bottom of the console was cut off.  In other words, I couldn't see the line I was typing on, which kind of meant I was flying blind.  I have a widescreen laptop and video expansion disabled in my bios (because I don't like blurry displays on LCD screens... I like native resolution even if it's small).  I even double checked on bootup, and the bootsplash is cut off as well.  I guess I'll have to change my bios if I want to use the console again.

Thanks again.

---

