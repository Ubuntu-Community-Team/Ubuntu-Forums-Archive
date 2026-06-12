---
title: "move data from old drive to new drive"
date: 2009-10-16
forum: General Help
---

### Post by pikkiem on 2009-10-16
hi. i have added a new drive as per previous discussions in this forum and named it mynewdrive under /media. it is formatted with ext3 fs. now i need to move all data on the srv/samba/share (that is on the older smaller drive) to the new bigger drive as well as all the /home directories for all the users (3). Without losing any data how will i do this and secondly, how will the network users see this new share. Does the smb.conf file needed to be changed? All i want is that the users still see the srv/samba/share when it is on the new drive. Can someone help me or point me in the correct direction please. I am still new to ubuntu.

hi. is this the right place for this question as no one seems interested in even reading this?

---

### Post by P4man on 2009-10-16
IM slightly confused. You access your home partitions over a network, is that right?

If so (and I guess, either way), if you copy the folders from the old to the new drive, and then adjust the share, nothing would change for the clients afaics. Except for permissions and ownership perhaps, but then again, Im not entirely sure how that works over a network, so i'll refrain from giving possibly bad advice.

---

### Post by StuartN on 2009-10-16
> **pikkiem said:**
> Without losing any data how will i do this and secondly

Is there any reason why you mount the new drive at /media/mynewdrive and not at /srv? If you mount it there (after renaming the old /srv to /srv_backup or some such) then you will not need to alter any configurations.

You can copy the data Using Nautilus, or cp in the terminal (cp -R /srv /media/mynewdrive), or rsync / Grsync. A second run of rsync should copy nothing if the first copy is correct (use rsync --verbose -itemize-changes --dry-run to check what would be copied, without actually copying)

Whichever method you use to copy, it would be wise to check the copy before remounting /media/mynewdrive as /srv - personally, I would install Krusader and use that to copy the directory and check the copy (using the Synchronise option).

---

### Post by Baelus on 2009-10-16
You can use rsync to copy the files:

```
rsync -avuhP -n /srv/samba/share/ /media/mynewdrive/
```

The switches do this:

a  archives the files, basically preserving permissions, owner, modification times etc.

v  for verbose gives you more feedback on what's going on.

u  is for update. It will skip files that are newer on the receiving end. Good if rsync gets interrupted and you have to resume.

h  will show file sizes in human readable format i.e. kilobytes, megabytes etc.

P  gives you a progress bar.

n  will perform a "dry run". It will show you what it will do without actually going through with the operation. Let's you make sure it'll do what you want it to do.

Then it's just the source followed by the destination.

You may want to run it with *sudo* so that it has access to all the files.

---

### Post by Chad5ter on 2009-10-16
Wow Baelus! I really appreciate the way you're explaining. I'm still new too on Ubuntu, but I can tell you when someone take time to reply and give more information possible and you did my friend. I don't need to copy anything at the moment, but if i need too, I'll keep this post in mind!

Cheers!

Chad5ter
Québec-~

---

### Post by Baelus on 2009-10-16
No problem. :)

---

