---
title: "How do I switch from grub-pc to grub?"
date: 2010-06-18
forum: General Help
---

### Post by mrwhoohoo on 2010-06-18
I need to switch from booting via grub-pc to grub (easier to edit O/S boot options). I know I can just select grub and deselect grub-pc via Synaptic Package Manager.

Is that sufficient or do I have to do anything else? 

Are there any precautions I should take before doing this?

I have a dual boot installation of XP and Xubuntu 9.10.

Thanks for your attention.

Steve

---

### Post by wilee-nilee on 2010-06-18
> **mrwhoohoo said:**
> I need to switch from booting via grub-pc to grub (easier to edit O/S boot options). I know I can just select grub and deselect grub-pc via Synaptic Package Manager.

Is that sufficient or do I have to do anything else? 

Are there any precautions I should take before doing this?

I have a dual boot installation of XP and Xubuntu 9.10.

Thanks for your attention.

Steve

Removing grub2 from synaptic doesn't remove the grub.cfg files and other links. darkod has a thread on this, and if not done right will make the setup really convoluted and possibly borked without some specialized help, at the least

You might consider that in actuality grub2 is easier to use if you understand it, and post your problems and the bootscript in my sig and see if at the least you can get some help in what ever your decision is.

---

### Post by oldfred on 2010-06-18
Ok it is different and you do not edit just one file, but that one menu.lst included a lot of things everyone ignored or screwed up and still had issues. I did not find it difficult to copy my windows entry to 40_custom and edit at will.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

---

