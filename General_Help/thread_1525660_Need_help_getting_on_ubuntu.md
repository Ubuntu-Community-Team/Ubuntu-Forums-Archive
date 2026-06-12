---
title: "Need help getting on ubuntu"
date: 2010-07-07
forum: General Help
---

### Post by sbctony on 2010-07-07
Ok so im not a total noob but not that tech savvy either. I put windows 7 on my desktop which is a dell E521. I had windows vista on their previously and had a dual boot setup on it. When i installed win 7 on i just did the upgrade so i wouldnt have to reformat my hardrive and now when i boot up it will not show the option to boot into windows or ubuntu. If anyone could give me a hand that would be awesome. Thanks for reading!!

---

### Post by sbctony on 2010-07-07
Ok so im not a total noob but not that tech savvy either. I put windows 7 on my desktop which is a dell E521. I had windows vista on their previously and had a dual boot setup on it. When i installed win 7 on i just did the upgrade so i wouldnt have to reformat my hardrive and now when i boot up it will not show the option to boot into windows or ubuntu. If anyone could give me a hand that would be awesome. Thanks for reading!!

---

### Post by JoelOl75 on 2010-07-07
When you upgraded Windows, it remove Grub from the MBR.  All you need to do is boot off the Ubuntu Live CD and reinstall GRUB to the MBR.  Assuming you are using Grub 2 you can follow the instructions at [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by mikewhatever on 2010-07-07
You'd have to reinstall Grub, the Ubuntu boot loader. Boot from a live cd, then follow the steps:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by philinux on 2010-07-07
> **sbctony said:**
> Ok so im not a total noob but not that tech savvy either. I put windows 7 on my desktop which is a dell E521. I had windows vista on their previously and had a dual boot setup on it. When i installed win 7 on i just did the upgrade so i wouldnt have to reformat my hardrive and now when i boot up it will not show the option to boot into windows or ubuntu. If anyone could give me a hand that would be awesome. Thanks for reading!!

Post #2 has all info in link.

Also this link will show you how.

Make sure you read through first.
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

For future reference this link is worth bookmarking too.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by lisati on 2010-07-07
Threads merged

---

### Post by sbctony on 2010-07-07
im using grub 0.97

---

### Post by sbctony on 2010-07-07
and still nothing ive tried the steps :/

---

