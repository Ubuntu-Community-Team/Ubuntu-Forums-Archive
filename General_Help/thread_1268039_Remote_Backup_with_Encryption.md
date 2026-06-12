---
title: "Remote Backup with Encryption"
date: 2009-09-16
forum: General Help
---

### Post by NertSkull on 2009-09-16
So I'm still in the learning curve for Ubuntu, but things are going well.  I'm kind of stuck on this problem and was hoping for some guidance.

What I want:

I want to back up my files (don't really care about system files/programs, just my data) remotely so that in case of damage/theft they will be backed-up somewhere else.  So I want to back them up to a computer I have set up remotely, but I don't want them to be accessible to anyone in that home (my parents).  So I want to have them encrypted.  Also I'm a phd student so I have a LOT of data and don't want to back it all up all the time so I need something that will do incremental backups (or differential would work).  Any ideas?

What I know:

-sbackup allows remote/ftp backing up, but I don't see any encryption ability.  Am I wrong?  
-I'm not great at command line or scriptting but I'm learning, so I looked at rsync (using grsync) but I didn't see any remote ability or encryption ability.
-I've also looked at some just encrypting options like truecrypt or something to encrypt first, and then back-up.  But I'm stuck there as well.

So that's kind of where I am.  Any help would be greatly appreciated.  I've been backing up to a local external USB drive, but I had someone try to break into my house recently so I want to go to a remote system.  So let me know if you have any ideas of where I can go to get started.  Thanks everyone.

---

### Post by NertSkull on 2009-09-16
Oh I forgot to mention Duplicity.  I've come accross this one as well and it appears to do everything I need.  But its all scripting which is something I've never done before.  I've been reading about it, and trying it out but not having a tone of success yet.  I've also read that it may be kind of shaky on being maintained in the future.  Is this something to be concerned about?  Is it my best option?  Is there any sort of a bit more user-frienddly GUI form for it?  Thanks!

---

### Post by XCan on 2009-09-16
I too have tons of data on my workstation which I regularily backup. Personally I use rsync, however, I don't use it with encryption. If you think rsync can suit your backup needs, perhaps the easiest is to do it through a script? I guess there are several possibilities, but you could, for example, write a script that first mounts your truecrypt volume, runs rsync, and then unmounts your truecrypt volume? I have an encrypted volume that I mount on more or less every boot through a script.

---

### Post by NertSkull on 2009-09-17
Interesting.  So I haven't actually set up truecrypt yet.  But let me see if I understand what you mean.

Basically create a volume that stores all my data and encrypt it with the true crypt.  Then mount that and have rsync back up that entire volume?

If I do that, will rsync be able to handle the pre-encrypted information on the volume?  And if doing an incremental back up will it be able to just back up single files (as most hasn't changed) in an encrypted fashion towards the remote server/computer?

thanks for the idea, its definitely something I will look into.

---

### Post by XCan on 2009-09-17
Yah, I think you got it. But just to clarify, create a truecrypt volume (this could even be a file, you don't need to partition your hdd), mount the truecrypt volume, run rsync, and dismount the volume. 

As soon as you mount the truecrypt volume, it will ask your for a password, and this will decrypt your volume making it readable. So from the outside it just looks as any directory, thus rsync wouldn't have any trouble. rsync will do incremental backups, it will compare each file, and only transfer the changes. Using rsync is rather straight forward for the simplest cases, for example,
```
 rsync -avz /src/dir /dest/dir 
``` is all you need to type to backup two dirs. Over the internet, you could simply let rsync run though ssh. Great docs with examples [http://www.samba.org/rsync/documentation.html](http://www.samba.org/rsync/documentation.html) .

---

