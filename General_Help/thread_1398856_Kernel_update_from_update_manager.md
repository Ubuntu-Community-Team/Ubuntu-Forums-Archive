---
title: "Kernel update from update manager"
date: 2010-02-05
forum: General Help
---

### Post by Mr Nemo on 2010-02-05
I received an update to my kernel through the update manager (updated from ****.32.14 to ****.32.19, or something like that) but grub still shows the old kernel and not the updated one. Was this not a full kernel update and only a patch or do I have to do something to use the new kernel? I'm new bear with me if this doesn't make any sense.

---

### Post by tom4everitt on 2010-02-05
Don't worry, you make sense :)

Check your /boot directory. (Type: ls /boot in a terminal, or use your file manager.) Ubuntu kernels are usually called something like:

vmlinuz-2.6.31-11-generic

---

### Post by wojox on 2010-02-05
Open your terminal and run:

```
sudo update-grub
```

---

### Post by Mr Nemo on 2010-02-05
Here's the whole list of what showed up. .31-19 is what I just had an update for, but grub only shows .31-14.


abi-2.6.31-14-generic 
abi-2.6.31-15-generic                    
abi-2.6.31-16-generic
abi-2.6.31-17-generic 
abi-2.6.31-19-generic
config-2.6.31-14-generic             
config-2.6.31-15-generic 
config-2.6.31-16-generic 
config-2.6.31-17-generic 
config-2.6.31-19-generic 
grub 
initrd.img-2.6.31-14-generic 
initrd.img-2.6.31-15-generic 
initrd.img-2.6.31-16-generic 
initrd.img-2.6.31-17-generic 
initrd.img-2.6.31-19-generic 
memtest86+.bin         
System.map-2.6.31-14-generic
System.map-2.6.31-15-generic
System.map-2.6.31-16-generic
System.map-2.6.31-17-generic
System.map-2.6.31-19-generic
vmcoreinfo-2.6.31-14-generic
vmcoreinfo-2.6.31-15-generic
vmcoreinfo-2.6.31-16-generic
vmcoreinfo-2.6.31-17-generic
vmcoreinfo-2.6.31-19-generic
vmlinuz-2.6.31-14-generic
vmlinuz-2.6.31-15-generic
vmlinuz-2.6.31-16-generic
vmlinuz-2.6.31-17-generic
vmlinuz-2.6.31-19-generic

---

### Post by Mr Nemo on 2010-02-05
> **wojox said:**
> Open your terminal and run:

```
sudo update-grub
```

I did that, it didn't seem to have any effect.

---

### Post by rnerwein on 2010-02-05
hi
try ( but first with your oldest kernel 2.6.31-14-generic because i have never used this command before - but it should work)

sudo apt-get remove --purge 2.6.32-14-generic
sudo update-grub

think this will answer your question
ciao

---

### Post by lotharmat on 2010-02-05
The best way to remove older kernels I've found is to do it through Synaptic Package Manager:

Search in SPM for 2.6.31-xx

Where xx is the kernel you wish to remove.

This will remove it and then automatically run update-grub for you.

BTW - I got the 2.6.31-19 today what happened to 18?

I went from 16->17->19..

Strange..

---

### Post by Mr Nemo on 2010-02-05
> **lotharmat said:**
> 

BTW - I got the 2.6.31-19 today what happened to 18?

I went from 16->17->19..

Strange..


I thought the exact same thing...

---

### Post by Mr Nemo on 2010-02-05
Ok, so I deleted the oldest kernel, and I guess it didn't automatically run update-grub since I keep getting an error message that say I have no kernel. ATM I am running off of the liveCD. Can I restore/fix the kernel?

---

### Post by saif_held on 2010-02-05
> **lotharmat said:**
> 
BTW - I got the 2.6.31-19 today what happened to 18?

I went from 16->17->19..

Strange..

That's really weird because I went from 16 to 19 without missing any in between...

---

### Post by tom4everitt on 2010-02-05
> **rnerwein said:**
> hi
try ( but first with your oldest kernel 2.6.31-14-generic because i have never used this command before - but it should work)

sudo apt-get remove --purge 2.6.32-14-generic
sudo update-grub

think this will answer your question
ciao

Exactly how would removing his only working kernel make things work?

---

### Post by tom4everitt on 2010-02-05
> **Mr Nemo said:**
> Ok, so I deleted the oldest kernel, and I guess it didn't automatically run update-grub since I keep getting an error message that say I have no kernel. ATM I am running off of the liveCD. Can I restore/fix the kernel?

Sorry to say this, but it was a completely idiotic advice you got telling you to remove your only working kernel that was recognised by grub. 

It still looks like you have working kernels however, so you could try to add a manual entry for one of them to you /boot/grub/grub.cfg

Here's a quick guide how to that (i'm going to assume you have installed ubuntu to /dev/sda1):

1. Boot from live cd.
2. Mount your ubuntu system:
2.1 sudo su
2.2 mkdir /foo
2.3 mount /dev/sda1 /foo

3. cd /foo/boot/grub
4. chmod +w grub.cfg
5. Add an entry for a kernel:
5.1 gedit grub.cfg
5.1 find the other menuentries and add one looking like this:

menuentry "Manual Ubuntu" {
   set root=(hd0,1)
   linux /boot/vmlinuz-2.6.31-19-generic ro quiet splash
   initrd /boot/initrd.img-2.6.31-19-generic
}

6. save and reboot.

Sorry about this. If you think it sounds way too complicated you can just reinstall the system.

EDIT:
Also, if you get it working, you should add that same entry to /etc/grub.d/40_custom

---

### Post by Jackzor on 2010-02-05
> **tom4everitt said:**
> Exactly how would removing his only working kernel make things work?

I think the guy misread the thread. I'm betting he read parts of it and *Assumed* that the OP wanted to remove it.

I sure hope that when I get help from people they completely understand what the problem is and they don't just assume they know whats going on though.

---

### Post by tom4everitt on 2010-02-05
Actually, this is way simpler:

boot from live cd and run:
```

sudo su
mkdir -p /foo && mount /dev/sda1 /foo && chroot /foo && sudo apt-get install linux-image-2.6.31-14-generic 
update-grub

```

which should just get you your old working kernel back.

---

### Post by Mr Nemo on 2010-02-05
Ya removing the kernel didn't work out at all, but I was able to reload the working kernel pretty easily, so no harm done. In the process of reading the other advice....Ill get back to you. Thanks for your help so far.

Edit: Just in case any wants to know I booted into grub, changed which kernel ubuntu booted from in the grub menu and then reloaded the older working kernel.

---

### Post by Mr Nemo on 2010-02-05
Ok so I was able to change grub so it boots from the newest kernel (was all of that worth it? I mean I assume since they sent me an update, it must be better in some way...right?) apparently all I had to do was manually edit my 40_custom file in grub.d. Although I never thought of this since someone told me I had to create a file for a custom boot order that contained a number below 10 so grub would use that file. Editing the file, which I called 6_custom (or 06_custom - I don't feel like checking), did absolutely nothing as far as I know. Anyway thanks for the help.

---

### Post by scouser73 on 2010-02-05
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

### Post by Mr Nemo on 2010-02-05
The new kernels on my system never made it to the grub boot menu (because I'm using a custom boot menu?), so I was only able to use the one that was first installed on this system.

---

### Post by gysheng on 2010-02-06
I meet same question.
you can try:
sudo apt-get install linux-image-2.6.31-19-generic

---

### Post by tom4everitt on 2010-02-06
> **Mr Nemo said:**
> The new kernels on my system never made it to the grub boot menu (because I'm using a custom boot menu?), so I was only able to use the one that was first installed on this system.

Okay, that makes a lot of sense. I just assumed you were using the automatic :)

---

