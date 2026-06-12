---
title: "Guide sought - reinstall with separate home partition"
date: 2012-04-24
forum: General Help
---

### Post by hawthornso23 on 2012-04-24
OK - my luck with upgrades finally ran out. Not surprising as the system has been upgraded all the way from Intrepid to Oneiric. The problem doesn't look too serious - for some reason it is hanging in lightdm on a blank screen and not getting to login - but rather than fuss about trying to fix it I think I'll just go for a fresh install which will let me switch to grub2 as well.

I have /home mounted on a second disk and all user files are there. It is a machine with six users. I can wipe the disk with the system on it and reinstall from scratch without touching user files. But I'm worried about how I will  get all the users back in business (if possible without having to change passwords) linked properly to their appropriate home directory with appropriate modifications to their config files so that stuff isn't broken for them by incorrect config stuff left over for the old system.

I should be able to wipe and do a fresh install to the system disk OK. But what I'm worried about is the process of getting the users hooked up their files. I'm worried that I might end up having to create six new users and manually change owners of a bunchaton of files and then muck about manually cleaning up six bunches of hidden config files to fix the inevitable breakages. 

I'm sure there is a clean way to do this and the process is not difficult. But since I've not done it before I need a decent guide to walk me through it. Could someone please point me at one?

Edit:    There seem to be a zillion guides for creating a separate home partition. And there are lots of comments that it makes upgrading easy. My guess is therefore that this is probably fairly trivial - perhaps self-documented in the install process - and thus nobody feels the urge to write a guide as to how to do it. So maybe the best way to proceed is to just give it a go. Since I'm wiping the system disk anyway I can't hurt anything as long as I take care to make sure the installer doesn't try to repartition the home disk. I have to download and burn an installation CD. If there are no comments here by the time that is done, I'll just go ahead and try it and see what happens.

---

### Post by RichardCain on 2012-04-25
I've done plenty of re-installs with a separate /home partition, albeit only with one user, but I can't see it would be any problem.  After installation, check to see if the users have been created.  If not, create them.  As long as you keep the user names exactly the same, Ubuntu should recognise the appropriate files.

My way of doing something like this would be to back everything up first, then go for it.  If it doesn't work, you can always get back to where you are now and nothing is lost.

---

### Post by techsupport on 2012-04-25
> **RichardCain said:**
> I've done plenty of re-installs with a separate /home partition, albeit only with one user, but I can't see it would be any problem.  After installation, check to see if the users have been created.  If not, create them.  As long as you keep the user names exactly the same, Ubuntu should recognise the appropriate files.

My way of doing something like this would be to back everything up first, then go for it.  If it doesn't work, you can always get back to where you are now and nothing is lost.

I concur! I know of no backup application that is specifically suited to exactly what the OP is requesting. It will need to be done manually since they are using multiple users with varying permissions folders/files.  

I would recommend instead, buying an internal TB hard drive, place it in an external NAS enclosure. Hook it directly to your router via ethernet. Boom, you have a file server.  Next time you need to do upgrades of this nature it won't be a headache again either.  That is the trend for most users these days.

:guitar:

---

### Post by hawthornso23 on 2012-04-25
Alright - it is doing something. But I'm not a happy camper. The installer doesn't offer anm option to reinstall keeping home and is appalingly vague about what it is doing. The advanced option seemed utterly determined to install on the wrong disk, and when I tried to specify a mountpoint for the existing home disk as home, unexpectedly commenced what sounded like a lengthy disk write scaring the crap out me as it wasn't what I expected it to do at that point. I hope like hell it wasn't commencing to reformat.


I rebooted back to the options screen and went with the option to upgrade 11.10 to 11.10 (duh). It immediately asked me to select a username and name for the computer which really doesn't sound promising in terms of keeping the existing users and files, and is now busy installing. To be honest I have no idea what disk it is installing to. It didn't ask me or give me feedback on that. I can only pray that it picked the right one. I'm half convinced it picked the wrong one given how implacably determined the advanced installer seemed to be to overwrite my home disk.

Why the hell doesn't this thing give more feedback as to what it is doing. It is like trying to repair a watch in the dark with leather gloves on.

At this point I'm committed. I just hope I haven't just wiped all my files.

---

### Post by techsupport on 2012-04-25
Wait. Don't upgrade without moving whatever you want to keep onto an external device, i.e. such as an external hard drive.  Or at the very least backup your very very important docs into the cloud, if you have no other options for backing up your data. 

Don't count on anything without moving your files some where else....  Why didn't you do a backup onto dvd-rs or something?  Manually. Eeek!

Drag and drop manually what you wanted to keep onto something.. right?

If you want a sloppy method, you could create a new partition to backup your stuff and install another partition for a fresh install of Ubuntu. Maybe?

> **hawthornso23 said:**
> Alright - it is doing something. But I'm not a happy camper. The installer doesn't offer anm option to reinstall keeping home and is appalingly vague about what it is doing. The advanced option seemed utterly determined to install on the wrong disk, and when I tried to specify a mountpoint for the existing home disk as home, unexpectedly commenced what sounded like a lengthy disk write scaring the crap out me as it wasn't what I expected it to do at that point. I hope like hell it wasn't commencing to reformat.


I rebooted back to the options screen and went with the option to upgrade 11.10 to 11.10 (duh). It immediately asked me to select a username and name for the computer which really doesn't sound promising in terms of keeping the existing users and files, and is now busy installing. To be honest I have no idea what disk it is installing to. It didn't ask me or give me feedback on that. I can only pray that it picked the right one. I'm half convinced it picked the wrong one given how implacably determined the advanced installer seemed to be to overwrite my home disk.

Why the hell doesn't this thing give more feedback as to what it is doing. It is like trying to repair a watch in the dark with leather gloves on.

At this point I'm committed. I just hope I haven't just wiped all my files.

---

### Post by hawthornso23 on 2012-04-25
YES 

Yes!!!!

- my files are OK. I'm back in business. One user only. But all user files are intact.

Huge sigh of relief.

Now I've just got to get the other five users back and linked to their files.

If I simply create users with the same name will they get their files back automatically given that the directories are still there in home.  [ edit: ANSWER = yes they will. Cool!]

---

### Post by techsupport on 2012-04-25
> **hawthornso23 said:**
> YES 

Yes!!!!

- my files are OK. I'm back in business. One user only. But all user files are intact.

Huge sigh of relief.

Now I've just got to get the other five users back and linked to their files.

If I simply create users with the same name will they get their files back automatically given that the directories are still there in home.

Good to know. Good job there! 

:lolflag:

---

### Post by RichardCain on 2012-04-25
> **hawthornso23 said:**
> my files are OK. I'm back in business. One user only. But all user files are intact.

Phew!!  Next time back-up first.  I speak as one who has made that mistake before, and it's not a nice place to be!  #-o

---

