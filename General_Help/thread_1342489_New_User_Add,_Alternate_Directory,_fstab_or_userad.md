---
title: "New User Add, Alternate Directory, fstab or useradd???"
date: 2009-11-30
forum: General Help
---

### Post by NertSkull on 2009-11-30
So I want to set up a new user on my computer that can act as an account to receive backups from my work computer.  But just to be safe I want to set up my ssh to only allow the work computer to have access to a handful of directories.

So I want to make the /home/newuser folder not be in the normal location, but instead mount it on a larger partition so that I can have plenty of room to back up the data.  I have come across two ways to do this (haven't tried either yet) and was hoping for some input on which may be the better way to go.

1) set up the new user/permissions and everything, but change my fstab file to cause the /home/newuser folder to be mounted on a different partition

2) user the useradd -d command to specify a home folder.  i.e. something akin to

useradd -d /mnt/Data/backup/ -m newuser

or something like that.

Is one better than the other??? Am I totally off and going about this in the completely wrong manner?  Any thoughts?  Thanks

---

### Post by jacobs444 on 2009-11-30
probably #1, but why not use the GUI user and groups tool, it is better to do it this way if this is a desktop version of ubuntu, just specify the home directory when customizing options.

System>administration>users and groups.

---

### Post by NertSkull on 2009-11-30
Well I can do that.  But isn't that essentially doing number 2, but just graphically.  So if thats the case it kind of seems you are suggesting doing both 1 and 2.

---

### Post by jacobs444 on 2009-11-30
it is, though it ensures everything gets set correctly.

I am trying to make it easier for you. Good luck

---

### Post by kaspar_silas on 2009-11-30
I have used both ways without any problems before thou I guess the fstab way is slightly riskier. 

You could also remove he original home and make a symbolic link. ie.
ln -s /mnt/Data/backup /home/newuser

Are you going to back up certain files from your work or your whole home drive from your work. If the latter you should be careful with permissions.

Previously I shared a home directory and forgot about the different computers having different user UIDs for me. Wasn't hard to fix when I realized but it led to weird xserver messages.

---

### Post by NertSkull on 2009-11-30
Sounds good.  Seems like either should work.  I'll probably try your suggestion first.  Thanks.

---

### Post by NertSkull on 2009-12-01
> **kaspar_silas said:**
> I have used both ways without any problems before thou I guess the fstab way is slightly riskier. 

You could also remove he original home and make a symbolic link. ie.
ln -s /mnt/Data/backup /home/newuser

Are you going to back up certain files from your work or your whole home drive from your work. If the latter you should be careful with permissions.


I'm planning on backing up most of my work computer onto my home computer.  I'm not sure I see what you mean by careful with permissions though.  My work computer is a Windows machine that I have running cygwin and then duplicity.  I was going to have them back up files onto an extra internal drive on my home computer.  But since my work computer is kind of shared I didn't want to risk having it have access to my whole computer.

So because of that I was going to make a new user with limited permissions, ssh (scp) into that user account from the work computer to back up files.  But I also wanted to have the backup folder on a large disk because its a lot of data.

I've never done anything with symbolic links before.  Would that be better than the fstab or changing the /home folder location?

---

### Post by kaspar_silas on 2009-12-02
You can probably ignore the file permissions thing. It's only if you are actually sharing a home drive. What you are doing seems sensible to me.

I don't know if the symbolic links way is especially better. It just stops you having to mess about with the fstab file.

---

