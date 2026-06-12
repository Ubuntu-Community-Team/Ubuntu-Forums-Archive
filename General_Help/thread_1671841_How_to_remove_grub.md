---
title: "How to remove grub"
date: 2011-01-20
forum: General Help
---

### Post by GrixM on 2011-01-20
So I installed ubuntu next to windows, but I wanted to uninstall it, so I   deleted the partition and tried to reboot back into windows. However I   am just met with gnu grub bitching, saying `no such partition`. I  don`t  have access to a windows install cd, only the `try` feature on  the  ubuntu disk. I tried the dd if=/dev/sd1 etc etc. command in linux  but it  says permission denied.

What the hell do i do?

---

### Post by lithopsian on 2011-01-20
> permission denied

sudo ...

However, this isn't going to fix your MBR, only copy it to somewhere else.  Useful as a backup but in your case you don't want it.

Have you overwritten the windows MBR with the Grub one?  I guess you probably have.  Far and away the easiest way to restore the Windows one is with a Windows CD.  Otherwise not easy.  You can find instructions on the web but it isn't simple.

You should just be able to update Grub from your CD so it will stop complaining and just boot into Windows.  Grub will still be there but you don't have to look at it if you don't want.

---

### Post by lithopsian on 2011-01-20
> permission deniedsudo ...

However, this isn't going to fix your MBR, only copy it to somewhere else.  Useful as a backup but in your case you don't want it.

Have you overwritten the windows MBR with the Grub one?  I guess you probably have.  Far and away the easiest way to restore the Windows one is with a Windows CD.  Otherwise not easy.  You can find instructions on the web but it isn't simple.

You should just be able to update Grub from your CD so it will stop complaining and just boot into Windows.  Grub will still be there but you don't have to look at it if you don't want.

---

