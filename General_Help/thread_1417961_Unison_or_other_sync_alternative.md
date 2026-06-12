---
title: "Unison or other sync alternative"
date: 2010-02-28
forum: General Help
---

### Post by WA1DH on 2010-02-28
I've used Linux (slackware, suse, mandrake, ubuntu) on and off over the past few years, and just recently I decided to migrate my IBM T40 Thinkpad over to ubuntu from Windows XP. When I used XP on the T40, I synced several folders to my other desktop PC (also running XP) using Windows Livesync. But, now that I have ubuntu on the T40, I need a new sync alternative that will work with windows on the remote (desktop) PC.

I shared the folders I want to sync from the Windows PC, and I can view them in ubuntu (via samba). However, if I try to sync to one of the folders from the Windows PC using the samba smb: path, Unison crashes and says smb: is an unrecognized protocol. I understand there is a way to make this work with SSH, but I haven't a clue how to get that to work.

Is there a simpler alternative to making unison read the smb: protocol, or otherwise mounting the Windows shared folders in ubuntu? Or, is there another sync program which can accomplish what I'm trying to do.

Thanks.

---

### Post by paxmark1 on 2010-02-28
for fat32 in your .prf (found in ~/.unison)  you probably want

perms=0 
owner=false

example
nano LEXLUTHER

root = /home/pa/Briefcase/
root = /media/Lexar/Briefcase
owner=false
perms=0

for going to a dlink 323 NAS with ext2   going from an external hdd in ext3

nano mp3a2.prf

root = /media/linuxbackup_/mp3
root = ssh://root@192.168.1.199//mnt/HD_a2/mp3

sshfs needed for machines.  And you need unison installed on both computers.


If you are always sending changes only in one direction, you can use rsync or grsync

peace mark

---

### Post by WA1DH on 2010-02-28
Ok, thanks for the info. I now have Unison installed on both machines (Ubuntu and Windows), and I installed sshfs on Ubuntu and added myself under the fuse usergroup. Apparently I also need an SSH client on the Windows PC, so I installed PuTTY. But, if I try to connect to the IP of the ubuntu PC from PuTTY, I get a 'Connection Refused' error. If I try to connect to the Windows PC from Ubuntu (via Unison using SSH), I immediately get 'Fatal Error: Lost connection with server'.

I also tried running Unison from the Windows PC and directing it to connect to the IP of the ubuntu PC, but I get the error 'Fatal error: Uncaught exception Unix.Unix_error(20, "create_process", "ssh")

Also, as I try to troubleshoot this - where is the typical install directory for Unison (where the .prf files are)? I tried to search for it but it looks like I'm only finding the compressed install packages.

---

### Post by dcstar on 2010-02-28
> **WA1DH said:**
> 
..........
Also, as I try to troubleshoot this - where is the typical install directory for Unison (where the .prf files are)? I tried to search for it but it looks like I'm only finding the compressed install packages.

```
~.unison
```

---

### Post by jingaling on 2010-07-24
I encountered the problem as we use livesync in work but I prefer Ubuntu. What I do is this:

My work machine runs 24/7 this has a VirtualBox VM running an extremely light version of XP. On the VM I have livesync and dropbox, on my ubuntu machine I have Dropbox only. Both dropbox and livesync sync the same folders in my VM so I can jsut leave it running in the system tray and when I update a file in dropbox ubuntu it then in turn updates on windows which update live sync - hey presto ubuntu > windows live sync intergration.

Hope this helps.

Jing

---

