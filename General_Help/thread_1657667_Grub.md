---
title: "Grub"
date: 2011-01-01
forum: General Help
---

### Post by Armaeddon on 2011-01-01
Hi.
I've (attempted) to create a quad-boot on my MacBook Pro (if the specs are needed, its- 8gbs RAM, core i7, 500GB hard drive @ 7200 rpms, and its running the latest update of snow leopard). I have installed rEFIt and had installed Windows 7 as well as ubuntu 10.10. Everything was working great until i tried loading Linux Mint 10. Linux Mint got rid of Ubuntu in the rEFIt boot menu. I thought the added Linux Mint partition had just pushed out Ubuntu, so i deleted the Linux Mint partition, and re-sized the Macintosh HD. Now whenever i try to boot Windows 7 or Ubuntu, i get something along the lines of "invalid file system: Grub rescue" What do I do?

---

### Post by Armaeddon on 2011-01-01
Can someone please help? i've recently tried entering "cat /grub/grub.cfg" but that didn't work, and i also tried booting from the DVD, but that didn't work either. please, please help

---

### Post by karthick87 on 2011-01-01
It is,
```
cat /boot/grub/grub.cfg
```

---

### Post by Armaeddon on 2011-01-01
It tells me that 'cat' is not a recognizable command

---

### Post by karthick87 on 2011-01-01
Boot from a live cd and post the results of [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) with code(#) tags.

---

### Post by Armaeddon on 2011-01-01
Is this what you want?
```
bash: -/: invalid option
Usage:    bash [GNU long option] [option] ...
    bash [GNU long option] [option] script-file ...
GNU long options:
    --debug
    --debugger
    --dump-po-strings
    --dump-strings
    --help
    --init-file
    --login
    --noediting
    --noprofile
    --norc
    --posix
    --protected
    --rcfile
    --restricted
    --verbose
    --version
    --wordexp
Shell options:
    -irsD or -c command or -O shopt_option        (invocation only)
    -abefhkmnptuvxBCHP or -o option
```

---

### Post by Armaeddon on 2011-01-01
I've decided to just start everything over, so thanks for your help, but....yeah. thx anyway

---

### Post by dcstar on 2011-01-02
> **Armaeddon said:**
> Hi.
I've (attempted) to create a quad-boot on my MacBook Pro (if the specs are needed, its- 8gbs RAM, core i7, 500GB hard drive @ 7200 rpms, and its running the latest update of snow leopard). I have installed **rEFI**t and had installed Windows 7 as well as ubuntu 10.10.
........

This bootloader is not an Ubuntu package, you will have to work out for yourself how to fix it:

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

It would seem to be simpler to just use the standard Ubuntu Grub bootloader?

---

