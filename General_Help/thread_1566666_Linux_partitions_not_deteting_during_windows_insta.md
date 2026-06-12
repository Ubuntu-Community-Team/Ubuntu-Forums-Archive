---
title: "Linux partitions not deteting during windows installation"
date: 2010-09-02
forum: General Help
---

### Post by h3llboy on 2010-09-02
Hello Everyone!!

I have installed openSUSE few days before that became the master boot along with windows xp. Then i tried to install windows xp again where i could see only 125 GB of my hard disk. But i see my whole 250 GB hard disk after installing UBUNTU. From then, im trying to installing Windows XP where its not detecting the linux partitions i guess.

Any help in this is greatly appreciated as i couldn rely permanantly on an OS.
I want to install Windows XP where i need all my 250 GB while installing. After that i will install UBUNTU within Windows.

Please help.

---

### Post by Autodidact on 2010-09-02
I assume you want to clear everything and install XP onto a new partition that uses the whole disk.

After booting the XP disk and agreeing with the licensing agreement you should see the partition manager. Delete all partitions that show up. Now there is only one entry left, named 'Unpartitionated Space'. This should equal the 250GB disk size.

Now just hit enter. Windows XP will automatically create one new partition that covers the whole disk.

---

### Post by h3llboy on 2010-09-02
Thanks for the response. If that is the case then i would have installed on the fly. What i see is an unpartitioned space that has 130 gig. I dont know what happens to the remaining gigs. That's the problem im facing.

---

### Post by Cypress421 on 2010-09-02
Delete all the partitions as suggested or try GParted to exterminate all partitions:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

