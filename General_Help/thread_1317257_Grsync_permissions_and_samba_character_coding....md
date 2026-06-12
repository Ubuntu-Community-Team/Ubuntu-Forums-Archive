---
title: "Grsync permissions and samba character coding..."
date: 2009-11-06
forum: General Help
---

### Post by Quaxo76 on 2009-11-06
I need to periodically sync a local folder on my pc with a samba share on a file server. I use grsync for my syncing needs, but it does not recognize smb:// addresses. So I added, in the grsync configuration, the following command to be executed BEFORE the sync:
```
sudo mount -t smbfs -o username=XXX -o password=YYY //192.168.1.3/cristian/ /media/sambacri/
```
so that the share is automatically mounted before the sync, and then I can sync to the local file system, and then the share is unmounted in a similar way.
But when the command is executed, grsync doesn't stop to ask my sudo password, so the command is not really executed, and the share is not mounted.
I can launch grsync as root, and remove the "sudo" from the above command; but I think it's dangerous. Is there another way to make grsync mount the share before syncing? A box that asks me for the password is OK, but having to mount manually via terminal is not (other users have to run grsync that can't use a terminal).

Even when running grsync as root, it works, but there's a problem: the mentioned mount command doesn't set the correct character coding. I have several files/folders with accented characters, and they're not recognized after mounting that way (they're shown as garbage characters).
Navigating to the share using Nautilus (to the smb:// address) works perfectly, and the accented characters are displayed properly. Needless to say, this incorrect character coding messes up my syncing.

Can anyone help me on either (or both! :) ) of these problems?

TIA, Cristian

---

### Post by Quaxo76 on 2009-11-10
Bump... Anyone?

---

