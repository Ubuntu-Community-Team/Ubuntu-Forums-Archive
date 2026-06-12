---
title: "Please help me reduce my Grub menu entries"
date: 2010-02-06
forum: General Help
---

### Post by Donalb on 2010-02-06
Hi all,

I've asked this in a different way and gotten no response.

Sometimes I've realised I need to go back to basics to understand something, so appreciate any clarification on this.

It's not about HOW to edit the GRUB menus, but the content of the menu I don't understand.

Let me explain.

So yesterday we got 2.6.31.19.

Rebooting today I have 4 entries for the latest kernel,2.6.31.19,
4 for 2.6.31.18, 
and 2 each for 2.6.31.17 & .16.

Two for .16 & .17 because I already removed 2 each, using Synaptic.

I also understand I can remove .16 & .17 completely using Synaptic or edit GRUB to only show the current and last kernel or reduce the visible entries for each kernel.

for .19 I have
linux 2.6.31.19.generic-pae
linux 2.6.31.19.generic-pae (recovery)
linux 2.6.31.19.generic
linux 2.6.31.19.generic-(recovery)

Same for .18. For .17 & .16 I removed 2 each of those. I'll probably now remove 0.16 completely anyway.

My question:
What are the 4 different kernel images? How can determine which two I can remove?
My current vague understanding is these are processor specific (x86) and "Headers"? Am I completely wrong on this? What's the "Image" vs the "Headers"? I guess each kernel needs the headers, but why 2 of each for each release, therefore which can I remove?

The end questions here are;
How do I (an average user) know which one I should choose on start-up?
I currently (always) choose the first on the list. Once I understand WHICH entry I SHOULD use, then I can remove the others?

Again, thanks for any assistance here.

---

### Post by Nazrudin on 2010-02-06
I think I have the same question.  I'm taking a Linux class in college, and I've had no prior experience with this OS.  I resized my Windows 7 partition and installed the latest version of Ubuntu on a new partition created from the empty space on my drive.
 
The installation went fine, and when the GRUB boot menu appeared, I was able to choose between booting Ubuntu, booting Ubuntu in recovery mode, or running the windows boot loader to get to my Windows 7 installation.
 
After playing around in Ubuntu for a while, I soon discovered that it has an updater similar to windows update.  I ran it, and ended up downloading and installing roughly 40 updates.  I was prompted to restart, so I did.
 
When Grub loaded again, I was shocked and confused to see what appeared to be a 2nd version of ubuntu on my machine.  I could choose between windows boot loader, either of 2 versions of ubuntu, or either of 2 versions of ubuntu in recovery mode.
 
So did I update Ubuntu, or did I install a 2nd version and leave the origional intact?

---

### Post by smerral on 2010-02-06
Well I usually keep one previous kernel as a backup. Right now I have 19 and 17 (plus recovery modes). To get rid of the older ones (using 16 as an example) do:

sudo apt-get purge linux-image-2.6.31-16-generic

---

### Post by kareempharmacist on 2010-02-06
hi
sometimes after u update your system ubuntu installs new kernal not an entire opeating system just a small but very important part of it .After each kernal install two enteries in the grub menu are installed one for normal boot the other for recovery. Updating your kernal is very important .Any way you have to read about linux I recommend......

[http://wiki.linuxquestions.org/wiki/Main_Page](http://wiki.linuxquestions.org/wiki/Main_Page)

:p

---

### Post by faical117 on 2010-02-06
sudo apt-get purge linux-image-2.6.31-16-generic

don't forget this :  sudo update_grub
;)

---

### Post by 2hot6ft2 on 2010-02-06
> **Donalb said:**
> 
The end questions here are;
How do I (an average user) know which one I should choose on start-up?
I currently (always) choose the first on the list. Once I understand WHICH entry I SHOULD use, then I can remove the others?

Again, thanks for any assistance here.
Use the most current kernel (the one with the highest number)
Keep the next highest working kernel as a backup in case you have issues with the newest one.
Remove the older ones i.e. the rest.

---

### Post by Leppie on 2010-02-06
first of all, *you* are using 2 different types of kernel.
pae (Physical Address Extension) is to guarantee the usuability of 4+gb of memory. then there's the normal kernel which can handle up to 4gb of memory (video + ram combined). the pae kernel is installed by default for the 32bit server version. 64bit systems already support 4+gb memory without any extension.

furthermore you have recovery mode entries for all kernel versions. i would say it isn't necessary to have those as you can easily change the boot menu entry at boot time to enter recovery mode. with grub2 this is done by pressing the "e" key and then adding tthe letter "s" after the kernel options "ro quiet splash". pressing CTRL+x will boot it like that.

the linux image is the actual kernel you are using. the headers are required if you want to compile modules (like proprietary video card drivers) which are not found in the repositories.

you normally can safely remove older kernel versions from your system. however, i wouldn't recommend removing the 14 kernel from your system, as this is the default stock kernel and it should be the least likely to give issues. it's better to skip it in the menu, so you aren't presented with it at every boot, but you will still be able to boot using that kernel version if needed. if you're using grub2 and want to know how to "hide" the 14 kernel, let me know and i'll provide instructions.

you can remove older kernel versions using synaptic (System>Administration>Synaptic Package Manager). type the kernel version you would like to delete in the quick search box, something like 2.6.31-17. there normally are 3 packages installed for every kernel version, the image, the headers and the generic headers.

hope this helps

---

### Post by wangsuda on 2010-02-07
Removing old kernals is easy! First, find out which kernal you are using now. If you've done the latest update, then your kernal should be 2.6.31-19. All other kernals are old and can safely be removed. Here's how to do that:

1. Open Synaptic and click on the "Installed" option on your left.

2. In the search box, type in the kernal number you want to remove. MAKE SURE IT IS NOT YOUR CURRENT KERNAL!

3. Mark the old kernal elements for removal.

4. Click on apply.

You can also check out this thread [http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521) and specifically this post [http://ubuntuforums.org/showpost.php...50&postcount=8](http://ubuntuforums.org/showpost.php...50&postcount=8) for more detailed information.

---

### Post by Nazrudin on 2010-02-08
Thank you all for the helpful replies!  :D

---

### Post by scouser73 on 2010-02-08
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

