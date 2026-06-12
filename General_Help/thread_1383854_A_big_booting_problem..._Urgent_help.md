---
title: "A big booting problem... Urgent help"
date: 2010-01-17
forum: General Help
---

### Post by Coffee Coder on 2010-01-17
Hello, I've been having a bit of a problem. So here it goes, I was trying to do a clean install of ubuntu 9.10 but I had two hard drives so I decided to use one for the "/" partition (+swap) and another one for the "/home" partition. The problem started when the installation was at around 80%, it suddenly froze so I had to reboot the computer. Well, since that happened I haven't been able to boot from any device. I've tried using the CD, USB, HD but none of them seem to be recognized. Also, when I try to boot from the HD I get a GRUB rescue prompt, but the only command that it seems to recognize is "ls".

So this is kind of a big problem since I can't use the computer in any way. Any help will be appreciated.

---

### Post by Leppie on 2010-01-17
you could try the following:
```
set root=(hd0,1)
insmod normal
insmod linux
linux /vmlinuz root=/dev/sda1 ro        
initrd /initrd.img        
boot
```

---

