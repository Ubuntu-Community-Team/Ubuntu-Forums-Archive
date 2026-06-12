---
title: "Grub won't load"
date: 2010-06-28
forum: General Help
---

### Post by steve296 on 2010-06-28
Hi,

I installed ubuntu 10.04 on a hard disk where there was 9.10 originally, and now I can't get it to boot, mainly because of grub.

After my first attempt at installing, I rebooted, and the grub-rescue> (or something like that) command line came in, saying error 15 to everything I threw at it. From there I switched between liveCD and the grub command line dozens of times, trying out everything I could find on these forums. I had mixed results, for example at first on liveCD it couldn't find grub at all - when i installed it, it wouldn't find /boot/grub/stage1. With chroot it worked after a couple of attempts, and after grub-install it could locate hd(1,0), root() and setup() worked too, I rebooted again, and still the grub command line came in (with no error messages whatsoever, just the introductory text and 'grub>' ).

Reinstalled. After that, no grub command line, just this:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 15

I've been screwing with this for 5 hrs since I woke up today, pretty pissed off that something like version numbering can turn into such a roadblock.

Oh, did I mention that I have no /boot/grub/stage1 nor /boot/grub/menu.lst ?

---

### Post by oldfred on 2010-06-28
It sounds like you have old grub in the MBR but grub2? Error 15 often is where both grubs are interfering with each other.

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by steve296 on 2010-06-29
Ehh, sorry for writing in an angry mood, happens to me often. Yesterday (late night, mind you) I finally solved the problem by reinstalling GRUB (found it here [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") - praised be the documentation). And only today did it occur to me to mark this thread solved.

Answering your question, and remembering from another thread (maybe 2010 feb or so?) the same symptoms, yes, I think that was the case. Mind you, I'm going to check that script, if for nothing else, then to satisfy my curiosity. Thank you for helping me anyways, and please excuse me of my manners.

Did I mention that Ubuntu's working again for me? cheers :mrgreen:

EDIT: The hell?

Wow, GRUB is installed to sda too, where the spawn of **M**ephi**$**to resides. I wonder how it got there...
I may have installed it there accidentally yesterday when I wanted to restore GRUB, I may have typed sda in stead of sdb...

---

