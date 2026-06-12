---
title: "recommended backup software or scripts?"
date: 2011-07-11
forum: General Help
---

### Post by dbloom on 2011-07-11
I'm not sure if I'm posting in the right place, but i've been researching how to set up a simple backup to remote server solution.  Tried DejaDup, which worked fine at first, but now has issues.  I was looking at Super Simple Backup (sbackup), but the caution statement at the top of the web site makes me wary.  Right now I'm thinking the best thing might just be adding rsync to a cron job and see how that goes.

Before I completely give up, I was wondering what the community uses.  What do you use?  And have you had to restore?  If so, how did that go? 

Any advice is appreciated.  I already have an NAS set up with plenty of storage.  All i need is to back up that home folder (and maybe some others).

Thanks!

---

### Post by dFlyer on 2011-07-11
What issues are you having with deja dup?

---

### Post by Lars Noodén on 2011-07-11
> **dbloom said:**
> ...Right now I'm thinking the best thing might just be adding rsync to a cron job and see how that goes.
...

That would be my recommendation for most situations.  It works well.

---

### Post by dbloom on 2011-07-11
Well, this setup is actually on my mom's computer, which i don't have direct access to so the communication of the error may not be perfect... That said, DejaDup failed due to "broken pipe".

Seems to be a duplicity issue, but i'm not sure how to deal with it, especially not having access to her pc right now.  i assume it couldn't log into the NAS for some reason so i may try adding it to her fstab to see if an always on connection would help.  

Any ideas on how to deal with would be helpful too? Thanks.

---

### Post by Gyokuro on 2011-07-11
I'm a big fan of rsync and maybe **rsnapshot** is something for you.

---

### Post by dbloom on 2011-07-11
> **Gyokuro said:**
> I'm a big fan of rsync and maybe **rsnapshot** is something for you.

funny, i was just reading about rsnapshot.  it's worth a try.  i think i might check out that o'reilly book, 'Back & recovery' featured on the web site.  thanks!

---

### Post by dbloom on 2011-07-11
What about [Back In Time]("http://backintime.le-web.org/")? This looks promising too.  Anyone have experience with this?

---

### Post by bpb_21 on 2011-11-15
> **dbloom said:**
> 
...
I already have an NAS set up with plenty of storage.  All i need is to back up that home folder (and maybe some others).

Thanks!

I use luckyBackup with Ubuntu 11.10.  It's a good front end to rsync (I believe) and does exactly what I need it to do: copy my home folder and a few others.  I needed a backup solution where the files backed up would be accessible, on the remote server, from another system if my main production laptop were to crash.

I've had the same issues with deja dup; works fine at first but subsequent backups ... just don't.

---

### Post by GSD4ME on 2011-11-15
I am interested in people's views here as well

I am trying to establish a backup scenario for my laptop, where I want files saved to an external drive.

I used to use DejapDup to backup to Ubunto One cloud, but since going to 11.10, it fails miserably to operate at all.
Similar problems (apparently now well known by others) with Ubuntu One on 11.10 where it won't even sync with the cloud (or anything else it seems from discussions elsewhere)

So I went to backup to an external drive
Tried Lucky Backup  - wouldn't recognise my external drive
Tried Deja Dup again with the HDD - were problems but I cannot exactly remember what they were! (Not forgetting the missing capabilities (such as excluding "." files) and the simplistic GUI that precludes anything remotely beyond basic functionality being carried out)
Tried BackInTime but kept getting some sort of error that I cannot find an answer to ("Profile : Main profile : snapshots folder is not valid") when I try to specify the HDD as the target for the backup

All I want is a system where I can backup my files, simply, with a good GUI, able to recognise external drives and be able to specify a whole range of file types as exceptions.
Getting frustrated about this subject now as, being a recent convert from Windows to Linux, at least the system I had previously on Vista worked a treat to enable remote backups to a cloud repository.

If anyone comes across a decent system, please leave a posting here as I have searched the software repository and tried them all with no success

Many thanks

---

### Post by bpb_21 on 2011-11-15
> **GSD4ME said:**
> 
...
I am trying to establish a backup scenario for my laptop, where I want files saved to an external drive.
...
So I went to backup to an external drive
Tried Lucky Backup  - wouldn't recognise my external drive ...

Many thanks

LuckyBackup wouldn't recognize your external drive?  Now that's odd, because I'm using an external drive on a remote server to back up using LuckyBackup without problems.  That makes me think something else is going on with that external drive other than LuckyBackup.  I've had great results with it, but of course your mileage may vary.  Any error messages in particular from LB, or it just can't see the drive when you go to select the backup path?

---

### Post by GSD4ME on 2011-11-16
Forget that last complaint!

Managed to get LuckyBackup to use my external HDD - the problem (if I could call itthat) was that I was expecting the HDD to show up in the available options for the 'destination' directory, but when I started to type "/media" the GUI recognised what I was trying to do and gave me the option of using the HDD, so problem solved.

So I did a backup of my directories - VERY impressive!! Very quick, very informative, very reliable.

Will be my package of choice for backups from now on.

Gold star to be awarded to LuckyBackup

Thanks for the help

---

### Post by cscj01 on 2011-11-16
Here's another vote for LuckyBackup.  I have been using it successfully for quite a while to backup my data disk to a remote external drive on another computer on my home LAN.  No problems, ever.  It uses rsync and has many options.  I also use Clonezilla to copy my system drive to a local external drive.  I have been able to completely restore the Clonezilla backup on two occasions.  One was after a system snafu.  The other was when I upgraded my internal discs to larger ones.  It works great for that purpose.

---

