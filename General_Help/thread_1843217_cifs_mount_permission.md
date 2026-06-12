---
title: "cifs mount permission"
date: 2011-09-13
forum: General Help
---

### Post by daddmac on 2011-09-13
Problem: allowing non-root users to write to a cifs mountpoint.  

I have created a mountpoint from a 10.04 Ubuntu server to a Windows 2008 server.  I can read it with non-root accounts, but cannot write to it with non-root accounts.  

From what I've read, the root ownership and 755 (?) permissions are by design.  However, I need to allow non-root accounts to create files in the mountpoints.  

I've tried chown and chmod at various levels in the mountpoint.  

Also, for context, I'm access the mountpoint via a sftp chroot.  When the same tree is local/not a cifs mountpoint it works as expected.  

cifs version 1.12-3.4.7

command I'm using to connect:
mount.cifs //server/share /mountpoint -o user=domain/user uid=localnixuser noperm rw

Anyone know what I need to do to give write access to a non-root user?  

TIA.

---

### Post by daddmac on 2011-09-13
Links and references are equally welcome.

---

### Post by jwcalifo on 2011-09-13
Try creating a "cifsgroup" group and then assign group ownership to that and then place your read-write users in that group.

---

### Post by daddmac on 2011-09-13
Thanks for the suggestion!  

I did it, using a group named sftponly.  

After the chown ls -l listed sftponly as the owner group with 755.  

I mounted the share and ls -l listed root as the owner group with 755.  Also, the non-root account I tested with got "permission denied" when it tried to touch a file.

If it helps to know, on the Windows server the connecting account (user=) has full permissions and is the owner.  

I'm willing to test variations of the above.  So you know I'm not a feeb, I've tried every combination that I can find listed on google or from my interpretation of what I think I could be doing wrong based on the man page.

---

### Post by daddmac on 2011-09-13
I don't know if this is relevant, but the mount.cifs command ignores the password= argument that I include, and prompts me for the password, and forces me to enter it before mounting the share.

---

