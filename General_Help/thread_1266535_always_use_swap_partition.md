---
title: "always use swap partition"
date: 2009-09-14
forum: General Help
---

### Post by FreezWay on 2009-09-14
I have to re-partition my disk a while back, and i just discovered, when i boot, my swap partition is not on! i have gparted. i can turn it on manually whenever i boot, but i'd rather not. Is there a way to make it so it automatically turns on?

Also, when i repartitioned my disk i got a different upsplash sceen (i switched from kde to gnome, when i sudo apt-got(like my new verb?) ubuntu-desktop it changed it for me.) I get the Kubuntu screen instead of the ubuntu screen.

Any help is very much appreciated.

---

### Post by oldfred on 2009-09-14
When you repartitioned you probalby renumbered you partitions.
find the UUID number for your swap
blkid -L
gksudo gedit /etc/fstab

You should find an entry like mine and plug in your correct UUID.

# Entry for /dev/sdb5 :
UUID=144d59f5-9eeb-49ce-9d78-83bd317c443d none swap sw 0 0

I installed kubuntu over my ubuntu and I still get the kbuntu logo even though I deleted most of the kubuntu. Someone said startup manager will allow you to fix it but I have not tried.

---

### Post by CatKiller on 2009-09-14
> **FreezWay said:**
>  Also, when i repartitioned my disk i got a different upsplash sceen (i switched from kde to gnome, when i sudo apt-got(like my new verb?) ubuntu-desktop it changed it for me.) I get the Kubuntu screen instead of the ubuntu screen.

```
sudo update-alternatives --config usplash-artwork.so
sudo update-initramfs -u 
```

---

