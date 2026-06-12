---
title: "Booting windows after installing ubuntu"
date: 2012-05-26
forum: General Help
---

### Post by Rammstein55 on 2012-05-26
Hello,

I recently installed ubuntu server alongside windows, I boot my PC and it automatically goes to ubuntu. Can anyone give me a command or tell me how to boot windows from here. Help would be greatly appreciated thank you.

---

### Post by Shadius on 2012-05-26
> **Rammstein55 said:**
> Hello,

I recently installed ubuntu server alongside windows, I boot my PC and it automatically goes to ubuntu. Can anyone give me a command or tell me how to boot windows from here. Help would be greatly appreciated thank you.

I have no experience with Ubuntu Server, but I think you need to install GRUB so that it gives you options on which system to boot into. 

Check here:

[GRUB]("https://help.ubuntu.com/community/Grub2")

---

### Post by listerdl on 2012-05-26
This might be helpful - [http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/](http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/)

Then i realized you said ubuntu server!

---

### Post by wilee-nilee on 2012-05-26
In the server terminal.

```
sudo update-grub
```

If you are in root no sudo.

---

