---
title: "require urgent help!!"
date: 2009-07-09
forum: General Help
---

### Post by becoolpal on 2009-07-09
There  wa a routine check up of my files when i started my computer & following error was reported

/dev/sda6 : unexpexted inconsistency :run fsck manually(without option -a or -p)

fsck died with exit status 4

Please tell me how should i do it manually?Is it a major problem?

---

### Post by HermanAB on 2009-07-09
It certainly is a major problem.  However, sda6 is probably not your boot partition - probably the /home partition.  The issue is that you cannot run fsck on a mounted partition.

So you can likely boot into single user mode and then run fsck (since in that mode it won't mount /home).  Otherwise, you need to boot off a CDROM.

'Hope that helps!

---

### Post by becoolpal on 2009-07-09
Please tell me how to run fsck manually

---

### Post by prem1er on 2009-07-09
> **HermanAB said:**
> It certainly is a major problem.  However, sda6 is probably not your boot partition - probably the /home partition.  The issue is that you cannot run fsck on a mounted partition.

So you can likely boot into single user mode and then run fsck (since in that mode it won't mount /home).  Otherwise, you need to boot off a CDROM.

'Hope that helps!

He just explained why and told you how to do it.  Boot into single user mode from grub.
1. Highlight the kernel you are going to boot.
2. Hit 'e' to edit the selection.
3. Highlight the line with Kernel.
4. Hit 'e' again.
5. Go to the end of that line and enter the letter 'S' for single user.
6. Run fsck when it boots.

---

