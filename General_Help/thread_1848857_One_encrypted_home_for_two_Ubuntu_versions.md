---
title: "One encrypted home for two Ubuntu versions"
date: 2011-09-23
forum: General Help
---

### Post by DzmitryG on 2011-09-23
Basically, I've got two Ubuntu versions installed - one 10.04 LTS and the other - 11.04 with Gnome3 (aka more experimental). There is also a separate encrypted home partition that I set up from 10.04. Right now I use chroot to be able to read the encrypted data from the home partition when I use 11.04. But I would prefer to mount the partition as a home under 11.04, too.

The question is: will it work? I.e. can the two Gnomes use the same home safely?
And if yes, how would I do it?

Thanks!

---

### Post by oldfred on 2011-09-23
I do not know encryption, so I can only give part of an answer. 

Even if you did not have encryption which to me is an extra level of complication, I would not suggest sharing. Home can be considered as two things. 

One is the partition which you can easily share but should still have different users within the partition. I think that does not solve the issue of easily getting to the data. 

The other is the user and that usrs settins & data. I often recommend a separate /home to make it easy to upgrade. Software is designed to read an older configuration file and update to the newer version. The issue becomes once updated it make not work or work well with the oldr version of the software. New/Changed/Deleted settings may be enough different to create problems.

But /home has two parts. The mostly hidden files &  folders that are user configuration settings and some files or hidden files that are the user data. If sharing with Windows we suggest having most of the data in a shared NTFS partition so you do not need a large /home or may not even need a separate /home. Many of us also have separate /data partitions in Linux formats for data also. 

My /home is now just over 1GB with 3/4s of that .wine as that is not as easy to redirect to another partition. But I am aggressive in moving any data file to another partition. I use linking to make my /home look like a standard /home but links for Documents, Downloads, etc go to folders in another data partition.

You may be able to have two /home partitions (separate or inside / ), only copy a few settings that you want from one to the other and then have a separate encrypted data partition. Not sure what encryption adds to the complexity of trying to share a separate data partition.

---

### Post by Nostalos on 2011-09-23
From an encryption standpoint but without having done it myself using cryptfs (i maintain 2 homes via LUKS/LVM).  I would have to say your best answer is going to be "Possibly".   If you created the original with 10.04 and mount it from 11.04 it should work.  New features might not be backwards compatible.  Example my encfs folder using defaults from 11.04 will not mount on a 10.04 server. 

Also I agree 100% with oldfred.  While Gnome2 and 3 use some seperate config folders there are other app issues as well.   Example,  Firefox 3.6 and 6.0 do work, but trying to share the same .mozilla folder for each gets to be troublesome at best.  Same goes for pretty much any other apps of differing versions between the two distros.  

I say Probably, but I can think of more reasons for it being a bad idea than a good one.

---

### Post by DzmitryG on 2011-09-24
**oldfred**, that is actually a good idea - to have home in root, but hardlink documents to a different partition. I think I'll try it, so that both Ubuntus will have their own home in / and, therefore, their own config folders. I will remove encryption from the data partition, too. And then hardlink folders on the data partition to the folders in both homes, respectively. Does anyone see potential problems doing it this way?

---

### Post by oldfred on 2011-09-24
I use soft links, never have used hard links. Is that a requirement with your encryption? I would think data is what you want to encrypt not the system as that is the same for all of us.

Splitting home directory discussion Post #4 is oldfred's details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)

As long as you are using Debian based systems sharing works well, issues with other systems.
Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by DzmitryG on 2011-09-25
So I moved home under 10.04 into root partition and did symlinks to the folders in a data partition, however the folders do not sync with Ubuntu One. I guess, a link to a folder is not the same as the folder. Is there a way to make it look like a folder? Will bindfs, for example, do the job? I would think that mounting a directory should help.

---

### Post by oldfred on 2011-09-26
I do not use UbuntuOne. But I have seen several posts by Morbius1 where the bindfs method worked better with some networking issues.

Only in one or two cases have I had an issue with the links and in each I just refered to the underlying actual mount. In a script for example I do not use ~/Documents (the link) but /mnt/data/Documents (the place the link refers to).

---

### Post by DzmitryG on 2011-09-26
Bindfs did the trick. I am currently syncing.
Thank you guys for your help, especially **oldfred**.

---

### Post by oldfred on 2011-09-26
Glad you got it working.:)

---

