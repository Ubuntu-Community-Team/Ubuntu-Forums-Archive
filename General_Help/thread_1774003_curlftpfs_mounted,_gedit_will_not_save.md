---
title: "curlftpfs mounted, gedit will not save"
date: 2011-06-02
forum: General Help
---

### Post by Little Blue on 2011-06-02
Hi,

I've been trying to mount a remote ftp server using curlftpfs and, just as I finally get that working, I get stuck on trying to edit the remote files using gedit.

This is the command I use to mount it:
```
sudo curlftpfs -o allow_other -o uid=1000 -o gid=1000 -o direct_io -o umask=000 ftp.site.org mount/point
```

and then a simple "gedit index.php" afterwards. When trying to save the file after editing it I then get the following error:

"gedit cannot handle *file:* locations in write mode."

I'm sure its not an obvious permissions error as uid etc should set the mounted system to my user as the owner, and the mask is setting everything to 777 (I've done various permutations of having uid, gid, umask or not (e.g., sudo curlftpfs -o allow_other -o direct_io ftp.site.org mount/point) with no change), and I can still do things like mv and write files with nano, but not with gedit. (Incidentally, nano also says "(Warning: No write permission)" but writes regardless)

I've seen many a post about this from google, but I am yet to find a usable solution beyond gksudo gedit, and for some reason I dislike the idea of doing something as trivial as remote editing php files in a sudo session... Or is this the best I can hope for, that or use another editor for this stuff! :P

Cheers

---

### Post by atz6975 on 2012-03-27
Hi,
I'm running into this problem on Ubuntu 11.10x64 Desktop.
I can do wathever I want with nano.
But Gedit refuses to save and edited file on the mounted curlftpfs.
I get the same error as OP.

Thank you for any suggestions.

---

