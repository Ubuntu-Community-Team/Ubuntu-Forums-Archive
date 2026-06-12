---
title: "Automounting remote drives to back up to"
date: 2010-04-17
forum: General Help
---

### Post by nowhere@cox.net on 2010-04-17
Hey everyone,

What's the current best practice for automounting a remote drive for automated backup? I want to use Back in Time and maintain snapshots but it can't do that remotely so I have to mount a folder outside of Back in Time. 

I have used sshfs from this howto in the past and it works mostly but seems to lose connection and not reconnect a lot.
[http://ubuntuforums.org/showthread.php?t=430312]("http://ubuntuforums.org/showthread.php?t=430312")
Is there a more "modern" way? NFS is horribly unreliable and dog slow for me so it's OUT unless it's changed in the last year. 

Thanks!

---

### Post by RudolfMDLT on 2010-04-17
Hi there,

I wrote this bash script, changed the user privileges to be able to run it, and then setup a cron job to run this script every half an hour. 

> #!/bin/bash
echo This will now sync your Documents folder using rsync
#STR_FOLDER_SRC=/homer/rudolf/Documents/
#STR_FOLDER_DEST=/backupfolder/
[B]fusermount -u /backupfolders/Documents/
sshfs root@192.168.10.250:/backupdrive1/Rudolf/incremential/DocsSync/ /backupfolders/Documents/ -p 2233
rsync -ruve ssh --delete /home/rudolf/Documents/ /backupfolders/Documents/[/B]



The hashed out variables where used in a slightly more complex script, but you can ignore them if you are new to scripting.*192.168.10.250* is a local linux desktop. Read up on some cron basics, there are even GUI's available to configure it and you'll make life much easier for yourself.

This script basically maps a folder locally and then runs rsync. You can run your program if you wish.

Regards,

Rudolf

PS: I know you have used sshfs, but as far as dropping connections are concerned, I've never encountered this. Might be a network problem? run this command for about 20 minutes or so, ping -s 2048 *ServerIP* >> ./ping.txt , it'll ping your server with very large packets, just check the reliability of the link. You can get the results in your home folder under ping.txt.

---

