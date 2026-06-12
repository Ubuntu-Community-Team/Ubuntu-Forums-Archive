---
title: "Ubuntu crashed after update (twice!)"
date: 2010-09-30
forum: General Help
---

### Post by %zqMOA$@U97bJ£&amp; on 2010-09-30
Hello.

(sorry for my English)

I've installed Xubuntu 9.10. Then I've updated it with packages from
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
Than Xubuntu crashed - after restart and loading desktop there was no reaction to mouse or keyboard and message "HAL deamon is not started". I gived up and installed system again.

This time I've used Ubuntu 10.04.1 LTS ISO image. I've installed WINE, Kadu, Firefox, ubuntu-restricted-extras, NVIDIA Drivers (ver. 185) and everything was ok. I've turned pc off. This morning Ubuntu stopped during boot - black screen and flashing underscore on left top corner. In recovery mode booting stopped after mounting swap.

I have started Avira Rescue CD and formated swap partition - nothing changed.
I have started ARCD once again, used chroot and made this: sudo apt-get upgrade - noting changed.
I have edited Grub lines during boot - removed 2 lines at the begining - first was to log fail start, secont was something about EXT2 - but I'm using EXT3 with journal! Booting went further - graphic mode was on, but Ubuntu still crashed when loading /udev/rules.d/z80_user.rule (or something like this), and 3 more error lines - something about "error code 4".

Now I have installed Ubuntu 10.04.1 once again. But...

Can be this coused by NVIDIA driver? 
Anyone else had similar problems?
Maybe new kernel has problem with old hardware?

I'm working on Asus M2N SE MX Plus (integrated GF 6150SE), AMD X2 4400+, Seagate 320GB (SATA2). Windows works ok so hardware should be ok.

I know, that I should give exac error codes/names, but I didn't write it down. If system fails again, I will give you more info about it.

---

### Post by andrewthomas on 2010-09-30
> **ULLISSES said:**
> 

I have started Avira Rescue CD and formated swap partition - nothing changed.

For one, when you format the swap partition it changes the UUID.   
You will have to edit your /etc/fstab and change the UUID of your swap partition.

You can find out the new UUID using 
```
sudo blkid
```There is more information here.

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
> **ULLISSES said:**
> 
Can be this coused by NVIDIA driver? Yes.
```
sudo apt-get update && sudo apt-get nvidia-current
```

---

### Post by %zqMOA$@U97bJ£&amp; on 2010-10-01
Thanks for UUID tip.

In current installation everything seems to be working. I've used "build-in" repo-base - no launchpad sources.

Now NVIDIA drivers work well - there is 100Hz @ 1024x768 in NVIDIA panel - for the first time since I'm testing Ubuntu! In all other version there was: 60, 65, 67, 70, 72 only with 1024x768.

There are 2 more problems:
1. [Backspace] doesn't work in Firefox 3.6.10 (it should give: history.back). It should be that way on Ubuntu or I must change settings to get it working?
2. When batteries in my wireless mouse went out system freezed - no reaction to mouse or keyboard (even there was no reaction to "Power" on the case). It's coincidence or common issue? It's Logitech MX600.

If above problems should have separate threats (forum rules etc), please let me now - I'll fix it.

---

### Post by andrewthomas on 2010-10-01
I would mark this thread as solved and start a new thread for each different issue.

---

### Post by %zqMOA$@U97bJ£&amp; on 2010-10-01
Thanks. I'll do that.

BTW:
[Backspace] in Firefox can be fixed in 10 seconds:
> Type “about:config” in the address bar of Firefox and press Enter.
`Filter` for ‘browser.backspace_action’ and change its value to 0 (zero).
Solution found after typing "backspace firefox" in Google ;]
About "wireless mouse ubuntu freeze" Google also has something to say - I'll find out.

Marked as SOLVED.

---

