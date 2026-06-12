---
title: "Intel Matrix Storage + dmraid"
date: 2011-07-20
forum: General Help
---

### Post by dfcavalho on 2011-07-20
Hello,

I'm kinda new to the forum and to Linux, but let's go straight into my problem...

I set up a desktop with Ubuntu 11.04 to use mostly as a file server. I set up a **RAID 5** using my motherboard's softRAID chip (Intel Matrix Storage). Unfortunately the software that comes with it is for Windows only.

I did a little research and I managed to make dmraid recognize and mount my RAID. But every time I reboot the server, the moment I try to mount my RAID device, I get the **"Device or resource busy"**. When that happens, if I try to use either the "dmraid -ay" or "dmraid -an" commands, the terminal freezes. The only way I've found to make it work is to uninstall dmraid (via apt-get remove), reboot the server, reinstall dmraid and then do the "dmraid -ay" command. And even then, it's not guaranteed that it will work. Sometimes I have to do this 2-3 times before I'm able to mount my RAID again. I rarely have to reboot my server, but it occasionally happens and it's very annoying.

I realize I probably haven't given enough information for you guys to help me, but I just don't know what info you guys would need. This has given me major headaches and I can't find anyone who has had a similar problem.

Can anyone help me?

Thanks in advance,
Danilo.

---

### Post by dfcavalho on 2011-09-04
Sorry to bump this, but it's been a month and I still haven't figured this out.

---

