---
title: "Rsync not Deleting"
date: 2012-02-28
forum: General Help
---

### Post by Quarkrad on 2012-02-28
Newbie running 10.10.  I have  a script in init.d and GAdmin-Rsync set up so that when I shut my pc off I backup my **Home** folder and another folder on a different partition to a second HD in my pc called **backup** (the **backup** partition is formatted as ntfs).  This works very well - I am completely happy as my key data is backed up automatically.  My issue is that in GAdmin-Rsync there is a tick box that offers 'Delete destination files that does not exist in source' - when I tick this box and run GAdmin-Rsync manually (I normally do not have this box ticked) the remote backup HD shows files that do not exist on my source HD (because I have deleted them). So, if in the morning I clear out some files in **Home** and then run GAdmin-Rsync manually in the afternoon with the 'Delete destination files' option ticked the files are not in **Home** but are in **backup**.  I believe I have the right permissions set up - attached permissions of **backup**.

---

### Post by Quarkrad on 2012-02-28
Of dear - very sorry.  Been at this for ages!!!!   in GAdmin-Rsync there is a button called Save backup.  Yes - I didn't press this, still learning about Rsync.

---

