---
title: "How to backup a previous partition from the LiveCD?"
date: 2011-10-16
forum: General Help
---

### Post by n0c0d3 on 2011-10-16
I've run into troubles after upgrading to Xubuntu 11.10 (Windows partition is not recognized and some network problem) and now I can't boot anymore. I've decided to just do a fresh install of Oneiric. But I need to make a backup of my home directory to an external HD first. I used ext2explore from my Win7 partition to copy the whole shebang, but there is 2 Gig missing and it's way too much work to find out what is missing. So I booted from the 11.10 LiveCD (Xubuntu) to see if I could make a copy from there, but I don't seem to have permission to write to my external HD from within the LiveCD. I can create files and folders though. Ï tried to change the permissions in the folder properties on the External drive to 'admin', but that immediately flips back to what is was before.
How can I make a backup and make sure I don't miss a single file, not even one hidden file and directory?

---

### Post by gsmanners on 2011-10-16
I would probably do it like this:

```
sudo -i
cd /media/bigdrive
mkdir data
chown 1000:1000 data
exit
cd /media/bigdrive/data
cp -r /home/jack .
```

(The above will only works with a drive formatted with EXT or XFS or something like that.)

---

### Post by n0c0d3 on 2011-10-16
gsmanners, thanks for your suggestion. The external drive is formatted in NTFS, so it wont work? I haven't tried yet. I'm about to go to sleep now, so I'll give it a try anyway tomorrow. It won't do any harm I suppose...

Edit:
I just realize it won't probably work because of the format of the permission change.

---

### Post by gsmanners on 2011-10-16
Somehow, I doubt that chown command will work right on an NTFS drive.

Okay, for NTFS, you might consider making a big archive of your files onto the external drive.

---

### Post by n0c0d3 on 2011-10-17
I was thinking of creating an archive, but probably that's gonna take an awful long time. I was also considering an extra ext partition on my external drive, but then I also need an extra partition on my computer drive to get xubuntu and gparted installed first and I then afterwards can fuse the old and new partitions, because I was thinking of increasing my Linux partition and swap partition anyway.

Well, thanks for the advice, I'll see later today what I'm gonna do, when I have the time...

---

### Post by n0c0d3 on 2011-10-17
I lready made full backup. It turned out to be even 2 Gig larger than I first thought. gParted turned out to be on the LiveCD, so I didn't need to create an extra partition on my computer HD. I made an ext partition on my external drive and by starting Thunar as root (gksu thunar) I could copy it all. No need for extra permission stuff. Maybe I could have done that already without creating the ext-partition as well.
Then I installed Xubuntu and it turned out there was a choice to ceate an upgrade wich keeps most of the system settings and installed software when possible. I can't remember that was possibble when I installed Linux from CD for the first  time(which was also the last until now). I did that and Xubuntu boots without problem now. Still need to re-install some stuff and not all repositories are working now, but most seems to be okay now.

Thanks for your help.

---

### Post by gsmanners on 2011-10-17
> **n0c0d3 said:**
> I made an ext partition on my external drive and by starting Thunar as root (gksu thunar) I could copy it all. No need for extra permission stuff.

You like living dangerously, huh? Well, kudos on your guts, but I don't recommend that method for anyone else. Copying files as root makes them owned by root on the other drive. Then, later (when you want to restore those files) you'll have to set the owner back to whatever it was before.

---

### Post by n0c0d3 on 2011-10-17
Thank for giving the trust to me ;) To be honest I didn't really think of possible security issues. So the risk was more more like ignorance. But I don't think there will be a great hazard. But now you mentioned it, I'm now aware I should change the permissions when I copy things to my home directory. 

Thanks!

---

