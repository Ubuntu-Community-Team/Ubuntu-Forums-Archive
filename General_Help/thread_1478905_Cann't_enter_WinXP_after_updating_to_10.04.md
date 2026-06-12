---
title: "Cann't enter WinXP after updating to 10.04"
date: 2010-05-10
forum: General Help
---

### Post by coldwind2010 on 2010-05-10
After Updating to Ubuntu 10.04, I cann't enter into Windows XP, even there is a option for Windows XP in the Grub menu. :(

I have tried the command " sudo grub-update", but it is useless. I just re-install my Windows XP. I can enter it again. However, I do a stupied thing again. I just update grub to a newer version, and then I cann#t enter XP again just like before.

What should I do to fix it?

Thank you in advance!

---

### Post by Mark Phelps on 2010-05-10
> **coldwind2010 said:**
> After Updating to Ubuntu 10.04, I cann't enter into Windows XP, even there is a option for Windows XP in the Grub menu. :(
Doesn't really tell us anything other than it doesn't work.  Some info on error messages or what you see on screen would help.

If you have a WinXP CD, you could boot into it, select command mode, and enter the commands fixboot and fixmbr.

---

### Post by pathfindermwd on 2010-05-10
what if one doesnt have the XP Cd, is there a download?

Thanks

---

### Post by pricetech on 2010-05-10
None that I'm aware of.  However, it doesn't have to be the original disk for the computer, so a loaner from a friend would allow you to run the commands.  Keep in mind that you'll overwrite grub so you'll need to fix it afterward.

---

### Post by pathfindermwd on 2010-05-10
> **pricetech said:**
> None that I'm aware of. However, it doesn't have to be the original disk for the computer, so a loaner from a friend would allow you to run the commands. Keep in mind that you'll overwrite grub so you'll need to fix it afterward.
 
yeah, I did the fixmbr and it didnt do anything.  So I went back in and did fixboot and then a quick fixmbr, now it says NTLDR is missing.  Is this where I need to fix grub.   How do I do that?
 
Thanks

---

### Post by pathfindermwd on 2010-05-10
and btw, yes the grub menu is now gone.

---

### Post by myjess on 2010-05-10
> **pathfindermwd said:**
> yeah, I did the fixmbr and it didnt do anything.  So I went back in and did fixboot and then a quick fixmbr, now it says NTLDR is missing.  Is this where I need to fix grub.   How do I do that?
 
Thanks

In lkucid update-grub didn't find my xp part si I added the details to /etc/grub.d/40_custom and then did update-grub.

menuentry "Windows" {
insmod ntfs
set root=(hd0,1)
chainloader +1
}

---

### Post by pathfindermwd on 2010-05-10
> **myjess said:**
> In lkucid update-grub didn't find my xp part si I added the details to /etc/grub.d/40_custom and then did update-grub.
 
menuentry "Windows" {
insmod ntfs
set root=(hd0,1)
chainloader +1
}
 
 
 
Huh?

---

### Post by coldwind2010 on 2010-05-11
Thank you very much!
I have read another thread and find a solution without Windows XP CD

Just try [http://sourceforge.net/apps/mediawik...ms:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

