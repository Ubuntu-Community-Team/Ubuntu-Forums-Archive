---
title: "Mount issue"
date: 2011-09-10
forum: General Help
---

### Post by Peter Engstrom on 2011-09-10
Hi all!

Using ubuntu 10.10 for mounting a smb share on a Fedora 14 server owned by me.

If mounting the share in Nautilus providing all credentials, the share is RW = no problems at all.
 
If mounting the share as in #mount -t cifs ...etc... the share will never go RW.

Have tested a lot -o options and followed links in this forum, so what am I doing wrong?

// Regards Peter

---

### Post by Peter Engstrom on 2011-09-10
Hi all!

Figured it out after a while:

On Fedora 14 server I sat the file and folder rights to match the in #mount -o options rights, and now all is well.

Maybe not the very best solution but it works.

// Peter

---

### Post by Peter Engstrom on 2011-09-11
Hi again!

Never say never. And in my case I lately found the option uid=myusername to be missed in the #mount string to the server. I guess this is a better fix for my issue.

More on page: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

