---
title: "Samba and hidden files"
date: 2009-08-26
forum: General Help
---

### Post by root1234 on 2009-08-26
Hi All.

I have a samba server running 100%.

I have a mapped Drive op windows xp workstations.

The client needs to be able to hide files.

If you right click on the file or folder, go to properties, it gives you the tickbox "hidden" and if you tick it and apply nothing happens, and no error message?

and then if you right click and go to properties the "hidden" tickbox is un-ticked?

Please if anyone can help, it will be great!

Thanks
Root1234

---

### Post by nikhilk on 2009-08-26
Check these threads for solution to a similar problem
[Thread1]("http://ubuntuforums.org/showthread.php?t=1046948")
[Thread2]("http://ubuntuforums.org/showthread.php?t=127012")

---

### Post by root1234 on 2009-08-26
Thanks for the reply.

---

### Post by root1234 on 2009-08-26
Me again.

I followed the links and it help a bit.
I can hide files now but still can't hide any folders via windows xp in the samba share.

here is my share 
[share]
        comment = share
        path = /home/share
        guest ok = yes
        read only = no
        browseable = no
        directory mask = 0744
        create mask = 0755
        map system = Yes
        map hidden = Yes

Please could you assist

---

