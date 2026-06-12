---
title: "Fail to recognize files on mounted NAS drive"
date: 2009-07-14
forum: General Help
---

### Post by rwintner on 2009-07-14
I'm new to Linux, but I am very familiar with computers and more than one OS (although not Unix).  Having said that...

I'm running Ubuntu 9.04 on my old laptop with an Intel Celeron 2.66GHz and 1.2GB RAM.  Pretty vanilla.

I found info on how to mount my NAS file folder with my music collection (all mp3 files) and I now have a drive icon on my desktop that's labeled correctly.  Here's what I did:

I added this line to fstab--
//192.168.50.99/MUSIC/mp3/mp3%20-%20192kbps /home/russell/Music/ cifs nounix,username=rwintner%password,uid=russell,gid=russell,file_mode=0777,dir_mode=0777 0 0

which points to the beginning of the sub-directory tree of my music collection.  My NAS device is only a few years old, ADS NAS Kit, but it's no longer supported by ADS.  In fact, they don't even list it in their legacy products.  It seems to be using SMB, it formats the drive ext3, and if I simply use the Connect to server... option in Places, I connect and can scan all of the subdirectories and files, no problem.  But if I click on the icon for the mounted drive, I get this:


Could Not Display &#8220;/home/russell/Music&#8221;
The file is of an unknown type


I tried to look up all of the options for CIFS but found nothing obvious that I could add to fix this, except sdu, which I tried and didn't help.

Oh yeah, I need to have the folder mounted in order to use the files in my music players and music server.  They won't accpet a network drive by URL.


Help anyone?


--Russ

---

### Post by michaelzap on 2009-07-14
Try the new GVFS method for mounting your share instead:
[http://ubuntuforums.org/showthread.php?p=7563868](http://ubuntuforums.org/showthread.php?p=7563868)

I've had a lot better luck with that than CIFS via fstab (tho that works also). I always used to mount my music library and other NAS shares via fstab, but I think I'm done with that now. It was always a bit of a hack, and it wasn't appropriate for multi-user systems.

You'll want to create a symbolic link to the hidden .gvfs directory so that your music program can easily access your library (I posted the command to do that in the above thread, in case you need it).

---

### Post by rwintner on 2009-07-14
Thanks.  This is easier, but I still have the same issues.  Although, I think I am getting closer to understanding the real issue here.

Two problems:

1. Using Rhythmbox I can easily traverse the subdirectories on the mounted NAS drive.  But, when I try and import a file (mp3 or wav) is says that it couldn't open the file for reading.

2. My real goal is to use FireFly so I can use my Roku Soundbridge.  In the config file, it won't accept a string "smb://*anything*".  It requires the Samba linked NAS drive to appear as /home/media/music which the fstab method is supposed to accomplish.  But using that method, I got the error I reported earlier: 
Could Not Display &#8220;/home/russell/Music&#8221;
The file is of an unknown type

Ughhh...

---

### Post by michaelzap on 2009-07-14
> **rwintner said:**
> Thanks.  This is easier, but I still have the same issues.  Although, I think I am getting closer to understanding the real issue here.

Two problems:

1. Using Rhythmbox I can easily traverse the subdirectories on the mounted NAS drive.  But, when I try and import a file (mp3 or wav) is says that it couldn't open the file for reading.

2. My real goal is to use FireFly so I can use my Roku Soundbridge.  In the config file, it won't accept a string "smb://*anything*".  It requires the Samba linked NAS drive to appear as /home/media/music which the fstab method is supposed to accomplish.  But using that method, I got the error I reported earlier: 
Could Not Display “/home/russell/Music”
The file is of an unknown type

Ughhh...

I created symbolic links to my GVFS mount paths and used those as library links and whatnot:
```
ln -s ~/.gvfs/'mp3s on server' ~/Music/shared
```
That does the trick for Exaile, and it also allowed me to keep the exact same paths that I had before switching to GVFS so that programs with saved path info wouldn't need to be updated.

---

### Post by rwintner on 2009-07-14
Am I supposed to subsitiute anything in the command?  I did this and got a broken share.

BTW, if I double click on one of my songs on the NAS, itopens up MoviePlayer and plays.

---

### Post by michaelzap on 2009-07-14
> **rwintner said:**
> Am I supposed to subsitiute anything in the command?  I did this and got a broken share.

Well, yes. Those are just example share and link names. You should look in your .gvfs folder and substitute your own share name, and of course you can put the symbolic link wherever you like (I just created a shared link in your Music directory as an example).

If you haven't mounted your GVFS shares, the symbolic link will say it's broken if you click on it. That's just because the share doesn't exist in GVFS until you mount it. Mount your GVFS shares and try again if you get that error.

---

### Post by rwintner on 2009-07-14
You're being very patient.  Thank you!

---

### Post by nelamvr6 on 2009-07-14
I had much better luck mounting my NAS using NFS instead of CIFS, if your NAS supports it.

My fstab entry looks like this:

192.168.0.176:/backup /media/backup nfs defaults 0 0

You have to make sure you have NFS installed of course.

---

### Post by rwintner on 2009-07-14
Well, half the battle has been won!  I can use Rythmbox and I see the link to shared in my Music folder.  Unfortunately, when I put the path /home/russell/Music/shared in FireFly config and try to save it, I get Error: 500general:mp3_dir

Unless you now why, I guess I need to go to that group.

Thanks again!

---

### Post by michaelzap on 2009-07-14
> **rwintner said:**
> Well, half the battle has been won!  I can use Rythmbox and I see the link to shared in my Music folder.  Unfortunately, when I put the path /home/russell/Music/shared in FireFly config and try to save it, I get Error: 500general:mp3_dir

Unless you now why, I guess I need to go to that group.

Thanks again!

Glad you're getting there! I don't use Firefly, so I can't say for sure, but does it work if you tell it to look for files in ~/.gvfs/'mp3s on server' (using your share name, of course)? That is the actual mount point afaik, so I would think that it would work as well as an fstab mount point.

Does Firefly run as root or another user (not you)? If so, that could also be an issue. The only negative that I've found with GVFS mounts is that they're only accessible by the user that mounted them. Other users (or even you using sudo) can't access those shares at all.

In that case you might need to also mount the share as the Firefly user before starting it up.

---

### Post by rwintner on 2009-07-14
> **michaelzap said:**
> Glad you're getting there! I don't use Firefly, so I can't say for sure, but does it work if you tell it to look for files in ~/.gvfs/'mp3s on server' (using your share name, of course)? That is the actual mount point afaik, so I would think that it would work as well as an fstab mount point.

Does Firefly run as root or another user (not you)? If so, that could also be an issue. The only negative that I've found with GVFS mounts is that they're only accessible by the user that mounted them. Other users (or even you using sudo) can't access those shares at all.

In that case you might need to also mount the share as the Firefly user before starting it up.
I only have 1 user and it's me.  And, obviously, I'm logged on as me.  So that's not it.

I tried ~/.gvfs/'mp3s on server' substituting 'mp3s on server' for 'music', the name of the directory on the NAS drive.  No luck.  Same error 500.  Since it's working with Rythmbox, I'm really surprised that I'm having an issue, but then, Linux seems to have so many choices in how you can do something, I can see where not all apps yiled the same results.

---

### Post by michaelzap on 2009-07-15
But does Firefly run as root (sudo)? That seems to make shares mounted this way inaccessible. If so you might need to run your mount command as sudo also before starting Firefly.

---

