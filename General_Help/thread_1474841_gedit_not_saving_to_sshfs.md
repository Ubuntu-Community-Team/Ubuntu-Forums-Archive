---
title: "gedit not saving to sshfs"
date: 2010-05-06
forum: General Help
---

### Post by jcoglan on 2010-05-06
I just updated to 10.04 from 9.10 and suddenly gedit is saying I don't have permission to save files in an sshfs-mounted directory. Nothing I've found through Google works.

* I'm mounting using `sshfs james@of1-dev-james:/home/james/projects $HOME/projects`

* `fuse` is listed in /etc/modules

* I'm a member of the `fuse` group

* Using `newgrp fuse` before mounting stops gedit from seeing the mounted directory at all.

* /dev/fuse belongs to `root:fuse` and has `crw-rw-rw-` permission.

* Other apps e.g. `nano` have no problem reading/writing to this directory.

I'm all out of luck on Google, anyone got any other ideas?

---

### Post by jcoglan on 2010-05-06
One more thing: gedit has auto-save/backup switched off, but is managing to write files called things like `.goutputstream-5U5PCV` to the mounted directory when I try to save. Seems the permission error must crop up after writing these, as they contain the text I'm trying to write -- they don't replace the file I'm actually editing.

---

### Post by longanduselessname on 2010-05-06
What sort of permissions are listed on the mounted files?

"ls -l" in $home/projects will give you the permissions.

That ".goutputstream" is a pretty weird file.

---

### Post by dcstar on 2010-05-07
Names that contain a leading "." are illegal on NTFS filesystems.

If gedit is disobeying the "No backups" setting then you will get this sort of problem.

---

### Post by jap1968 on 2010-05-11
I am experiencing this same problem since I updated to 10.04 beta, about one month ago.

I opened a bug in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/557150](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/557150)

but I think that the description provided here is more precise (i.e. that seems not to be a bug in sshfs but in some gnome-related piece of software).

---

### Post by m0ns00n on 2010-06-17
This is really annoying for me and my collagues. Is there any sign of a fix yet? I can save now with having the backup option enabled, but I really hate having tilde files laying around in every folder.. I don't need these backups and I'd rather not have to make a "deleteBackupfiles.sh" run every time I'm done.

---

### Post by jap1968 on 2010-07-02
Some user found the origin of the problem.
It is a bug in the creation of backup files in gedit.
More information: [http://ubuntuforums.org/showpost.php?p=9248113&postcount=4](http://ubuntuforums.org/showpost.php?p=9248113&postcount=4)

Not a real solution, but at least I can use gedit to edit my remote files.

---

