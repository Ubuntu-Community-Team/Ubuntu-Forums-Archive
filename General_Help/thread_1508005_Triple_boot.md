---
title: "Triple boot"
date: 2010-06-12
forum: General Help
---

### Post by grumpy.biatch on 2010-06-12
Hi,

Has anyone tried or know how to make a triple boot on a single hard disk with Ubuntu 10.04 32 bit, Windows 7 x64 and Opensuse 11.2 x64. 

I have Ubuntu and Windows installed already and they work in harmony with Ubuntu Grub 2 in MBR. I need Opensuse for development.

---

### Post by MichealH on 2010-06-12
You could boot into windows and start up Computer management and "shrink" one of your partitions. The same applies for GParted in Ubuntu. Then when you install OpenSuse you just use the partition the new one that you had created. You dont need to format it aslong as you click New at the partition select screen and make a space from the unallocated amount.

---

### Post by grumpy.biatch on 2010-06-12
> **MichealH said:**
> You could boot into windows and start up Computer management and "shrink" one of your partitions. The same applies for GParted in Ubuntu. Then when you install OpenSuse you just use the partition the new one that you had created. You dont need to format it aslong as you click New at the partition select screen and make a space from the unallocated amount.


Done that already. Previously I installed OpenSolaris 2009.06 and mandriva 2010 but that didnt go well. There are complications setting up a triple boot with Grub 2.0. In addition, I have tried super grub disk from windows but that didnt work either.

---

### Post by konqueror7 on 2010-06-12
not directly the same OSes as yours, mine was Ubuntu, Fedora, and Vista. you just need to take note on what partition they are installed so later you can add it to GRUB. just better don'T install another bootloader.

---

### Post by MichealH on 2010-06-12
What are you saying? When you install it only boots Opensuse? If so do ```
sudo update-grub
``` in either a live CD or in OpenSuse itself.

---

### Post by MichealH on 2010-06-12
> **konqueror7 said:**
> not directly the same OSes as yours, mine was Ubuntu, Fedora, and Vista. you just need to take note on what partition they are installed so later you can add it to GRUB.

Or you do what I said above

---

### Post by grumpy.biatch on 2010-06-12
> **konqueror7 said:**
> not directly the same OSes as yours, mine was Ubuntu, Fedora, and Vista. you just need to take note on what partition they are installed so later you can add it to GRUB.


Right. If you can could you please provide Grub editing script post install.

---

### Post by MichealH on 2010-06-12
Yup make a .sh script with ```
sudo update-grub
``` in it and you're done.

---

### Post by grumpy.biatch on 2010-06-12
> **MichealH said:**
> What are you saying? When you install it only boots Opensuse? If so do ```
sudo update-grub
``` in either a live CD or in OpenSuse itself.


I need to know how I can edit the Grub entry in order to get 3 boot menus.

---

### Post by grumpy.biatch on 2010-06-12
> **MichealH said:**
> Yup make a .sh script with ```
sudo update-grub
``` in it and you're done.


Right, I will give it a go and get back tomorrow.

---

### Post by Elfy on 2010-06-12
I'd be inclined towards installing grub for the opensuse in it's partition. If update-grub fails to pick it up - I know that the os-prober script failed to include pclinuxos correctly and I ended up adding a custom entry to the buntu grub.

You can see if it will at least find it with 

```
sudo os-prober
```

(whether it works or not is a completely different kettle of fish.)

---

### Post by MichealH on 2010-06-12
> **grumpy.biatch said:**
> I need to know how I can edit the Grub entry in order to get 3 boot menus.

I mean, You dont need to. I really should of explained the command. sudo update-grub basically Updates your grub file for you. It finds the OS's and Lists them. It it is reccomended in my book when for example: I have just installed Win7 and now I need to boot into a live CD and type: "sudo update-grub".

---

### Post by grumpy.biatch on 2010-06-12
> **forestpiskie said:**
> I'd be inclined towards installing grub for the opensuse in it's partition. If update-grub fails to pick it up - I know that the os-prober script failed to include pclinuxos correctly and I ended up adding a custom entry to the buntu grub.

You can see if it will at least find it with 

```
sudo os-prober
```(whether it works or not is a completely different kettle of fish.)

Yeah, my guestimation is to edit the grub from Ubuntu and add Opensuse.

---

### Post by grumpy.biatch on 2010-06-12
> **MichealH said:**
> I mean, You dont need to. I really should of explained the command. sudo update-grub basically Updates your grub file for you. It finds the OS's and Lists them. It it is reccomended in my book when for example: I have just installed Win7 and now I need to boot into a live CD and type: "sudo update-grub".


That works for a dual boot but for triple boot it messes up.

---

### Post by MichealH on 2010-06-12
But, Opensuse should give you the option to install GRUB. Make sure it installs in /dev/sda (Or whatever root drive you have)

---

### Post by grumpy.biatch on 2010-06-12
> **MichealH said:**
> But, Opensuse should give you the option to install GRUB. Make sure it installs in /dev/sda (Or whatever root drive you have)


Well Opensuse will install its Grub in MBR and overwrite Ubuntu Grub. I know how to restore Ubuntu Grub but I need a script modification in order to add Opensuse (kde) in Ubuntu Grub.

---

### Post by oldfred on 2010-06-12
It looks like opensuse still uses grub legacy so installing it to the boot partition not MBR for opensuse would be the easiest way.

Then open 40_custom in Ubuntu and add a chainboot entry, adjust partition entries to suit:

gksudo gedit /etc/grub.d/40_custom

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

---

### Post by grumpy.biatch on 2010-06-12
> **oldfred said:**
> It looks like opensuse still uses grub legacy so installing it to the boot partition not MBR for opensuse would be the easiest way.

Then open 40_custom in Ubuntu and add a chainboot entry, adjust partition entries to suit:

gksudo gedit /etc/grub.d/40_custom

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}


Working on it atm. Let Opensuse install its Grub legacy 1.94 and I will then edit the Grub 2 with live cd.

---

### Post by MichealH on 2010-06-12
Yeah but If installed then... Oh yeah my bad It may work.

---

### Post by grumpy.biatch on 2010-06-12
> **MichealH said:**
> Yeah but If installed then... Oh yeah my bad It may work.


SUSE doesnt see Ubuntu on extended partition and wants to overwritre it.

Below is the geometry -

sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004557c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       34997   239167687+   7  HPFS/NTFS
/dev/sda3   *       34998       38913    31455081    5  Extended
/dev/sda5           34999       36303    10482412+  83  Linux
/dev/sda6           36304       36955     5237158+  82  Linux swap / Solaris

I have 15 GB empty space on extended partition, will like to fix SUSE in it.

---

### Post by MichealH on 2010-06-12
> **grumpy.biatch said:**
> SUSE doesnt see Ubuntu on extended partition and wants to overwritre it.

Below is the geometry -

sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004557c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       34997   239167687+   7  HPFS/NTFS
/dev/sda3   *       34998       38913    31455081    5  Extended
/dev/sda5           34999       36303    10482412+  83  Linux
/dev/sda6           36304       36955     5237158+  82  Linux swap / Solaris

I have 15 GB empty space on extended partition, will like to fix SUSE in it.

Do you know which one it is?

---

### Post by grumpy.biatch on 2010-06-12
> **MichealH said:**
> Do you know which one it is?

Yeah, it is sda7, formatted it to logical partition.

---

### Post by MichealH on 2010-06-12
> **grumpy.biatch said:**
> Yeah, it is sda7, formatted it to logical partition.

By formatted it means you *wiped* your drive?

---

### Post by grumpy.biatch on 2010-06-12
> **MichealH said:**
> By formatted it means you *wiped* your drive?


Nope, just formatted the partition on which I plan to install SUSE.

---

### Post by MichealH on 2010-06-12
So you have Your SUSE,Ubuntu and Windows Drive altogether?

---

### Post by grumpy.biatch on 2010-06-13
> **MichealH said:**
> So you have Your SUSE,Ubuntu and Windows Drive altogether?

tried second time but the SUSE wants to format Ubuntu partition and gives error.

---

### Post by MichealH on 2010-06-13
Mybe try and Back up and override Ubuntu then put Ubuntu on the drive it can only see? Is it because the new drive is ext2/3/4?

---

