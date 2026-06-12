---
title: "Problem with groups"
date: 2010-03-15
forum: General Help
---

### Post by Ivanrdg on 2010-03-15
Hello,

I will first tell you some personal configurations:

$ ls -ld /mnt/grups/velec
drwxrws--- 14 root velec 4096 Mar 15 13:07 /mnt/grups/velec/

$ id
uid=7862(ivan) gid=10096(velec) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),104(fuse),105(lpadmin),112(netdev),115(admin),122(sambashare),124(vboxusers),400(inet),605(alumnes-eps),10096(velec)

$ ls -l /mnt/grups/velec
ls: cannot open directory /mnt/grups/velec: Permission denied

Why I can't access /mnt/grups/velec if I am member of group velec?

If you need to know more information, please tell me what do you need...

Thank-you!

---

### Post by gmargo on 2010-03-15
How is the directory mounted?  Local mount options and remote export options can make a difference.  What happens if you duplicate the test on a local disk?  (It worked as expected for me.)

---

### Post by Ivanrdg on 2010-03-15
I have a mounted file system provided by my university. Here is my fstab line:

$ grep grups /etc/fstab 
grups.udl.net:/usuaris/grups    /mnt/grups    nfs    noauto,user,rw,bg,vers=3,tcp,timeo=600,rsize=32768,wsize=32768,hard,intr    0    0

I used the command mount /mnt/grups after reboot as a normal user...

Thank-you!

---

