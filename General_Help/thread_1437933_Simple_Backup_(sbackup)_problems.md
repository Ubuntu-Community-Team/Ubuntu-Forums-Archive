---
title: "Simple Backup (sbackup) problems"
date: 2010-03-24
forum: General Help
---

### Post by LinuxTAd on 2010-03-24
Hello,

 I have run into some snags in my chosen backup solution, namely Simple Backup.

1) Evidently the backup size has grown too large(20 gigs)although no warnings are provided. While I can backup the data, I am unable to "load" them in the Simple Backup Restore process across a network on a Samba share.

2) If backing up multiple machines, it identifies the incorrect machine as the "base".

3) I attempted to load one of the backups files.tgz to see about obtaining files from it. And at the end I received an unexpected end of archive. Hence the testing began...

Thinking that something must be amiss, I completely removed the application (yes and conf files) and reinstalled it. I was still unable to load the back ups. I mean they would not even populate the list. Checked everything, permissions, folder targets, etc. still no love.

 I then created a new folder and created a brand new full backup. After it was completed I again attempted to load the backup to simulate a restore. I was shocked, it refused to load the backup. The new backup does not populate the list.

I then run it in terminal to see if it is providing any errors
sudo simple-restore-gnome nothing shows up. Just the simple statement in the restore window stating 

"Error: no backups found in the target directory"

 Complete removal reboot and then a reinstall. But at this point I am getting a bit peeved.

 I then went through and added some folders containing large amounts of data, in the "excluded list" and performed another backup. The backup this time was 11.9 Gigs in size. 

 I open the restore portion of the application and to my surprise, the backup finally loads but at this point I have lost all faith in it. Evidently there is some magical size limit to the size of a backup with no warnings provided or error messages...

 Has anyone else seen this behavior? Can anyone else provide confirmation on this behavior?

Thank you,
Tom

---

### Post by LinuxTAd on 2010-03-26
I have been working on alternatives to this. I had Rsync ready to go, however it will not work. The target drive is on a windows based server with of course NTFS drives. rsync errors trying to copy symlinks to ntfs drives.

> rsync: symlink "target ->  source" failed: Operation not supported (95)


Back to tar! ;)

And my new bash script is completed. :)

---

