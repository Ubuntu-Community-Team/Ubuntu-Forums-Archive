---
title: "rsync wants to recopy all my files on next run and not sure why?"
date: 2010-03-15
forum: General Help
---

### Post by codeblue2k on 2010-03-15
So I just used rsync to backup about 400gb of data to my NAS. Look just over a day to complete, which is what I figured. I decided I should run rsync again to see how its going to handle comparing and only adding new files to the remote location. So I added a few new files and then ran the backup again. Well rsync is trying to do a complete copy of all of my original data, even though they have not changed. 

Is there a way that I can tell rsync to compare the two directories and only add the new files and delete the ones that are no longer in the original location?

Here is command that I am running:

```
sudo rsync -azvv --progress --stats /media/sda1/multimedia/movies /home/codeblue/NAS_Share_Point

```

---

### Post by solar george on 2010-03-15
how are you accessing your NAS? ssh or some other kind of share. Maybe you could install grsync to allow you to experiment with options from a GUI.

Why are you using -w? that will make the sync much less efficient because it transfers the whole files not just the bit which has changed.

---

### Post by codeblue2k on 2010-03-15
> **solar george said:**
> how are you accessing your NAS? ssh or some other kind of share. Maybe you could install grsync to allow you to experiment with options from a GUI.

Why are you using -w? that will make the sync much less efficient because it transfers the whole files not just the bit which has changed.

Thats not a "w" its two v's "vv"

I may have figured it out, does anyone see any issues with changing my command to:

> sudo rsync -atvv --ignore-existing --progress --stats /media/sda1/multimedia/movies /home/codeblue/NAS_Share_Point

I added the --ignore-existing argument

---

### Post by solar george on 2010-03-15
> Thats not a "w" its two v's "vv"
Urgh, bad font settings ftw.

> I added the --ignore-existing argument
Well that would prevent any changed files from being updated.

Again how are you accessing the NAS? What filesystem is the NAS using for its disks (as long as its not VFAT it doesn't matter actually)?

---

### Post by codeblue2k on 2010-03-15
> **solar george said:**
> Urgh, bad font settings ftw.


Well that would prevent any changed files from being updated.

Again how are you accessing the NAS? What filesystem is the NAS using for its disks (as long as its not VFAT it doesn't matter actually)?

Well the NAS is mounted locally and then I am rsyncing the data to the mount point. I would use SSH but its a Western Digital My World Book and it does not have SSH support nativity.

---

### Post by solar george on 2010-03-15
how about using the -c (always checksum) option incase it doesn't report file times correctly.

---

### Post by codeblue2k on 2010-03-15
Also anyone know anything about this error that im getting? The transfer seems to be working just fine, but I would still like to find out what the error is and how to remove it.

```
rsync: chown "<Directory>" failed: invalid argument (22)
```

---

### Post by solar george on 2010-03-15
thats a bit odd could you post the final command you're using

---

### Post by codeblue2k on 2010-03-15
> **solar george said:**
> how about using the -c (always checksum) option incase it doesn't report file times correctly.

Hmmm when I add -c to my command it sits at "sending incremental file list"

---

### Post by codeblue2k on 2010-03-15
My current command is:

```
sudo rsync -atcvv --ignore-existing --delete --omit-dir-times --progress --stats /media/sda1/multimedia/movies /home/codeblue/NAS_Share_Point

```

---

### Post by solar george on 2010-03-15
> **codeblue2k said:**
> Hmmm when I add -c to my command it sits at "sending incremental file list"

It will take a long time as it has to checksum everyfile - that avoids recopying unneeded files if there are inconsistancies in the modified time records of the files.

---

### Post by codeblue2k on 2010-03-15
I just realized a pattern, the folders that are throwing the chown Invalid Argument (22) error are ones that were created from my windows box. The ubuntu box is my file server and for right now my main pc is Windows 7.

But the items in the folder are still getting copied over as they should. They dont get an error, just the folder on the NAS. Any idea what would be causing that? Permissions?

---

### Post by solar george on 2010-03-15
maybe something to do with the fact that windows doesn't know about *nix file permissions.
Maybe try adding -X to the options (i'm not sure why i just vaguely remember somthing about win vista and later and extended file attributes.)

---

### Post by codeblue2k on 2010-03-15
> **solar george said:**
> maybe something to do with the fact that windows doesn't know about *nix file permissions.
Maybe try adding -X to the options (i'm not sure why i just vaguely remember somthing about win vista and later and extended file attributes.)

No luck... -X didnt help, i still get the same error

---

### Post by Seq on 2010-03-15
(Assuming you are using SMB/CIFS)

From a quick look, Windows previously used timestamps with less resolution than we typically have on Linux. According to `man rsync` this was a two-second resolution. It could be that as the timestamp goes through SMB/CIFS, it also gets clobbered, thus rsync will see different timestamps between local and remote.

```
       --modify-window
              When  comparing  two  timestamps, rsync treats the timestamps as
              being equal if they differ by no  more  than  the  modify-window
              value.   This  is  normally  0 (for an exact match), but you may
              find it useful to set this to a larger value in some situations.
              In  particular,  when  transferring to or from an MS Windows FAT
              filesystem (which represents times with a 2-second  resolution),
              --modify-window=1 is useful (allowing times to differ by up to 1
              second).
```

Regarding your chown issue, if you're copying as a regular user, you probably don't have permissions to change ownership.

---

### Post by codeblue2k on 2010-03-15
> **Seq said:**
> (Assuming you are using SMB/CIFS)

From a quick look, Windows previously used timestamps with less resolution than we typically have on Linux. According to `man rsync` this was a two-second resolution. It could be that as the timestamp goes through SMB/CIFS, it also gets clobbered, thus rsync will see different timestamps between local and remote.

```
       --modify-window
              When  comparing  two  timestamps, rsync treats the timestamps as
              being equal if they differ by no  more  than  the  modify-window
              value.   This  is  normally  0 (for an exact match), but you may
              find it useful to set this to a larger value in some situations.
              In  particular,  when  transferring to or from an MS Windows FAT
              filesystem (which represents times with a 2-second  resolution),
              --modify-window=1 is useful (allowing times to differ by up to 1
              second).
```

Regarding your chown issue, if you're copying as a regular user, you probably don't have permissions to change ownership.

Hmmmm... I am using SMB to transfer the files. I would use SSH if the NAS had support for it. And comparing the time stamps, they are completely different. The modified date on some are off by more then a month or two for some reason. Im totally confused as to whats going on. Why would a file that got coppied over to the NAS less then 2 days ago have a time stamp thats different?

The account that im using to map the NAS share to a local mount point is an admin on the NAS. So how would I take ownership? Is it even a big deal as long as the files are copying over, will it cause issues down the road?

---

### Post by codeblue2k on 2010-03-15
The date on my ubuntu server is the date that the file was originally created and the date on the NAS is the date the file was coppied over to my NAS. Could be as much as two months difference between the two. How do I keep them synced?

---

