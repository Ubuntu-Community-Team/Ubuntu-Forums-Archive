---
title: "An Ubuntu Startup Problem?"
date: 2009-09-13
forum: General Help
---

### Post by rocket16 on 2009-09-13
[SIZE="4"][FONT="Comic Sans MS"]Hello to all. I have a Compaq Desktop Computer, with Windows Vista and Ubuntu 9.04 Installed. Ubuntu 9.04 is installed via Wubi. Now, everything was going fine, but just today, when I try to load Ubuntu, it shows that "Minimal Grub-like editing is supported". I realized the proble, that is The Grub bootloader is not found. But when I opened the Bootloader file, that is menu.lst in Windows (using Notepad), there was no problem. So, where can I get to repair the Gurb? Or is there a way to replace the faulty Grub with a new version of Grub? If so, where can I get the file to be downloaded?[/FONT][/SIZE]

---

### Post by harrismh777 on 2009-09-13
grub may be downloaded using the synaptic package manager...

grub 0.97-29ubuntu53 

The GRand Unified Bootloader package can be downloaded as a tarball also, but...

... probably the best solution here is to reinstall ubuntu.   

How, may I ask, did you clobber grub?  Did you clobber anything else in the process?  Does wubi have issues? 

Why do you not simply dual boot windows and ubuntu... or better yet, just dump windows and install ubuntu stand-alone?

---

### Post by rocket16 on 2009-09-13
I did use Wubi, because it frees us from all troubles related to ext3 partion. I have not yet installed Ubuntu to NTFS Partition. So, I used Grub.

---

