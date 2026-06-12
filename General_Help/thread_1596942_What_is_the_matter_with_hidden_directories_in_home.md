---
title: "What is the matter with hidden directories in /home?"
date: 2010-10-14
forum: General Help
---

### Post by Asmodai on 2010-10-14
For example, I tried downloading files using JDownloader. It drops the downloads to ~/.jdownloader/downloads by default.
The downloads finished successfully (or so it seemed), however no files appear in that directory and the free space doesn't go down either.
When I check which files the process has opened during download (using System Monitor), I always see an entry such as ~/.jdownloader/downloads/my.file (deleted).
When changing the directory to ~/Downloads, everything works as expected.

Similarly, last week, I tried to share a profile folder in ~/.thunderbird. However, on other machines, I was always prompted for a password even though I enabled guest access.
After messing around with the file permissions for half an hour I gave up and tried copying the profile folder to another location. Sharing that one worked perfectly fine like it normally does.

So it seems there is something unusual about hidden directories.
What is the reason, though?

---

### Post by Asmodai on 2010-10-16
Bump.

---

### Post by dcstar on 2010-10-16
> **Asmodai said:**
> For example, I tried downloading files using JDownloader. It drops the downloads to ~/.jdownloader/downloads by default.
........
So it seems there is something unusual about hidden directories.
What is the reason, though?

Sometimes people do silly things like putting /home folders on non-Linux filesystems which do not support names beginning with ".".

---

### Post by Asmodai on 2010-10-16
Well, I dunno. My /home partition is formatted with ext4, so there should be no problem with that, right?

---

### Post by dcstar on 2010-10-16
> **Asmodai said:**
> Well, I dunno. My /home partition is formatted with ext4, so there should be no problem with that, right?

Should be ok, but sharing may not work as the Samba protocol (used for sharing) may not support the "." as it is a Windows protocol.

---

### Post by James78 on 2010-10-17
Well, all I know is that I use Samba for my Ubuntu server, and . folders/files are hidden by default, but I can access them normally if I know the paths (which of course I do)

---

### Post by CharlesA on 2010-10-17
> **James78 said:**
> Well, all I know is that I use Samba for my Ubuntu server, and . folders/files are hidden by default, but I can access them normally if I know the paths (which of course I do)

I've noticed this as well. Anything starting with a "." is hidden even when browsing the Samba share from Windows.

If you know the path, you can get into that folder tho.

---

