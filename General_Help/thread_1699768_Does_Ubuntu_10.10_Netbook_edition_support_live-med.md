---
title: "Does Ubuntu 10.10 Netbook edition support live-media-path?"
date: 2011-03-04
forum: General Help
---

### Post by Holmes.Sherlock on 2011-03-04
Yesterday I got confused while doing the following:

[LIST]
[*]I extracted [COLOR=#171717]**ubuntu-10.10-netbook-i386.iso**[/COLOR] in a folder on hard disk called **ubuntu-10.10-netbook-i386.**
[*][COLOR=#171717]In Grub4DOS menu.lst, I used this piece of code[/COLOR]
[/LIST]```

[COLOR=#171717]title ubuntu 10.10-netbook-i386  [/COLOR]
[COLOR=#171717][/COLOR] 
[COLOR=#171717]kernel /ubuntu-10.10-netbook-i386/casper/vmlinuz file=/ubuntu-10.10-netbook-i386/preseed/ubuntu-netbook.seed boot=casper ignore_uuid live-media-path=/ubuntu-10.10-netbook-i386/casper/  [/COLOR]
[COLOR=#171717]  [/COLOR]
[COLOR=#171717]initrd /ubuntu-10.10-netbook-i386/casper/initrd.lz[/COLOR]

```
 
[COLOR=#171717]When I tried to boot, it stopped with an error saying that it can't find **ubuntu-netbook.seed **file. It made me belief that this distro does not support **live-media-path **parameter. But, probably, a few months back I experimented with the same distro & got a success. I know it supports **iso-scan/filename. **But that's not my point. Can anybody please try out with the distro & report whether it supports **live-media-path **or not?[/COLOR]

---

