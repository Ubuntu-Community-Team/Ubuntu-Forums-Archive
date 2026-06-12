---
title: "How to install Debian side-by-side to Ubuntu..."
date: 2010-12-20
forum: General Help
---

### Post by Linyx on 2010-12-20
[SIZE="2"]I am running Lucid, but i want to test Debian OS, but i don't want to run in VM, therefore i had decided to install Debian side-by-side to Ubuntu...

Debian also uses Grub-2..? i am asking this because once i install it, i don't want to lose my Ubuntu, therefore i need Advice before install it,...[/SIZE]

---

### Post by Linyx on 2010-12-20
[SIZE="2"]bump[/SIZE]

---

### Post by karmila on 2010-12-20
Make another partition for debian installation, install debian there.

At installation, if you are prompted where to install grub choose to install grub at your debian partition (for example /dev/sda5) instead of install it to your hard drive (sda) so you still can use your ubuntu grub.

After installation you will not see debian yet because you are using ubuntu grub. Then at ubuntu terminal update-grub
```
sudo update-grub
```Grub should detect your debian installation.

---

### Post by mastablasta on 2010-12-20
[QUOTE=Linyx;10259403] 
[SIZE=2]Debian also uses Grub-2..? [/[/SIZE]QUOTE]
 
Debian testing (Sqeeze) is using the same Grub as Ubuntu:
[http://distrowatch.com/table.php?distribution=debian](http://distrowatch.com/table.php?distribution=debian)
 
 
Lenny is quite old, while Squeze is already frozen, so they are now just clearing the bugs. I think this is the one you will probably want to try.
 
Another option is to use Debian LiveCD and make persistant USB from it [http://live.debian.net/](http://live.debian.net/).

---

### Post by Linyx on 2010-12-21
[SIZE="2"]I made a live-USB of debian OS, but while Installing, it gives a message that **mount your CD-Rom**, and i am installing it via USB...

Any suggestion..?[/SIZE]

---

