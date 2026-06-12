---
title: "Backup Home Symlink Destinations"
date: 2011-07-22
forum: General Help
---

### Post by robohippy on 2011-07-22
Hi,

Apologies if this is covered elsewhere, but I've not managed to find it.

I am setting up a dual boot Vista/Ubuntu on the same HDD and will replace my Home folders for photos, music etc. with symlinks to the corresponding Vista folders so they are all in one place and accessible from either system. 

I want to back up these common folders to a separate internal HDD. My question is, if I backup the Home folder will it just backup the symlink pointers, or would it backup the contents of the destination folders(which is what I want to achieve). If, as I suspect it is the former, how can I set it up to backup the actual contents?

Thanks for any help.

Robohippy

---

### Post by papibe on 2011-07-22
Are you going to run the backup on Vista or Ubuntu?

Regards.

---

### Post by vanadium on 2011-07-23
I guess the backup is going to be from Linux. It depends on the tool you use and its settings. For example, the cp or rsync commands can be told to follow symlinks (= copy their contents) or not (= just copy the small symlink file itself).

---

### Post by papibe on 2011-07-23
I have backed up ext4 disks to NTFS using rsync with no problem (well, you except permissions), but I've never used it from NTFS to NTFS.

I faced a similar situation last year. I played safe and backup my files from Vista. I would recommend taking a look at [SyncToy]("http://www.microsoft.com/download/en/details.aspx?id=15155"). It is a Microsoft graphical tool based on the idea of rsync (more like Unison actually). I didn't use the whole functionality, I just use it as backup tool by mirroring my Windows file to an external USB HD. It is free, BTW.

Just some thoughts,
Regards.

---

### Post by robohippy on 2011-07-23
> **papibe said:**
> Are you going to run the backup on Vista or Ubuntu?

Regards.
The backup will be from Ubuntu.

---

### Post by robohippy on 2011-07-23
> **vanadium said:**
> I guess the backup is going to be from Linux. It depends on the tool you use and its settings. For example, the cp or rsync commands can be told to follow symlinks (= copy their contents) or not (= just copy the small symlink file itself).
Thanks Vanadium, would you recommend a particular tool?

---

### Post by robohippy on 2011-07-23
> **papibe said:**
> I have backed up ext4 disks to NTFS using rsync with no problem (well, you except permissions), but I've never used it from NTFS to NTFS.

I faced a similar situation last year. I played safe and backup my files from Vista. I would recommend taking a look at [SyncToy]("http://www.microsoft.com/download/en/details.aspx?id=15155"). It is a Microsoft graphical tool based on the idea of rsync (more like Unison actually). I didn't use the whole functionality, I just use it as backup tool by mirroring my Windows file to an external USB HD. It is free, BTW.

Just some thoughts,
Regards.
Thanks Papibe, I'll bear that in mind but ideally I'd like to run the backup from Ubuntu. The reason being that Vista will be rarely used (and also because I like to play around with Linux) - It gives me a plan B, though.

---

### Post by vanadium on 2011-07-23
I use rsync with the -a option, which preserves links, file attributes, permissions, etc. (-a stands for "archive"). Yet I never backup my home folder, only the actual data folders inside them (e.g. Documents, Pictures, ...).

I guess that, to copy files from ntfs volumes, the options -rt would do. In this case, rsync will not preserve links, but copy their contents. The t option will cause rsync to preserve the original time stamp on the copy.

To create a "mirror" copy, i.e., have files you deleted automatically deleted in the backup as well, use the --delete option. Be very careful with that option, and only add it once you know your command is correct.

For example, to backup your Documents to a drive "Backup", the syntax would be
```

rsync -rt ~/Documents /media/Backup/

```
(note no trailing slash for Documents, but a trailing slash for the (existing) destination directory)

---

### Post by robohippy on 2011-07-23
> **vanadium said:**
> I use rsync with the -a option, which preserves links, file attributes, permissions, etc. (-a stands for "archive"). Yet I never backup my home folder, only the actual data folders inside them (e.g. Documents, Pictures, ...).

I guess that, to copy files from ntfs volumes, the options -rt would do. In this case, rsync will not preserve links, but copy their contents. The t option will cause rsync to preserve the original time stamp on the copy.

To create a "mirror" copy, i.e., have files you deleted automatically deleted in the backup as well, use the --delete option. Be very careful with that option, and only add it once you know your command is correct.

For example, to backup your Documents to a drive "Backup", the syntax would be
```

rsync -rt ~/Documents /media/Backup/

```(note no trailing slash for Documents, but a trailing slash for the (existing) destination directory)

Thanks Vanadium, I am intending to do same, backup some of the individual folders in home rather than all of home. I don't think I'll need the 'delete' option as it is will be photos, music etc. that just accumulates and won't be deleted. That is useful to know about, though. 

Ultimately I just want to have a physically separate backup of photos, music etc. to copy from if the main disc should ever fail - I'm not worried about preserving any system data or OS's as if I manage to screw them up if I get a bit over-enthusiastic when tinkering then I just clean install the latest version anyway.
Anyway, I shall attempt all that tonight and report back.

Thanks to everyone for  your responses.

---

### Post by vanadium on 2011-07-23
> **robohippy said:**
> I'm not worried about preserving any system data or OS's as if I manage to screw them up if I get a bit over-enthusiastic when tinkering then I just clean install the latest version anyway.

+1
That is exactly how I feel about backup.

Once you have a good command line, put it in a small script file.
* Create a directory "bin" in your home directory
* Create a text file "bkup" in that bin directory (gedit ~/bin/bkup) (obviously, you can use another name than bkup)
* Add
```

#!/bin/bash
rsync <your parameters>

```
and quit the editor.

* Make the text file executable: "chmod +x ~/bin/bkup"

Next time you will log in, Ubuntu will automatically include your personal bin directory in your search path. From that point, open a terminal and type "bkup" followed by enter to do your backup.

- The script can contain different lines for your different folders you want to backup.
- The first time, all data must be copied. On subsequent runs, only changed data are copied, making the backup very fast and quite effortless.

---

### Post by robohippy on 2012-01-28
Thanks everyone.....had to delay getting round to doing this - but all working nicely, thanks!

---

