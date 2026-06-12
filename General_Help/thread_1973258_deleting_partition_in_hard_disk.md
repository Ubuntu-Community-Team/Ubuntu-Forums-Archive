---
title: "deleting partition in hard disk"
date: 2012-05-04
forum: General Help
---

### Post by gozlemci on 2012-05-04
Hi everyone.
My hard disk was divided. There are XP and ubuntu in my Hard disk, and it asks where to start.
I want to delete XP partititon and let ubuntu to control whole HDD.Ubuntu must be the default os and no question in start-up.How?

Thanks in advance.

---

### Post by grahammechanical on 2012-05-04
The simple way it to install Ubuntu from a live CD and tell the installer program to use the entire hard disk.

But, and I repeat BUT, this will remove all your files and documents. So, backup everything that you do not want to loose.

The second way is to use the live Cd and go into Try Ubuntu and then launch Gparted. And use that to remove the windows partitions (there will be more than one) and to re-size the Ubuntu partition to take up the space and fill the whole hard disk.

You will then need to boot into Ubuntu and run the command

```
sudo update-grub
```

To refresh the Grub menu so that it no longer shows Windows XP as an option.

Plan everything first.

Regards.

---

### Post by m3topaz on 2012-05-04
If you are re-installing, use the installer to 'flatten' the hard disk and remove everything for a clean install.
If not, you can grab gparted and use that to remove the XP partition as the first step. If you want to use the space for Ubuntu, format it to ext4 or whatever and set a mount point. Then you can drop files on that mount.
Update grub with $ sudo update-grub

---

### Post by gozlemci on 2012-05-04
Thanks, m3topaz and  grahammechanical.

---

