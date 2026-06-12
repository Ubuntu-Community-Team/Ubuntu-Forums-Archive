---
title: "removing dual boot, grub boot loader basic question"
date: 2009-09-18
forum: General Help
---

### Post by lalamax3d on 2009-09-18
history:
few months ago, i switched to linux(ubuntu), just for safe side, i kept my windows installation (partition) and install ubuntu in second partition. everything works good. just after installation, it creates something (grub) and now my computer asks me at booting , about going to (ubuntu or windows xp)

question:
now i want to remove windows, format that partition and use for data storage, as i m a lot comfortable with ubuntu. everything works for me here except a few 
a- terminal proxy (firefox / synaptic worked via settings, but terminal udpates never worked)
b- ai files creation v3 compatibility, i sometimes have to go to windows, adobe illustrator and export)

but anyhow, i have heard about wine / vmware and both of them can worked for me. so i m sure about using that first orignal partition of winXP

Q: GRUB BOOT Loader files are where?  (winXP partition or linux ext3 partition)
Q: can i simply format that partition and ubuntu booting system will automatically understand that what i have done and on computer restart, it will directly come to linux without asking anything (ideal)
Q: any ideas / recommendations, please ??

hope to hear soon, thanks

---

### Post by mikewhatever on 2009-09-18
> **lalamax3d said:**
> ..........

Q: GRUB BOOT Loader files are where?  (winXP partition or linux ext3 partition)

Grub files are on the linux partition under /boot/grub.

> Q: can i simply format that partition and ubuntu booting system will automatically understand that what i have done and on computer restart, it will directly come to linux without asking anything (ideal)



You can format the Windows partition. Grub will not know, but the fact will not hinder the boot process for Ubuntu. You can easily configure GRUB to boot Ubuntu directly, and remove the Windows entry from the menu.

---

### Post by csi_guy on 2009-09-19
As Mike stated you can edit the /boot/grub

# sudo nano /boot/grub/menu.lst

You can simply remark "#" out the windows boot options in the .lst file

Then use qtparted  to wipe out and reformat the windows partitions.

You will have to unmount the win partition first if it is mounted.

#umount /dev/sda?

---

### Post by lalamax3d on 2009-09-19
> **csi_guy said:**
> As Mike stated you can edit the /boot/grub

# sudo nano /boot/grub/menu.lst

You can simply remark "#" out the windows boot options in the .lst file

Then use qtparted  to wipe out and reformat the windows partitions.

You will have to unmount the win partition first if it is mounted.

#umount /dev/sda?

thanks guys, for sure, this will help.
i m going to do all this tonight. if any problem pops up, i'll let you know
thanks in advance, lala

---

