---
title: "Ok to delete old linux files from /boot?"
date: 2010-03-08
forum: General Help
---

### Post by Lido on 2010-03-08
Update manager was giving me an error that there was not enough free space on /boot. I went in and deleted anything that had 31-14 or 31-15 in the file name (I'm running 2.6.31-19-generic). Will this cause any trouble? I didn't look at my grub file, but does it care if you remove things that it's pointing to that won't get used anyway? Thanks.

---

### Post by rnerwein on 2010-03-08
hi
id don't know what will happen when you remove old kernels or other stuff inside /boot because that 
stuff is still present in the system data bases. you should better use the command:
apt-get remove --purge your_old_kernel 
ciao

---

### Post by bumanie on 2010-03-08
Go in to synaptic and type linux-image and completely remove the kernels you no longer want - take note: it is always a good idea to keep one known 'old' working kernel. Then in synaptic type linux-headers and completely remove them, ensuring they are the same as the images you have removed. Then do > sudo update-grub in terminal. That should give you extra space - each kernel takes up a little over 110mb.

---

### Post by darolu on 2010-03-08
Yes you can, but I would strongly recommend to use Synaptic to do it.
Open Synaptic and search for "linux-image", mark the ones you don't need to be uninstalled and then hit apply; you can also uninstall the headers you no longer need.
Keeping one old kernel that has proven to work, along with the latest, is adviced.

---

### Post by dcstar on 2010-03-08
> **bumanie said:**
> Go in to synaptic and type linux-image and completely remove the kernels you no longer want - take note: it is always a good idea to keep one known 'old' working kernel. Then in synaptic type linux-headers and completely remove them, ensuring they are the same as the images you have removed. Then do  in terminal. That should give you extra space - each kernel takes up a little over 110mb.

There is no need to manually run update-grub as that is part of any kernel install/removal process using the proper tools like Synaptic.

As well, do not "quote" code as text in these forums - anything in quotes is removed.

---

### Post by scouser73 on 2010-03-08
Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

### Post by Lido on 2010-03-08
Actually, I did use synaptic to remove my old kernals with "remove completely" or whatever, but they were still left in /boot for some reason and that's where I needed more space. I should probably just enlarge that partition, but I was looking for a quick fix. Hopefully not dangerous.

---

### Post by Keith_Beef on 2010-05-01
> **Lido said:**
> Actually, I did use synaptic to remove my old kernals with "remove completely" or whatever, but they were still left in /boot for some reason and that's where I needed more space. I should probably just enlarge that partition, but I was looking for a quick fix. Hopefully not dangerous.

I also used Synaptic to remove old kernels, but found that they are still left in /boot, taking up space.

I still have about 4 MB left, but I wonder why Synaptic didn't get rid of the files below.

```
abi-2.6.28-16-generic
config-2.6.28-16-generic
initrd.img-2.6.28-16-generic
System.map-2.6.28-16-generic
vmcoreinfo-2.6.28-16-generic
vmlinuz-2.6.28-16-generic
```

K.

---

### Post by geoffreymatthews on 2011-08-01
I have the same problem. There's a ton of these files lying around:

abi-2*
config-2*
initrd.img-2*
System.map-2*
vmcoreinfo-2*
vmlinux-2*

But synpatic shows only the latest linux-image as installed. The others don't appear at all. How to do a clean uninstall?

---

### Post by DWizzle on 2012-01-23
Being a new convert to anything besides a windows OS, I wasn't sure what to do when I received a message stating that I had low disk space in /boot.  I used the instructions from scouser, as they were written, and it cleared the problem up pronto.

Thanks scouser.

> **scouser73 said:**
> Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR=Red]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

