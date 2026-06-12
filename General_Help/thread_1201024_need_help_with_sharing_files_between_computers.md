---
title: "need help with sharing files between computers"
date: 2009-06-30
forum: General Help
---

### Post by zzero on 2009-06-30
hello everybody

     i have an old pc that i have converted into a server(installed ubuntu server),my desktop PC  has ubuntu 9.04 running on it.i have networked both the comps using samba. i plan to store all my files on the server especially media files.now some of te problems that i am facing are

1)cant open the music files in most of the music players(fixed this problem by using DAAP server).is there any player that can play songs that are on a remote location? 
2)i cant use any of the tag editors fix missing tags.
is there any way to fix this problem?

---

### Post by t4thfavor on 2009-06-30
Sounds like samba permissions, I would start there.

---

### Post by zzero on 2009-06-30
> **t4thfavor said:**
> Sounds like samba permissions, I would start there.

don't think so i have done [COLOR=Black]chmod 0777 to the share files.
what i am trying to say is that when i try to add files to the play list i see only local folders and not remote folders[/COLOR]

---

### Post by t4thfavor on 2009-06-30
OK so you need to click on Places -> Connect to Server Select Windows Share, and then add bookmark. then you can add songs from the network to your players. Thing is that you didn't have the share mounted, and ubuntu won't just go look for them you must point it in the correct direction.

If that doesn't work break out your windows box and try visiting \\yourserverip in an explorer window to see what you get.

---

### Post by zzero on 2009-06-30
so what you are saying is that i need to mount the samba share on my desktop?

i tried this command 

mount -t smbfs -o username=U_name,password=P_word //blackwater/MyFiles /home/zero/mount/ 

got the following error

mount: wrong fs type, bad option, bad superblock on //blackwater/MyFiles,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by zzero on 2009-06-30
damm feel like a dodo forgot to install smbfs. now that i have mounted the samba share on my home folder it ,works fine. now i want to auto mount  i want to add the following command :

 //blackwater/MyFiles /home/zero/mount/ smbfs username=U-name,password=P-word 0 2



also can anyone explain me what 0 and 2 does?

---

### Post by Iowan on 2009-06-30
Before you get too involved with that setup...
**smbfs** has been deprecated in favor of **cifs**. [Here]("http://ubuntuforums.org/showthread.php?t=288534") is a helpful (but lengthy) How-To on setting up cifs shares.

I should mention that the smbfs package you installed was not wasted - it uses cifs.

---

### Post by ronaldprettyman on 2009-06-30
If your trying to share media, why not do your transport to the server though NFS and streaming from the server using a web application like ampache.

In apt
nfs-user-server
ampache

Windows XP and Vista support NFS as well, though in Vista I think its only business and above, not home or home premium. NFS is much stronger then samba or windows sharing in my opinion. I've had better luck with NFS then samba and better speeds.

---

### Post by bodhi.zazen on 2009-06-30
NFS is faster. IMO samba is more secure.

---

### Post by 3rdalbum on 2009-06-30
There is a known problem with Rhythmbox - it can't access Samba shares that have been mounted by Gnome. *sigh*

I use DAAP for this now - I run Rhythmbox on the server and whenever I want to play music, I run Rhythmbox on my desktop.

What tag editors have you tried using? I'm sure I've used Easytag to update tags on my Samba share, even when mounted by Gnome.

---

### Post by t4thfavor on 2009-06-30
Note: If you use the connec to server dialog it would have told you that smbfs was not instaled :)

Don't worry, I've done that before as well.

I would 2nd, or 3rd or whatever the NFS over samba as well. I still use samba because My wife doesn't know how to connect to the NFS share.

---

