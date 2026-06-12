---
title: "Samba cdrom - mount/umount ?"
date: 2009-11-16
forum: General Help
---

### Post by VeskoJl on 2009-11-16
I've configured samba share for my cd , but when client disconnects cd is not unmounted and manually unmount also doesn't work! Here is my config:

[cdrom]
  read only = yes
  locking = no
  path = /media/cdrom0
  guest ok = yes


  preexec = /bin/mount /media/cdrom0
  postexec = /bin/umount /media/cdrom0

---

### Post by VeskoJl on 2009-11-16
The strange thing is that i can "sudo umount" , but can't right click -> umount cd icon on Desktop! That gives me following error:

"umount: only nobody can unmount /dev/...."

!! I got why can't unmount cd from Desktop - i mounted it from client like guest, so  can't umount it from dskt, because that's different user.

So basically preexec works, but when postexec is fired ?

---

