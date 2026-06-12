---
title: "How can I edit fstab on bootup?"
date: 2011-10-16
forum: General Help
---

### Post by Tighearna on 2011-10-16
I was trying to load my NAS on boot up.

I added the line to the fstab, except I messed something up.

Now the computer will not boot.

I can access the fstab on boot from the command line but it is in read only.

How can I edit the fstab so I can remove those lines?

Thank you in advance.

---

### Post by Tighearna on 2011-10-16
If anyone else faces this, the way I solved it was.
1. Boot to the live cd
2. Go To Places
3. Open the folder that is you HDD
4. Open a terminal
5. gksudo nautilus
6. open /etc/
7. open fstab with gedit
8. modify and save
9. reboot problem solved.
Hope that helps.

---

