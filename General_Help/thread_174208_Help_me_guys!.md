---
title: "Help me guys!"
date: 2006-05-11
forum: General Help
---

### Post by prince on 2006-05-11
hey i have two hard drives, on the first one i run the windows XP as the operating system and the second one had all the files i downloaded from the internet, just recently i tried out UBUNTU, i installed it as the operating system on my second harddrive. i didnt like the os very much so i want to get rid of UBUNTU (whihc is in my second hard drive) so plzz guys i could u tell me a way i could get rid of UBUNTU from my second harddrive and use it as a storage space as i used to do b4, p[lzz help thnx

---

### Post by cgjones on 2006-05-11
I haven't used Windows in awhile, so this might not be exactly right, but it should be close.

In Windows, go to My Computer, then right click on the second hard drive and click Format. Follow the steps and you should be good to go.

P.S. Any specific reason you didn't care for Ubuntu?

---

### Post by aysiu on 2006-05-11
Follow [these directions](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458)

---

### Post by linuxcity on 2006-05-11
It is likely that GRUB is installed to boot record.  You need to have a Windows 98 bootup CDrom/disk to get to the DOS Prompt.

When you get to the command prompt in DOS
type :     fdisk /MBR

that will reset the boot to the Windows Default

In Windows, Right click on "My computers | Properties | mangement" go to the DISk management section, repartition the  your second hdd, and format the partition.

Hope that helps.

---

