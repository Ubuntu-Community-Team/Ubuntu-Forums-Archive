---
title: "remove old partition"
date: 2010-06-27
forum: General Help
---

### Post by Dex73 on 2010-06-27
I partitioned my drive with Hardy and Lucid, but now I'm ready to go all Lucid. Can I remove Hardy and have Lucid take over the whole drive without having to completely reinstall my OS?

---

### Post by wilee-nilee on 2010-06-27
> **Dex73 said:**
> I partitioned my drive with Hardy and Lucid, but now I'm ready to go all Lucid. Can I remove Hardy and have Lucid take over the whole drive without having to completely reinstall my OS?

Probably, post the bootscript in my signature in code tags as described. I just want to be sure that grub-legacy isn't mixed in with Lucid other then a chainload.

---

### Post by Dex73 on 2010-06-28
Can you tell me how? I don't know how to post the boot script. It would be great to be able to keep things like they are in Lucid.

---

### Post by wilee-nilee on 2010-06-28
> **Dex73 said:**
> Can you tell me how? I don't know how to post the boot script. It would be great to be able to keep things like they are in Lucid.

Boot the live cd and take a screenshot of gparted it is in system-admin-gparted and post it to the thread. You will use the live cd and gparted to remove Hardy and expand Lucid. The thing here is that both had different bootloaders, and I'm just taking extra precautions that your setup here, and that you don't bork Lucid.

---

### Post by dcstar on 2010-06-28
> **Dex73 said:**
> I partitioned my drive with Hardy and Lucid, but now I'm ready to go all Lucid. Can I remove Hardy and have Lucid take over the whole drive without having to completely reinstall my OS?

If you installed Lucid last and installed the Grub2 bootloader to the standard place (the MBR), then simply unmount and delete the old partition using gparted.

Then do:

```
sudo update-grub
```

---

### Post by wilee-nilee on 2010-06-28
> **dcstar said:**
> If you installed Lucid last and installed the Grub2 bootloader to the standard place (the MBR), then simply unmount and delete the old partition using gparted.

Then do:

```
sudo update-grub
```

I'm just overly cautious.;) you are correct.

---

### Post by Dex73 on 2010-06-28
This is my gparted screen shot.

---

### Post by wilee-nilee on 2010-06-28
From a live Ubuntu cd with gparted remove ext3=hardy then expand the extended to the left then do the same with ext4. You will have to turn both swaps off to do this.

You have two swap partitions which are no big deal you can remove both and just put one back in that takes up the space completely, which will be more then you need or after running the first paragraphs instruction you could expand the ext4 to the right and have the one swap that is equal to your ram amount.

I'm assuming that the hardy setup has nothing you want to save in it here, once ext3 is removed it is basically gone.

---

### Post by oldfred on 2010-06-28
I do not like moving partitions left unless you have to. It will work but because it has to copy all the data and verify the copy it can take a very long time. Because of the extended time it is a bit more risky as any power failure or other hiccup will leave you unbootable. Always good to have backups of important data before partition operations.

I might suggest you use the existing partition as /home if you want to move /home or just use it as a data partition.

Also a few BIOS want a boot flag on a primary partition (they precheck that windows will boot as windows needs a flag). Grub does not need the flag but it is good practice to keep a primary partition and keep a boot flag on it even if you do not boot from it.

---

### Post by wilee-nilee on 2010-06-28
> **oldfred said:**
> I do not like moving partitions left unless you have to. It will work but because it has to copy all the data and verify the copy it can take a very long time. Because of the extended time it is a bit more risky as any power failure or other hiccup will leave you unbootable. Always good to have backups of important data before partition operations.

I might suggest you use the existing partition as /home if you want to move /home or just use it as a data partition.

Also a few BIOS want a boot flag on a primary partition (they precheck that windows will boot as windows needs a flag). Grub does not need the flag but it is good practice to keep a primary partition and keep a boot flag on it even if you do not boot from it.

I would agree the process is a long one, and many like the separate home, I don't use this as I change OS at the drop of a hat, and just know how to set them up quickly and have my junk on a external HD.

---

### Post by Dex73 on 2010-06-29
I messed something up with gparted and I couldn't even boot. So, I rebooted the OS and copied my external hard drive. Everything works great now. For anyone else that's reading this, it is much easier and faster to just install over everything(assuming you have an external hard drive). Thanks for all the help anyway!

---

