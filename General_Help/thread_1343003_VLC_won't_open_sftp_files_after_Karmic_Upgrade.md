---
title: "VLC won't open sftp files after Karmic Upgrade"
date: 2009-12-01
forum: General Help
---

### Post by KyleBrandt on 2009-12-01
After upgrading to karmic, when I try to open a file from another computer via sftp://... in nautlius, it no longer works.

I get "VLC is unable to open the MRL ... sftp://kbrandt@...."

Anyone know why this might be? When I copy the file to the local HD it plays fine.

---

### Post by shutdown -h now on 2010-02-16
I did a fresh Kububtu 9.10 install and I've got the same problem, even with smb://.

---

### Post by neon401 on 2011-02-23
I know it's an old thread, but I'm having the exact same problem, running Ubuntu 10.10.

---

### Post by Pithikos on 2012-04-06
Same problem here on my Lubuntu which is based on Ubuntu Oneiric.
I can't stream video files via sftp on VLC but I can with other movie players like Dragon Player.

---

### Post by Pithikos on 2012-11-27
The problem seems to be with the sftp folders not mounting in ```
~/.gvfs
```. A solution is to make the folder manually if not there and try mount it. Some help can be found here: [http://askubuntu.com/questions/61196/why-do-my-gvfs-mounts-not-show-up-under-gvfs](http://askubuntu.com/questions/61196/why-do-my-gvfs-mounts-not-show-up-under-gvfs)

---

