---
title: "What the **** is going on?"
date: 2009-11-15
forum: General Help
---

### Post by vcj88 on 2009-11-15
I've been using 9.10 since they released the stable version and I saw tonight there were some security upgrades so I clicked on them and started the download and installation. After it finished, my network-manager disappears completely. Not just the icon, but the newtork-manager itself. So, the idiot being me thought "maybe it just needs to reboot" . So i went into terminal and typed in sudo shutdown -r now and then it went through the normal reboot phase until it got to a screen where it says

"Boot from (hd0, 0) ext3 somerandomnumbers

Error 15: File not found

Press any key to continue"

So I press a key and it sends me to a screen with 5 options, 4 of which are ubuntu9.10 and the kernel and two of them have recovery mode in paranthesis behind them. Not of those for take me anywhere, the just send me back to the File not found screen. The 5th option is ubuntu9.10 memtest86+ and it goes into what I'm assuming is a memory test(?)

So yeah. Any suggestions? I have about a year's worth of research on this POS and only partially backed up (I know, stupid) but is there anyway to salvage the memory?

Thanks ahead of time.

---

### Post by jeb800e on 2009-11-15
boot into one of those older kernels, or you may want to boot into the memtest just to make sure there is nothing wrong with your memory. If your computer won't reboot, do the REISUB technique. (You can find easily how to do REISUB by searching it up on Google.)

Try to get a livecd from someone or burn it yourself from another PC. Restart your broken one with the livecd. Run the FSCK utility inside the terminal once your load the livecd.

---

### Post by CharlesA on 2009-11-15
Booting off a LiveCD and running fsck would be the best thing.

Personally I'd boot off a LiveCD and pull the files off  to a USB drive or network server before messing with it. that way you won't lose more data if it isn't fixable.

I could be wrong, but doesn't that error mean something is wrong with GRUB?

---

### Post by HuaiDan on 2009-11-15
Ah, the joys of linux coming of age. 

Sounds like you messed up your grub, which is something every adventuresome linux user does from time to time. Get a pen and paper and write this down, without doubt you'll need it again someday in the indefinite future.


Boot from cd.

Open terminal.

Type these commands:

#sudo grub

#grub>find /boot/grub/stage1

Grub will find the boot sector and tell you which drive it is located on.
Use this info for

#grub>root (hd0,0)

Replace the (hd0,0) by your boot partition number. If your Ubuntu is installed in the second partition, then change it to (hd0,1)

then

#grub>setup (hd0)
#grub>quit

Remove CD and reboot your system. You should be able to access the Grub bootloader now

---

### Post by vcj88 on 2009-11-15
> **HuaiDan said:**
> Ah, the joys of linux coming of age. 

Sounds like you messed up your grub, which is something every adventuresome linux user does from time to time. Get a pen and paper and write this down, without doubt you'll need it again someday in the indefinite future.


Boot from cd.

Open terminal.

Type these commands:

#sudo grub

#grub>find /boot/grub/stage1

Grub will find the boot sector and tell you which drive it is located on.
Use this info for

#grub>root (hd0,0)

Replace the (hd0,0) by your boot partition number. If your Ubuntu is installed in the second partition, then change it to (hd0,1)

then

#grub>setup (hd0)
#grub>quit

Remove CD and reboot your system. You should be able to access the Grub bootloader now

Thanks for the reply, it appears on the livecd that grub isn't installed. I try sudo grub and it says command not found then I try just grub without sudo and it gives me a think telling me to get it with apt-get.

 However, while in boot mode without the livecd where I can only go to the memtest, I can navigate to a grub shell. Can I just use this?

Thanks.

---

### Post by HuaiDan on 2009-11-15
Now I'm not so sure. Grub2 complicates things, so my last suggestion is probably barking up the wrong tree.  I haven't done my reading on grub2, sorry. I had to check which version I had by going into synaptic.

[http://unpluggable.com/?p=294](http://unpluggable.com/?p=294)


This article in this link recommends using grub1 to fix a hosed grub2.

---

### Post by vcj88 on 2009-11-15
> **HuaiDan said:**
> Now I'm not so sure. Grub2 complicates things, so my last suggestion is probably barking up the wrong tree.  I haven't done my reading on grub2, sorry. I had to check which version I had by going into synaptic.

[http://unpluggable.com/?p=294](http://unpluggable.com/?p=294)


This article in this link recommends using grub1 to fix a hosed grub2.

Ehh I had most of backed up, just did a fresh install with 9.04. Honestly I've felt like Ubuntu has been taking steps back with the compatibility on my machines since 8.04. But thats probably just because the machines themselves are getting older. Thanks anyways.

---

