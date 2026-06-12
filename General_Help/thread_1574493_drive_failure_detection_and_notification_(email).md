---
title: "drive failure detection and notification (email)"
date: 2010-09-14
forum: General Help
---

### Post by davidstoll on 2010-09-14
I recently had a backup hard drive fail and didn't realize it my main drive filled up.

drive 1: /
drive 2: /data
drive 3: /backup

/ is the os and gets backed up to /data on a weekly basis.  /data gets backed up to /backup on a monthly basis.

My /backup drive failed, so my rsync created a /backup folder which filled up my small / os drive.  This has since been fixed.  If it doesn't detect a "lost+found" folder, it doesn't rsync.

Now for my question...How can I send myself a message (email) to notify me that a drive has gone bad, isn't mounting, or maybe just detect that the "lost+found" is not present (meaning the drive isn't mounted), or maybe parse a "df -h" and report my findings depending on the output.

At the end of the day is there a shell script that can email me when a drive fails?  I can use perl, but would prefer to not use it if I can do it with normal shell commands in a script.

Thanks so much!

---

