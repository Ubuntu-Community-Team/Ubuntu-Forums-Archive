---
title: "What the heck is eating up my hard drive space?"
date: 2010-12-25
forum: General Help
---

### Post by Th3Professor on 2010-12-25
Something that seems to be running hidden in the background is constantly eating up hard drive space off of my root partition.

I've partitioned off other sections of my HDDs to allow for storage space and editing space and such, though I only set aside about 19G for my root partition (enough for the system install (in root, /bin, /dev, /etc, and such) and the /home files).

17G of the 19G is used... just 2 minutes ago it said 870M is free, and now it says 857M is free. Something's eating up the space and at a fairly fast rate, too, but I have no idea what it is.

I'm searching for possible causes and so far the only thing I can find that is currently taking up a lot of space is "/home/[user]/.Private". Although ".Private" is within "/home" it is also being treated as a separate partition but still within the 19G limit.

Is there possibly something going on in ".Private" that is constantly taking up more space (and what might that be)?

I'm not downloading anything. I'm not extracting or installing anything.

Everything in "/home" adds up to 12G of the 19G partition.
Everything in the ".Private" of one user's "/home" space adds up to 17G of the 19G.

Maybe it has nothing to do with ".Private" but maybe something else entirely. I have no idea.

I've cleared out all caches from web browsers and /tmp is only using 840M.

What's going on here?

:confused:

I'd just like to stop whatever it is from constantly eating up hard drive space.

Thanks!

---

### Post by Th3Professor on 2010-12-25
Also...

Is there a way that I can monitor in real-time HDD usage per directory/partition so that I can detect exactly where the hard drive space is being "eaten up" and such?

---

### Post by 4Orbs on 2010-12-25
Is your Private folder perhaps the mount-point for a Data or shared partition? If so, and the shared partition fails to mount, then any files you put in that Private folder will be written to the folder anyway, but won't be on the shared partition, but in the Private folder in your /home partition. If this is the case, you can check it by unmounting the shared partition then look inside the Private folder. If there are saved files still showing in the Private folder, it means that you have duplicate files... one on the shared partition and the same file in the Private folder but located in your /home/Private space. OR, those files may not be duplicates, but only located in your /home userspace and deceiving you into believing they are on the shared partition. This happened to me once upon a time.

---

### Post by Th3Professor on 2010-12-26
Hi, I'm confused by your response, sorry. :( I don't even use the ".Private"/encrypted folder stuff. And yet, there's like 17G of stuff in there.

I disabled my internet and did periodic "df -h" from command line and, still, hard drive space is being eaten up.

I'm getting really worried about what the heck is causing this.

...and it's happening fairly fast too. :( I'm now down to about 750M free on / and those 200-ish megs have vanished just in the past couple hours.

edit - okay strange, there is now 7G of stuff in ".Private"...and yet I'm still losing HDD space on "/" and everything in that partition. I have less than 750M free out of a 19G partition and it just shouldn't be anywhere close to that low. :(

edit2- okay, looks like "/home/username" has a lot more than just 2G of stuff. @#%^& arg... I'm trying to find out what the heck is taking up all the space in username's home but what is really worrying me here is that I was *still losing space* *even* after I *disabled* the internet. :( That's just spooky. Anybody have any ideas what might be going on or how to remedy this?

edit3- okay now the /home/username is showing 18.7G used on a 19G partition... and it is something in a hidden folder. I rechecked ".Private" and it's up to 9.7G... why "private" keeps changing is beyond me.

final-edit- okay it looks like "home/.ecryptfs/username/.Private" is taking up lots of space, but it's still sitting at 9.7G. I have no idea where the 17G (of the 19G partition) is being used though, it seems the majority of it would have to be from somewhere, unless without that 9.7G the remaining space used is normal. Can I just delete that ".Private" stuff? I don't even know how to access it. It just shows text-like files with weird scrambled filenames and folder names.

---

### Post by 4Orbs on 2010-12-26
Sorry for my confusing post. If the private folder is something you did not intentionally create yourself, then my post has no relevance to your problem. Hopefully someone else will come along with a solution.

---

### Post by lisati on 2010-12-26
Things that come to mind are temporary file that are created when you, say, watch videos online or when you apply updates to your system.

Files stored in /tmp are usually deleted when you reboot.

---

### Post by mbobak on 2010-12-26
Ok, first, do:
```
df -k
```

to see what partition has all the space taken up.

Next, cd to that partition, then do:
```
du -sk *|sort -n
```

This will show you which directory has the most space used up.
cd into that directory, and repeat the 'du' command above.

Continue until you find the file or files taking up all the space.

Now, use the 'fuser' command to determine what running program has that file open.

Hope that helps,

-Mark

---

### Post by Th3Professor on 2010-12-26
> **4Orbs said:**
> Sorry for my confusing post. If the private folder is something you did not intentionally create yourself, then my post has no relevance to your problem. Hopefully someone else will come along with a solution.

Can I just go into the ".Private" directory and delete everything in there? Or, how do I actually access that stuff to make sure I don't need it? It's apparently taking up 9.7G of the 19G partition (if that is actually part of that partition, it's weird, like it's a partition within a partition).

> **lisati said:**
> Things that come to mind are temporary file that are created when you, say, watch videos online or when you apply updates to your system.

Files stored in /tmp are usually deleted when you reboot.

I went into /tmp and did a rm -rf (of only the tmp things of course) and that brought my "/" up from about 680M to 1.1G, so that helps... though I don't know what the heck is eating the space up (and it's happening when I have internet disabled and am not running any visible programs or any programs that I'm at least aware of).

> **mbobak said:**
> Ok, first, do:
```
df -k
```to see what partition has all the space taken up.

Here's a df -kh ...

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              19G   17G  1.1G  95% /
udev                  2.0G  400K  2.0G   1% /dev
none                  2.0G   20M  2.0G   1% /dev/shm
none                  2.0G  200K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda1             942M  112M  783M  13% /boot
/dev/mapper/vg0-vault
                      755G  740G   16G  98% /studio/vault
/dev/sda2             187G   92G   96G  49% /windows
/dev/mapper/vg0-zone   87G  184M   83G   1% /zone
/dev/sda6             216G  204G  516M 100% /studio/workspace
/dev/mapper/vg0-nomad
                       87G  184M   83G   1% /nomad
/home/username/.Private    19G   17G  1.1G  95% /home/username
/dev/sr0              1.7G  1.7G     0 100% /media/cdrom0
/dev/sde1             932G  901G   32G  97% /media/My Book
```These I was previously aware of as having very little space remaining, and I don't think the space is being "eaten up" on them:

```
/dev/sda6             216G  204G  516M 100% /studio/workspace
/dev/sde1             932G  901G   32G  97% /media/My Book
```These (or this (singular? plural?)) is/are what's concerning me:
```
/dev/sda5              19G   17G  1.1G  95% /
/home/username/.Private    19G   17G  1.1G  95% /home/username
```Having deleted the /tmp stuff helped bring up the dwindling space to 1.1G but it's still being eaten away by something. :( (i.e., I'm already down to 1.0G and I haven't done anything to lose that 100M since I ran that "df -kh" command a few minutes ago.)

> Next, cd to that partition, then do:
```
du -sk *|sort -n
```This will show you which directory has the most space used up.Here's du -skh /home/username/.Private|sort -n ...

4.0K

4? ...confusing. ...wait, it's a shortcut.

Okay, I'll try that on "/home/.ecryptfs/username/.Private" ...

```
9.8G    /home/.ecryptfs/username/.Private/
```...oh great :( now the previous 9.7G has gone up to 9.8G. arg @#%&

But I suppose the main culprit in all of this is, at least for now it seems, that ".Private" stuff (which I'm not even awaringly using).

> cd into that directory, and repeat the 'du' command above.

Continue until you find the file or files taking up all the space.Okay I did "du -skh [that Private dir]/* |sort -n ... and there doesn't appear to be anything that would add up to 9.8G ...

The largest things in there are -

A few files about 125M, 146M, 317M, and such, but otherwise a handful of kilobyte-size files, that's it.

And each file has a weird name like:
"ECRYPTFS_FNEK_ENCRYPTED.WkacAaJnFbsd2J5WYy16uifD74V.ShK--"

I don't know how to see what they are.

...woh... wait a sec...

I was using command line and that's all I found. I just re-checked using nautilus file browser and 1 file is 7.3G.

> Now, use the 'fuser' command to determine what running program has that file open.

Hope that helps,

-MarkI'm not familiar with "fuser" but trying it now...

Okay apparently I cannot use it with a private/encrypted file.

So I suppose this narrows down to 2 concerns now:

1. How do I access those ".Private" files/folders in an unencrypted way?

(That will help me determine what that 7.3G file is.)

2. How do I stop the computer from automatically eating up hard drive space?

(It seems that fuser doesn't let me see what's running that 7.3G file (if that file is open or if it's actually the space-eating file that mysterious-program-X is using.))

edit - of the 9.8G space used (and increasing) that 7.3G is only 1 file... and all of that within that "ecryptfs"/".Private" stuff. I think the ecryptfs stuff was an automatic part of the system install. I have never used it (nor do I know how to use it). I have no idea what the heck could possibly be going into that if I'm not even using the ecrypt/private stuff. Any ideas?

Also, I'm already down to 900M free... and it keeps getting lower. :(

edit2- I just rebooted the computer, the space was at 847M before, and it went up to 882M... and now, another check just a minute later, and it's down to 880M (I've opened no programs other than 1 web browser and a command line to check disk-free space). That's only a couple meg change in a minute or so, perhaps the result of loading the web browser again (if there was no cache factoring in). So maybe the reboot fixed whatever it was. However, I have no way of knowing what caused the HDD space decline before. And I'm still puzzled as to what can be done with that ".Private" stuff, how to unencrypt/access it, or if it's safe to just delete all of the contents in that directory (that seems to be where all of this problem is coming from).

edit3- the ".ecryptfs" directory is now up to 9.9G space used. ...but for the moment "/" is holding steady at 880M free. I just need to know if I can delete the ".Private" (ecryptfs) contents, which will help tremendously with this problem, or at least how to access it. It is within my currently logged in username, so I should theoretically have access to it now. I just don't know how. Anybody?

Thanks!

---

### Post by robgr85 on 2011-01-25
Don't know if it helps, but You can try to track the proceses using Your home directory:

```

lsof | grep home

```

That may help a bit in sloving the space puzzle game ;)

---

### Post by Th3Professor on 2011-03-18
...okay, problem with my HDD on / (and /home) being eaten up again.

I found one of the sources, though there are still more unknowns.

What I found:

**.xsession-errors.old**

That file, alone, was over 4 gigs. Crazy.

It's a text file, so I cat'd it to get a glance. There were a handful of "libdvd" but there seemed to be an infinite number of lines reading:

```
*** NSPlugin Viewer *** WARNING: (/build/buildd/nspluginwrapper-1.2.2/src/npw-viewer.c:1017):invoke_NPN_InvalidateRect: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
```

...and basically, just countless lines of "NSPlugin Viewer" warning/failed messages... enough to fill up a 4+ gig file.

I ran "tail" on the file and the darn NSPlugin error goes all the way to the end.

What's up with that?

Can anyone help with remedying that?

I'd like to *not* have to manually go in and do a "du" on the HDD, including hidden files, just to try to find the sneaky stuff that's eating up my space.

:confused:

---

### Post by louisgag on 2011-09-16
> **Th3Professor said:**
> ...

What I found:

**.xsession-errors.old**

:

Thanks for that hint, my .xsession-errors was taken 2.8 gig, guess we had the same problem.. I just deleted it right away.

Thanks!


-Louis

---

### Post by Th3Professor on 2011-09-18
I'm still having problems with HDD space running low, only now my xsession file is not the cause.

---

### Post by drs305 on 2011-09-18
I don't know what your specific problem is, especially if it's in a home folder called .Private. Normally lost disk space is caused by backups made on the Ubuntu partition rather than a backup one, undeleted trash (including root's) and large log files. But I don't know how these issues would relate to .Private.

In any case, perhaps you can use the commands or other techniques from this thread to help troubleshooting:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by pqwoerituytrueiwoq on 2011-09-18
have you checked /var/log for multi-gig files?

---

### Post by lolipop. on 2011-12-29
var/log definitely a problem!
1.Delete large Logs.
2.Disable all logging  through BootUp-Manager
(Due to some crazy frenzy of loging  of the system that might be having problems Handling or else...
3.Your Firewall might under constant Attack and Log like crazy -limit! or disable ...

4. Your .Private folder will hold the identical size in Gigs to your System  and Home folders
Due to Encryption when you chose to activated it and encrypt your system at the time of  installation ... of the System (for a while works fine then as a resoult - out of Space)...

Disable Loging - Will give you Pure size in gigs- no more eating!!!
Deleting the .Private folder wont Help - you give it all up for encryption of all your folders of system and Home... (Reinstall with no incryption-best for limited HD) 

Use Disk Usage Analyzer in Accessories to navigate to all your large (that includes hidden) folders -open folder - Delete through sudo nautilus dump the folder there in the terminal  - enter! 

                                                                                       Boom-Bam & Done.  

PS, also see to your root Trash Bin! There might be large stuff stored there ....
That is  sure thing - indefinitely.
                                                                                                 Cheerios

---

### Post by spillemw on 2012-01-03
I had the same problem that something is eating my disk space.  I recently installed Ubuntu server 10.04 and overnight my disk space grew from 15% used to 100% used.
Below a screen shot of df output AFTER I solved the situation (after much cursing).
As you can see the /dev/mapper/orion-root shows 6% now, where it showed 100% just a moment ago.  None of the other mounts showed anything more than what they show now.  However, I did have a lot of other mounts on remote filesystems and 2 USB disks, all mounted in the /mnt directory.
First thing i did was to unmount the remote samba disks (my NAS).  That did NOT help, but through the command "du" I did establish the /mnt directory was the culprit, in particular the USB disks.  Each USB disk is a 1 TB disk that I use to backup my filesystems.  For some reason, /dev/mapper/orion-root seemed to believe that the data on that USB disk was actually part of the 72 Gig hard disk of my server, so the 72 Gig of that disk were swallowed by /dev/mapper/orion-root.
I unplugged the USB disks.  For some reason that still was not the final thing to do as the mounted directories still showed the same disk space usage.  So without the USB disks plugged in, I had to rm the /mnt directories in which the USB disk had been mounted.
That immediately solved the issue.

I assume this is an LVM bug.  Can anyone tell me how i can possibly solve this?  I would prefer to use these cheap USB disks for backup again.



Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/orion-root
                      75945056   3774316  68312924   6% /
none                    508484       252    508232   1% /dev
none                    513088         0    513088   0% /dev/shm
none                    513088       360    512728   1% /var/run
none                    513088         0    513088   0% /var/lock
none                    513088         0    513088   0% /lib/init/rw
/dev/sda1               233191     31581    189169  15% /boot

---

### Post by drs305 on 2012-01-03
> **spillemw said:**
> For some reason, /dev/mapper/orion-root seemed to believe that the data on that USB disk was actually part of the 72 Gig hard disk of my server, so the 72 Gig of that disk were swallowed by /dev/mapper/orion-root.
I unplugged the USB disks.  For some reason that still was not the final thing to do as the mounted directories still showed the same disk space usage.  So without the USB disks plugged in, I had to rm the /mnt directories in which the USB disk had been mounted.
That immediately solved the issue.

I assume this is an LVM bug.  Can anyone tell me how i can possibly solve this?  I would prefer to use these cheap USB disks for backup again.


Are you sure data was not actually written to your system partition in the /mnt folder?  This can happen when backups are erroneously made when the backup partition isn't mounted. The backup is written to /mnt but without the backup partition being present the data is written directly to root's /mnt partition. Thus even when the USB device is removed the data remains on the system partition.

---

### Post by spillemw on 2012-01-03
Ouch.  That must have been it.

What is the smiley for "shamefaced" ?

---

### Post by drs305 on 2012-01-03
> **spillemw said:**
> Ouch.  That must have been it.

What is the smiley for "shamefaced" ?

Might be this one:

:oops:

But no worries - something like this has happened to all of us at some point. As far as making backups on /, it occurs often enough I wrote a thread about how to troubleshoot it.

Happy Ubuntu-ing !

You can mark this SOLVED via the 'Thread Tools' link at the top right of the first post if desired.

---

