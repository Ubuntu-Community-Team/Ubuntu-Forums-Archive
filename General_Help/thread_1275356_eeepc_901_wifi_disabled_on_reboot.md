---
title: "eeepc 901 wifi disabled on reboot"
date: 2009-09-25
forum: General Help
---

### Post by sblanzio on 2009-09-25
Hi there!
I still have this problem on my Asus eeePc 901 I can't stand anymore.
About a month ago I did an update and since then my Wi-fi card gets disabled in bios at EVERY reboot.

To make it work I have to remember to enter the BIOS with F2 every time i switch my netbook on. If I forget I always have to reboot and enable that again. 

This is an endless loop I want to stop.
any help please?

In an old [post]("http://ubuntuforums.org/showpost.php?p=7785009&postcount=3") I found the solution would be to uninstall some packages, but I would like to just fix the problem.

thank you very much
sblanzio

---

### Post by Yer_Grannie on 2009-11-01
Hi there, you can disable this behavior by editing
/etc/init.d/eeepc-restore

disable this line:
EEEPC_PATH/eeepc-wifi-toggle.sh poweroff || true

in the stop instruction of the script by putting a # in front of it.

Cheers,
Richard.

---

### Post by sblanzio on 2009-11-03
> **Yer_Grannie said:**
> Hi there, you can disable this ...

I love you.
would you marry me? ;) 

thanks a lot!!!! :D

---

### Post by masterblah777 on 2009-11-06
Thank you very much for this post. It should be stickied. It helped me immensely.

---

### Post by pinker on 2010-05-25
can someone pls post same solution for acer aspire one (aod150)?

---

