---
title: "Is it safe to clean out the temp. folder?"
date: 2012-07-13
forum: General Help
---

### Post by patriot56 on 2012-07-13
My problem is that I have a very small HDD in an old IBM computer and need to free up some space.
This machine is primarily used as a media station however, it does serve other functions that require more space than I currently have on the / partition.  At this time I am not in a position to afford another HDD.  (That is planned for the beginning of next year).

The HDD is an older (but rarely used) 40 gig. drive and I have it divided into **5** separate partitions with a Swap area as follows:

**sda1=** Backup - 7.9 gig.'s
**sda2**= Media-Movies - 20 gig.'s
**sda4**= Extended - 12 gig.'s (a container for Logical Partitions)
**sda5**= ~./ - 11 gig.'s (as indicated, this is the ( ~/ ) partition).
**sda6**= Swap Space - 1.6 gig.'s

I realize that this is probably not the most efficient way to divide the drive but, understand that it has been a work in progress and wasn't necessarily planned this way at the beginning.

*Is it safe to remove the contents of the temp. folder?  Are there any other ways to gain more real-estate on the / partition?*

Any help is greatly appreciated.

Thank you in advance.

---

### Post by Cheesemill on 2012-07-13
The contents of /tmp are deleted every time that you reboot.

I wouldn't just start randomly deleting files from the temp folder because they may be in use by currently running applications.

---

### Post by patriot56 on 2012-07-13
@Cheesemill
Thank you for your response.  I was suspicious that, that was the case and as such I thought it wise to ask before randomly deleting things.
Now I'm glad I did.  :o)

Thank you again for the advise.

---

### Post by Tamlynmac on 2012-07-13
> patriot56

It's been my experience that you can delete the files in the "temp"  folder.  I'm assuming that your talking about the temp files in the  "file system". Make sure you view hidden files and reboot or at least  logout/login after deleting. Unfortunately, a number of these files will  be rewritten. However, if you have a bunch of internet files or  unnecessary files stored in temp, it will clean them up. Especially, if you don't reboot or shut your system down very often. As Cheesemill indicted many of the unnecessary files should clear on boot.

One suggestion I'd make, is to purchase a small drive (don't know if  your system will support a digital drive) to run just Ubuntu and then  use your petitioned drive for storage. You can even buy a used drive, if  it's in good condition.

That new drive would then be dedicated to actually running Ubuntu and it  will help with upgrading or if you have a problem with the drive.  Should an upgrade have problems, you wouldn't need to worry about your  stored data. Also makes backing up data much simpler. All our desktop systems use a dedicated drive to run Ubuntu and a  separate drive for data storage. I've never been a big fan of over  petitioning drives. I've just experienced to many problems in the past  with petitioned drives.

IMHO it's never a good idea to keep your backup on the same drive as your data. Since it's only 7.9 gig, you could get an 8 gig stick and free up an additional 7.9 gig's of space on your HDD. Maintaining your backup on the stick and even adding additional sticks (usb dependent) as needed. This assures that an HDD failure won't result in loosing your backup data.

Good Luck

---

### Post by Cheesemill on 2012-07-13
> **Tamlynmac said:**
> It's been my experience that you can delete the files in the "temp"  folder.  I'm assuming that your talking about the temp files in the  "file system". Make sure you view hidden files and reboot or at least  logout/login after deleting.
If you are talking about the files in /tmp then there is no point in deleting them  just before you reboot. As I stated above *all* files in /tmp are deleted every time that you reboot.

If there are specific files that you are worried about then you can determine which application they belong to using lsof (**l**i**s**t **o**pen **f**iles).
```
root@precise:~# lsof | grep /tmp
Xorg      1112       root    3u     unix 0xffff88021266a3c0         0t0       7956 /tmp/.X11-unix/X0
gnome-key 1899        rob    5u     unix 0xffff8801f5cd8000         0t0      16444 /tmp/keyring-Y9pLnL/control
gnome-key 1899        rob    6u     unix 0xffff8801f5c1db00         0t0      12744 /tmp/keyring-Y9pLnL/pkcs11
gnome-key 1899        rob    7u     unix 0xffff8801f5d9eb40         0t0      15513 /tmp/keyring-Y9pLnL/gpg
gnome-key 1899        rob   13u     unix 0xffff8801f5d9f500         0t0      15540 /tmp/keyring-Y9pLnL/pkcs11
gnome-key 1899        rob   14u     unix 0xffff8801f5d9db00         0t0      12826 /tmp/keyring-Y9pLnL/pkcs11
gnome-key 1899        rob   15u     unix 0xffff8801f5d9f1c0         0t0      15539 /tmp/keyring-Y9pLnL/ssh
gnome-key 1899        rob   16u     unix 0xffff880180226b40         0t0     220217 /tmp/keyring-Y9pLnL/pkcs11
gnome-ses 1910        rob   12u     unix 0xffff8801f5d9e4c0         0t0      15482 /tmp/.ICE-unix/1910
ssh-agent 1945        rob    3u     unix 0xffff8801f5c196c0         0t0      10713 /tmp/ssh-lJheccuG1910/agent.1910
pulseaudi 1997        rob  DEL       REG                8,2                1972030 /tmp/orcexec.1NeZ36
VBoxXPCOM 2137        rob    7wW     REG                8,2           5    1972034 /tmp/.vbox-rob-ipc/lock
VBoxXPCOM 2137        rob    8u     unix 0xffff880203db5b00         0t0      16237 /tmp/.vbox-rob-ipc/ipcd
VBoxXPCOM 2137        rob   10u     unix 0xffff8801871b8340         0t0      13145 /tmp/.vbox-rob-ipc/ipcd
VBoxXPCOM 2137        rob   11u     unix 0xffff880180220680         0t0      24042 /tmp/.vbox-rob-ipc/ipcd
ubuntuone 2210        rob   18u      REG                8,2           0    1969730 /tmp/tmpQ5DCg0
gnome-ter 3015        rob   18r      REG                8,2         224    1972036 /tmp/vteMIHGHW (deleted)
gnome-ter 3015        rob   19u      REG                8,2     1012566    1973406 /tmp/vteMMHGHW (deleted)
gnome-ter 3015        rob   20r      REG                8,2      206192    1973407 /tmp/vte0LHGHW (deleted)
gnome-ter 3015        rob   21r      REG                8,2         510    1973408 /tmp/vteRBSRHW (deleted)
gnome-ter 3015        rob   22u      REG                8,2          48    1973409 /tmp/vteXDSRHW (deleted)
```

---

### Post by Tamlynmac on 2012-07-13
> Cheesemill
As I stated above *all* files in /tmp are deleted every time that you reboot.

Not  just on reboot, but also on logout/login and shut down. Not sure about  12.04, but historically one could retain the temp files on shut down,  reboot or logout. I certainly don't wish to discuss that in this thread,  as the OP didn't ask for that info.

I did agree with you and pointed it out in my post, which you choose to ignore:
> As Cheesemill indicted many of the unnecessary files should clear on boot.

IMHO it's foolish to argue over a question of temp files, when the OP  really needs to consider alternatives that might actually have a more  significant effect on increasing their storage capabilities. Unless,  they don't reboot, shut down or login/logout often. I don't think it  matters which files the OP identifies as system temp files, if the  result doesn't really increase their storage capabilities. As temp files  may continuously be added to the temp folder.

Logic might suggest we offer up alternative solutions that the OP might consider reasonable and would meet their needs.

Just my $0.02

---

### Post by patriot56 on 2012-07-13
My thanks to **Cheesemill** and **Tamlynmac** for your  advice.  The suggestions that you both offered is greatly appreciated.    As I am still learning Linux this kind of information is very valuable  to me. 
As stated earlier in my response to Cheesemill, I was sure that the  contents of the temp. file was emptied upon reboot or log out/log in but  I wasn't sure.  (I thought I had read that somewhere).

Thank you **Cheesemill** for the information regarding the code;  lsof (**l**i**s**t **o**pen **f**iles).  I didn't know about that code and now that I do I assure you I will be using it, a lot. 


> **Tamlynmac said:**
> 

One suggestion I'd make, is to purchase a small drive (don't know if  your system will support a digital drive) to run just Ubuntu and then  use your petitioned drive for storage. You can even buy a used drive, if  it's in good condition.



This is a nugget of excellent advice.  Thank you.  Since, I have been the victim of my own ignorance more times than I care to remember.  Neglecting to backup my data and loosing it all when the drive failed (as they all do at some point).
I have an 8 gig. USB stick that I can use to backup to. 
This raises a question though; I know I don't have to tell you that this USB drive will fill up very quickly if I backup on a regular basis, ie., once a week or even once a month.
Is there a utility or something that will remove or at least archive the previous backup prior to starting the latest backup?

Also, if I choose to use the 8 gig. USB drive to run the OS from and give the 40 gig. HDD over to all data, will Ubuntu 11.10 run happily on that 8 gig. stick?

Your thoughts/advice on this is very appreciated.

Once again, thank you both for your help.

---

### Post by Tamlynmac on 2012-07-14
> patriot56Personally, I wouldn't use a stick on an older system to run the OS. As you'd be limited to your usb speed and throughput.

Right now your drive is petitioned to store 7.9 gigs of backup, unless  your including the media movies. If you are considering increasing the  volume of backed up data. Then it might make sense to consider an  alternative such as a external or internal HDD. They're fairly  inexpensive and available. Any device can fail, the only question is  when. :wink:

You can selectively backup only new data, which would not only speed up  the backup process, but minimize the volume of data for each backup. You  may wish to read [this]("https://help.ubuntu.com/community/BackupYourSystem")  and determine the most comprehensive backup solution for your purposes.  That page also has numerous links that might interest you. The volume  of data to backup is best determined by what you can afford to loose and  how much you can afford to store. I have no idea how much data you  backing up now or how much you intend to back up in the future.

Since the drive is fairly old, it might make sense to consider setting  your system up so that a failure of the drive would have minimal effect.  While at the same time minimizing out of pocket cost. Which is why I  suggested a small HDD for running the OS and using your existing HDD for  data storage. Then chose which data is necessary to backup to an  external device.

---

### Post by patriot56 on 2012-07-15
**Tamlynmac**
Thank you for the advice and input.  I will look at the information you provided through the link you suggested and make a decision from there.
Everything that you said makes perfect sense, as I am planning to replace this machine  with a new one right after the first of the year.  
The Movie-Media partition of the drive is simply a temporary landing zone for media files; a sort of "staging area" if you will, to hold files until I can move them to CD/DVD's.

As I said, I will review the information that you suggested and go from there.
I will mark this thread [SOLVED] at this time, as I think I have some thinking/planning to do.

Thanks again mate.
Your help is respectfully appreciated.

This is why love this Forum. :D

---

