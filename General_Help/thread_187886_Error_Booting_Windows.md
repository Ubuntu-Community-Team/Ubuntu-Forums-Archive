---
title: "Error Booting Windows"
date: 2006-06-03
forum: General Help
---

### Post by Adanufgail on 2006-06-03
I'm using GRUB. When I try to boot Windows XP, it says "loading stage2" and goes back to the GRUB loading screen.

Here is my Menu.lst:

```
title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1
```

Any help is greatly appreciated.

---

### Post by trivialpackets on 2006-06-03
[QUOTE=Adanufgail]I'm using GRUB. When I try to boot Windows XP, it says "loading stage2" and goes back to the GRUB loading screen.

Here is my Menu.lst:

```
title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1
```

Any help is greatly appreciated.[/QUOTE]

[QUOTE=LO Matt]Bingo.  I'm in a band with it's own website and a myspace site.  The myspace site gets significantly more hits than the proper website.  Maybe not the same for big acts, but for small bands, this is true for lots of them.

It's a good place for music fans too.  Lots of artists preview their records on myspace before they are available.  

For others, it's the internet for dummies.

[sarchasm]MySpAZe iZ Da kEWL![/sarchasm] :-D[/QUOTE]


Try this.  


title Windows XP
	rootnoverify (hd0,0)
	chainloader +1

Hopefully this works for you.

---

### Post by Adanufgail on 2006-06-03
No, sorry. It still goes straight back to the grub loading screen.

---

### Post by trivialpackets on 2006-06-03
Tell you what, scares me a bit.  I haven't even bothered trying to get to windows since installing Dapper.  :)  I've read reports of errors with grub while doing "things" while running the installer.  Not sure though, it may be that something corrupted your windows install.  Let me just say I hope not.  Installing a beta of kubuntu wiped my windows drive entirely.  Color me not impressed, but I'm still here and I love Dapper still.

---

### Post by Adanufgail on 2006-06-03
Nah, I can still access the partition (I have it at /media/windows/). Although, I ran fixmbr off of my Windows XP Setup Disk and when I rebooted, GRUB came up. Also, this started before I upgraded to Draper Drake.

---

