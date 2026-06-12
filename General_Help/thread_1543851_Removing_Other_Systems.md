---
title: "Removing Other Systems"
date: 2010-08-01
forum: General Help
---

### Post by Hosmion on 2010-08-01
Hello everyone.  Recently my Windows got infected with a malicious file and it is not unaccessible.  I need to delete it off my dual-boot menu, but I don't know how.  Does anyone know?

I have an Acer computer, if that helps any.

Thanks,
Tom

---

### Post by Harris6310 on 2010-08-01
You can download a .iso for a partition editor (use google to find one), write it to a blank disc, re-boot with the disc in the disc drive, then finally delete the partition which contains Windows.

---

### Post by jerenept on 2010-08-01
In a Terminal:

```
 sudo apt-get install gparted
```
```
gksudo gparted
```

Then unmount and delete the NTFS partition.

now; ```
 sudo update-grub
```

---

### Post by malspa on 2010-08-01
I like to use a Mepis live CD for that kind of thing.  I guess any distro's live CD would work if it has GParted on it, but I'm most familiar with Mepis.  That way I can do partitioning, but also if something goes wrong I can boot into a live session and have a nice desktop available to work from.

---

### Post by prodigy_ on 2010-08-01
If you want to keep your Windows system partition, you can just disable os-prober script and run update-grub: ```
sudo chmod -x /etc/grub.d/30_os-prober
sudo chmod update-grub
```

---

