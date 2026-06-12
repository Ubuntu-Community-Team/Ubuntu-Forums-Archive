---
title: "Samba &lt;-&gt; Windows LFS Issue"
date: 2011-11-13
forum: General Help
---

### Post by Hazey11 on 2011-11-13
Hey everyone,     
    I have a samba server setup on my ubuntu 10.04 blade and it's had no problems - until now. I'm using all windows 7 boxes to access the samba shares via network, it initially hangs when I first attempt to browse the folder (from windows box) but thats not my issue - the issue is I've discovered there is no large file support apparently.

   It all started when I attempted to copy over my truecrypt 15gb file container to the samba share, it would not go. So I said screw it and transferred via FTP no problem, then i go to MOUNT that truecrypt container on the samba server from my windows box and it just doesnt go (does not recognize it as a truecrypt container). 

   This appears to be a lack of LFS as it occurs with all large files, I've searched around and all I can find is a solution using a linux client by adding the lfs flag to the samba share in /etc/fstab - but as mentioned I'm using windows clients and I just have them added as network locations.  Any ideas? Thanks!  Samba server is using linux accounts as auth and its occuring in my home directory. File system on the server is ext4 encrypted/software raid 1.

---

### Post by Hazey11 on 2011-11-15
Anyone have any ideas? I'm at my wits end with this, as I said there seems to be an LFS flag you can set on a linux client in /etc/fstab so i'm wondering if there is such a thing with windows? I don't think so as windows 7 and pretty much every version since 2000 has been ntfs so it's built in LFS all around. Or does the problem lay in the server?

---

### Post by Hazey11 on 2011-12-16
Any ideas anyone? Been a long time no replies hoping anyone has any kind of ideas? Thanks

---

