---
title: "Lucid can't mount network drives at boot, freezes"
date: 2010-05-20
forum: General Help
---

### Post by mcosta1973 on 2010-05-20
I just upgraded my 9.10 mythbuntu machine to 10.04.  I have 3 network drives listed in fstab that previously had no issues at boot.  They wouldn't mount there since the upgrade from 9.04 to 9.10, but at least I could login to the system and manually mount them.  Now, no such luck.

I get as far in the boot process as attempting to mount all the drives in fstab and them am unable to do anything else.

mount error: could not resolve address for nas-02-58-EE: Name or service not found
No ip address specified and hostname not found
mountall: mount /var/lib/mythtv/videos/nas_videos [948] terminated with status 1

I get that error repeated with all 3 network drives and cannot get past it.  I get no option to skip attempting to mount those drives and load the OS.  It just halts there.

I've always thought it ridiculous that it would attempt to mount network drives before there is a network connection, but never expected it to halt the boot and make the system unusable.

Are there any workarounds to this problem?  I cannot get to a prompt to run any commands in the current state.

Edit:  I can boot by loading the liveCD, manually mounting the first drive and commenting out the network drive in /etc/fstab.  I tried adding the 'nobootwait' command to each drive, but it only lets me press 'S' to skip the first drive, then goes back to not letting me do anything.

contents of fstab below
> 
#//nas-02-58-EE/media   /var/lib/mythtv/videos/nas_videos       cifs   guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,nobootwait 0       0
#//nas-02-58-EE/media1  /var/lib/mythtv/videos/nas_videos1      cifs   guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,nobootwait 0       0
#//DiskStation/video    /var/lib/mythtv/videos/diskstation1     cifs   user,uid=mythtv,guid=users,rw,suid,credentials=/etc/cifspwd,nobootwait  0       0


Any ideas on how to get these drives to mount at boot without any user interaction/errors?

---

### Post by mcosta1973 on 2010-05-22
Submitted a bug report here:

[https://bugs.launchpad.net/ubuntu/+bug/584301](https://bugs.launchpad.net/ubuntu/+bug/584301)

---

