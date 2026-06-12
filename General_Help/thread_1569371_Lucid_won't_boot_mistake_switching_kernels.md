---
title: "Lucid won't boot: mistake switching kernels"
date: 2010-09-06
forum: General Help
---

### Post by macho on 2010-09-06
I switched to the linux-image-rt kernel a while back, and decided yesterday to switch back to linux-image-generic. Unfortunately, I couldn't remember how to do this properly, so I just uninstalled all of the linux-rt related packages and then changed the /vmlinuz and /initrd.img symbolic links back to what they used to be and rebooted.

So now the machine gets stuck in a memtest whenever I boot from the HD.

I'm having trouble figuring out how to fix things from a rescue CD. If I try chroot /mnt/hd (where my old system was), and then update-grub, for example, I get:

/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

So, basically I'm completely lost, but also sure that a working system isn't more than a few simple commands away. Can anyone throw me a bone?

Thanks.

Oh, and I'm running Lucid.

---

### Post by oldfred on 2010-09-06
chroot into your system & update it.

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

# new for lucid & karmic 
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

Commands once in chroot:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by macho on 2010-09-07
This was extremely helpful, thanks so much.

On its own, this didn't fix my problem (I'm not sure the last command did anything for me), but I found that afterwards also doing

```
dpkg-reconfigure grub-pc
```

seemed to work just fine.

---

