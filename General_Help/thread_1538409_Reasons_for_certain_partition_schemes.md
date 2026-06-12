---
title: "Reasons for certain partition schemes"
date: 2010-07-25
forum: General Help
---

### Post by poltak on 2010-07-25
Hello there!
Just got another quick question. Well I've always installed Ubuntu (and other linux distros, for that matter) on a single logical partition, mounting it as / and using a separate partition for my swap. I gather this is a pretty basic partition scheme.
Anyway, I was wondering why use separate partitions for different folders (such as /home, /boot etc)? What are the advantages and are there any disadvantages?
The only advantage I can think of is if your system shits itself and you are forced to reinstall linux, all your personal stuff in the /home directory is still there since it's separate from the root directory. Am I right?

Also, just to add to my original question, using a partition scheme with several different partitions for different directories, does this slow your system down at all (from data being transfered across disk partitions)?

Thanks for your time :)

---

### Post by robsoles on 2010-07-25
Due to the way I organise both servers and desktops I have a tendency of setting up using 30Gb for /, 5Gb for /root and the remainder for /home. I give /root 5Gb so that I can keep .conf and other 'gem' files in his folder and they will be retained if I scrub the OS with a replacement.

I don't bother with /boot nor other folders to their own partitions because when I replace the OS, whether with same version of same distro or something completely different (but still Linux), the other folders will all need re-writing anyway.

A minor disadvantage is that .hidden directories in ~/ (user's homes) are retained and it is possible to go from such a distro to such another distro that this can be somewhat tiring if you forget to delete the ones you can afford to delete - if you want to keep your VirtualBox VMs then you can't afford to delete ~/.virtualbox for example.

I can't state a performance difference - I have many (a number I've lost track) installs (in three distros of Linux) behind me on more than a dozen machines and when I rush it a little and let the installer make a single partition or (worse IMHO) LVM of it that PC is no faster nor slower seeming than others, just more effort to replace OS and preserve personal files.

---

### Post by HermanAB on 2010-07-25
It is easier to re-install when all user data is in one partition or make backups of a whole partition.  There is no performance difference, unless the partitions are separate hard disks or network attached storage.

---

### Post by Blackbird_13 on 2010-07-25
You can get around the problem with ~/.hidden files in /home by having a separate Data partition with Documents/Pictures/Videos/Music etc. You can then create sym links in your /home/user/ directory to your Data directory. This has two advantages:

On a re-install your data files are safe.
You can use the same Data partition for more than  one operating system i.e. dual/triple boot.

I didn't notice any change in performance when I set up a separate Data partition.

---

### Post by poltak on 2010-07-25
Ah, right I'm starting to understand now. So there won't be a change in performance if the partitions are on the disk.

But just an additional question on what Blackbird_13 said:
Does that mean I can share, for example, my /home directory between various linux distros?
Let's say I wanted to have both OpenSuSE and Ubuntu installed in the extended partition on my hard disk. Of course, both of them can share the swap partition, but can they also share the /home, /usr etc directories/partitions?
Maybe I'm misunderstanding your post... but it sounds cool if it's possible :p

---

### Post by robsoles on 2010-07-25
/home directory can be shared by different distros provided one rule is followed: User number in Linux is the same for each user in each installation - something about differences between them may trash something in /home dirs anyway but probably nothing too serious (and I haven't tried it so I can be proven wrong for sure...)

/usr directory cannot be shared as far as I can see - unless the binaries for each distro are the same and I'm thinking they wouldn't be different distros if the binaries were the same ;)

---

### Post by poltak on 2010-07-25
Ah, I see. So it'll probably be less trouble for me to just have separate /home partitions/directories with different linux distros.

So are there any other advantages to having a specific partition scheme other than having your personal files separate from your system files?
I keep all my personal files separate anyway on an NTFS partition (which I mount to /media/stuff) which I currently share between Windows and another linux distro. So considering this, is it actually worth the trouble or should I stick with just logical partitions for / and swap for linux?

Thanks for helping a newbie out :P I should know more, I've been using linux systems for over a year now, but yeah... still a newbie at a lot of stuff with linux. I hope I'm not confusing anyone as well...

---

### Post by robsoles on 2010-07-25
Separation of /home and the rest of the file-system is really just a convenience if you or your user(s) keep a lot of stuff on their local HDD in their own 'profile' but it isn't worth it if you/they keep very little in their local private space that the OS in particular prescribes to them.

If I could convince people on my work's network to keep everything on the server I wouldn't bother making their desktops use similar structure as I use on the file-server. It's hard to preach it at them because for all the space on the file-server I run at home I end up with a lot of personal crap on my local HDD, that I mean to keep on the server, anyway.

Considering your behavior, if you will stick to keeping stuff you like and want to have in the long term on a seperate partition anyway, then it is not worth it to you - if you were going to run a file-server using a Linux base and allow multiple users and use the 'home' directory method usually employed then it is definitely worth it in that situation!

---

### Post by bodhi.zazen on 2010-07-25
> **poltak said:**
> Hello there!
Just got another quick question. Well I've always installed Ubuntu (and other linux distros, for that matter) on a single logical partition, mounting it as / and using a separate partition for my swap. I gather this is a pretty basic partition scheme.
Anyway, I was wondering why use separate partitions for different folders (such as /home, /boot etc)? What are the advantages and are there any disadvantages?
The only advantage I can think of is if your system shits itself and you are forced to reinstall linux, all your personal stuff in the /home directory is still there since it's separate from the root directory. Am I right?

Also, just to add to my original question, using a partition scheme with several different partitions for different directories, does this slow your system down at all (from data being transfered across disk partitions)?

Thanks for your time :)

There are various reasons for various partitioning schemes.

You need a /boot if grub can not mount the root partition directly. The two most common examples ar LVM and encryption.

The second reason is security : 

[http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html)

You can also specify options ofr various partitions , such as /home /tmp , with security options, such as noexec, nodev , etc or quotas or acl.

Thirs is for data. IMO it is extremely helpful to keep a data partition. This can be /home or another /data partition. You can keep data in one location for backup and re-install the os without data loss.

I only back up a few . files, .bashrc or .zshrc for example. The majority of . files are, IMO, of little to benefit.

In the second post, /root is serving as a separate home partition for root.

---

### Post by poltak on 2010-07-26
Alright, well after reading all of your posts, I've decided to stick with my standard linux partition scheme (since I've got my personal data separate from my systems anyway).

Thanks a lot for putting the effort into replying and clearing this up for me :) Very much appreciated. I hope one day I'll be proficient enough with linux to be able to help other newbies out as well :p Thanks again.

---

