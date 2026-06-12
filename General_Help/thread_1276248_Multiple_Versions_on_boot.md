---
title: "Multiple Versions on boot?"
date: 2009-09-26
forum: General Help
---

### Post by Mercenary(FH) on 2009-09-26
So this may and probably is a nublet question.
but I recently updated a bunch of stuff (i installed 9.04 from the cd) and then did some updates etc. then it restarted.

now in my bootup screen it had like.......4 different things

1 is like ubuntu 9.15 blah blah blah
then XXX diagnositic.

but right below it is ubuntu 9.11 or something with the diagnostic of the same version below it?

why do I have 2 kernals or w/e?
isn't it like a safety net kinda thing in case one breaks?

And is it gonna do that EVERY time I update stuff??
also. how do i get rid of the old one?
im not sure of the exact versions but the one on top is the highest number, or newest one.

thx :)

---

### Post by Marflus on 2009-09-26
Those are different kernel versions, yes. They're not auto removed when upgraded. You can remove them manually, though: [http://www.foogazi.com/2008/07/02/quickzi-how-to-remove-older-kernels-from-ubuntu/](http://www.foogazi.com/2008/07/02/quickzi-how-to-remove-older-kernels-from-ubuntu/).

Kernel upgrades don't happen too often, though, so you needn't worry about filling your bootlist with the things just yet.

---

### Post by oldfred on 2009-09-27
You can download startupmanager from synaptic and set the number of kernels to show to 2. You want one old one just incase the new one has issues.

This will not delete the old kernels from your system, just not display them.  You still need to do the housecleaning as marflus suggested if you want.

---

### Post by scouser73 on 2009-09-27
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

### Post by arnab_das on 2009-09-27
btw what if someone uses windows alongwith ubuntu and wants the windows option in the dual boot menu to be the second. how do i do that? in windows it is possible to do that by checking out properties etc, dont know the ubuntu way. plz help.

---

### Post by oldfred on 2009-09-27
arnab_das you should start a new thread, so that there is  no confusion with answers to your question and the original poster.

You can not have it second. First or last are the choices as everytime a kernel is updated everything in menu.lst between automagic list is updated:

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
[COLOR=Red]If you want it first put it here or last at the end.[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST

to edit:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

---

