---
title: "Is there a way to backup all programs installed?"
date: 2009-09-16
forum: General Help
---

### Post by rock it on 2009-09-16
Hi all,
Is there a way to backup all the programs that I have installed on xubuntu then if I have to re-install the os I can just stick all the programs back on?

either that or a way to backup my whole HDD?

thanks,:)

---

### Post by ubongo2008 on 2009-09-16
```
 dpkg --get-selections > myInstalledPackages.txt 
```restore with synaptic or  

```
dpkg --set-selections
```

you can also make an image of your linux install and restore it to an other computers patition then reinstall the bootloader and correct /etc/fstab 

i do that all the time (make a nice linux, distribute it to all other boxes)

---

### Post by rock it on 2009-09-16
If I did that would it work for wine? and wine-doors?
also do you know how I could make backup of everything on the HDD... like everything, because I'm wanting to dual boot, but if it doesn't work then I'd like to have all my programs ready to stick back on without having to download again.

sorry if this makes no sense or if I'm repeating. :S

---

### Post by lovinglinux on 2009-09-16
> **rock it said:**
> If I did that would it work for wine? and wine-doors?
also do you know how I could make backup of everything on the HDD... like everything, because I'm wanting to dual boot, but if it doesn't work then I'd like to have all my programs ready to stick back on without having to download again.

sorry if this makes no sense or if I'm repeating. :S

It only works for applications installed from the repositories. So any application manually downloaded and installed will require manual installation again.

Those commands works really nice. You could also use my [Umarks](https://addons.mozilla.org/en-US/firefox/addon/13153) Firefox extension, which basically does the same thing, but also creates, export and import lists of installed packages, that can be easily re-installed again using the extension installation feature. It also provides easy searching for installed packages on web sites like allmyapps, which also allows to create lists of installed packages and install them all at once.

If you don't want to download them again, then you could use remastersys.

---

### Post by little_penguin on 2009-09-16
You can create an exact image of your partition with a program called Partimage. There are some good howtos around, and once you get the hang of it, it's invaluable. 

Download yourself a Live CD with partimage on it via bittorrent (e.g. Parted Magic Live CD or just use a Ubuntu Live CD) and boot from that, because the partition you want to image cannot be mounted.

I've used Partimage for quite a bit now and it's saved my bacon a few times ;o)

Hope it helps,
LP

---

### Post by por100pre1 on 2009-09-16
> **rock it said:**
> If I did that would it work for wine? and wine-doors?
also do you know how I could make backup of everything on the HDD... like everything, because I'm wanting to dual boot, but if it doesn't work then I'd like to have all my programs ready to stick back on without having to download again.

sorry if this makes no sense or if I'm repeating. :S

Backup your whole user folder. That will save all Wine configuration and programs. For everything else use the commands in the second post.

---

### Post by freackout on 2009-09-16
> **por100pre1 said:**
> Backup your whole user folder. That will save all Wine configuration and programs. For everything else use the commands in the second post.

have you tried aptoncd its simple click and puts all your debs on cd and when you later insert it it will put them back on your hard drive.

---

### Post by raymondh on 2009-09-16
> **freackout said:**
> have you tried aptoncd its simple click and puts all your debs on cd and when you later insert it it will put them back on your hard drive.

+ 1.

I have used apton to move apps, repos, from one install to another (same version).

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Good luck.

---

### Post by por100pre1 on 2009-09-16
> **freackout said:**
> have you tried aptoncd its simple click and puts all your debs on cd and when you later insert it it will put them back on your hard drive.

I have tried it, but I experienced memory leaks with latest version from the repos. Too bad, AptonCD is a great tool.

---

### Post by majiciannz on 2009-09-16
Try Remastersys.

It will do everything you are wanting.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

