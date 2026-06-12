---
title: "Serious start-up problems"
date: 2006-05-23
forum: General Help
---

### Post by nalmeth on 2006-05-23
Booting up Breezy 5.10 (with all my media/data) I get some serious system failures.
First (on ubuntu splash) 
Setting up Networking : Failed
Synchronizing to ntp.ubuntu.whatever : Failed

Then usplash stops on:
Starting System Log Daemon : 

Eventually I get the verbose info
Here is the output I'm getting, don't know what to make of it (only negative output):```


/etc/rc5.d/S39ifupdown: Line 77 : /etc/network/run/ifstate : read-only filesystem
Failure initializing

/etc/rc5.d/S41hotplug-net : /etc/hotplug/.run/net.enable : read-only filesystem

Started System Log Daemon.socket: Address already in usemm ::[FAILED]
``` Like I said, I don't really know what to make of it. It's the first I've seen anything like this with my Ubuntu. I've done nothing out of the ordinary with my system, in fact I've been out of town for the weekend until yesterday.

What do you guys think? Look at all familiar? I'm willing to reinstall, I was going to reinstall dapper from scratch, but unfortunately just formatted that partition last week. I just want to be able to get in and save my data.

Please, anything you may be thinking, pass it on.

Thanks greatly :)

---

### Post by nalmeth on 2006-05-23
I've booted into recovery mode, and suprisingly was prompted for a root password.
I entered it, and now even as root, I can't touch anything in my 5.10 system.
Everything is read-only, even though I am root.

What is up with this? How can my entire file-system become read-only?

---

### Post by nalmeth on 2006-05-23
I thought I found a couple of leads, but I haven't gotten anywhere.

I can gain write access to the drive when I'm eventually carried (over the failed startup) into a terminal, by entering:
sudo mount /dev/hda1 -o rw,remount

But when restarting, it's back to read-only, failed startup.

I read that I might have damaged my filesystem somehow, but in Damn Small Linux, running sudo fsck -y /dev/hda1 I get:
```
dsl@box:~$ sudo fsck -y /dev/hda1
fsck 1.34-WIP (21-May-2003)
e2fsck 1.34-WIP (21-May-2003)
/: clean, 344447/18202624 files, 29821028/36401274 blocks
```

Does this mean that my filesystem is clean?

I seem to be stuck here, as the filesystem is booting as read-only, and it does not appear to be damaged. I'm out of ideas

---

### Post by professor_chaos on 2006-05-24
I can only think of checking /etc/fstab or /etc/mtab for anything that has changed with the options for mounting /
By default / is mounted ro with errors, but I dont see anything from your posts that would suggest errors in your filesystem

---

### Post by nalmeth on 2006-05-24
Thank you for replying Professor_Chaos!

I checked fstab, and everything seemed in order, and as you say it's set to mount ro with errors, but again as you say, I can't diagnose any source of error!

I have not checked my mtab, but will do when I get home.

Do you think it is safe to resize this troublesome partition? My original intention was to format my old dapper partition, make it a data partition, resize this breezy one, and install dapper along-side breezy. I have moved maybe half my media to the data partition. 

If it is safe, I would like to resize the hda1 (breezy) tonight and install dapper, but I am a little concerned with this situation.

Can you suggest where I might find some assurance/discouragement? 

BTW are you still teamed up with General Disarray? :D

---

### Post by professor_chaos on 2006-05-25
Yes, but ever since General Disarray bought a MAC, we don't talk much anymore :)

I apologize, I'm not sure I can give you any advice or reassurace when it comes to partitioning and formating, as they are risky actions. 
But on the plus side, you do have access to the contents of the hard drive and at the very worst, you just have to fresh install and waste a few hours, but all of your files you backup will be intact. 

But if ANYONE out there can save nalmeth some time by suggesting a solution to his problem....
I never liked the idea of just reinstalling to fix a problem, just like I don't like rebooting to fix something.

---

### Post by nalmeth on 2006-05-25
> Yes, but ever since General Disarray bought a MAC, we don't talk much anymore :) Hahaha didn't see that one coming :o

Thanks anyway, I've had my time with partitioning/formatting, and not alien to the process, but I'm just a little concerned considering I've been having these unfamiliar problems with this particular partition.

I'm only afraid that I'll lose all my media.
> but all of your files you backup will be intact 'fraid I only half backed-up... :embarrased:

Again, thanks for responding, even if you don't have a god-like miracle solution :)

I'll probably go ahead with it tonight anyway, then be in a sour mood tomorrow having in fact toasted the partition. 

Oh well
C'est la vie

---

### Post by ifokkema on 2006-05-25
[QUOTE=nalmeth]I read that I might have damaged my filesystem somehow, but in Damn Small Linux, running sudo fsck -y /dev/hda1 I get:
```
dsl@box:~$ sudo fsck -y /dev/hda1
fsck 1.34-WIP (21-May-2003)
e2fsck 1.34-WIP (21-May-2003)
/: clean, 344447/18202624 files, 29821028/36401274 blocks
```

Does this mean that my filesystem is clean?[/QUOTE]

Yes and no. When you issue a fsck, it doesn't really check your drive. It just looks at the filesystem info which is stored on the disk. Use the -f flag to force fsck to actually check your system. However, it is NOT recommended to do this on a mounted filesystem, so you may want to do this from the Ubuntu Live CD.

From recovery mode, if you've remounted your drive rw, you can try an `sudo init 5` to boot up normally. I assume during boot your system had a problem with the drive.

HTH,

Ivo

---

### Post by nalmeth on 2006-05-25
I thought that running the -y option told fsck to repair any damage? Is this incorrect? From the output of fsck -y does it look like my filesystem is damaged?

I was running it from D.S.L.

---

### Post by ifokkema on 2006-05-25
[QUOTE=nalmeth]I thought that running the -y option told fsck to repair any damage? Is this incorrect? From the output of fsck -y does it look like my filesystem is damaged?[/QUOTE]

From the manpage of fsck.ext3:
       -f     Force checking even if the file system seems clean.
(...)
       -y     Assume an answer of ‘yes’ to all questions; allows e2fsck to be used non-interactively.

So using -y doesn't make fsck check your drive if it SEEMS clean. -f does. -y just makes fsck answer 'yes' to all questions it would otherwise have asked you for.

From the output you've given, it shows fsck didn't really check your drive. It says it seems clean, without actually checking if that's true. I've had cases myself when fsck said it looked clean, but when actually running fsck with the -f option, it found some problems on my drive anyway.

Ivo

---

### Post by nalmeth on 2006-05-25
Thanks for clarification.
I go around telling people to **man** their command and should have done myself.
I will try this out.

---

