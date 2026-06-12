---
title: "WUBI install 10.04 problem"
date: 2010-04-30
forum: General Help
---

### Post by WatTwo on 2010-04-30
Well I just tried doing a WUBI install of the new version, it installed fine, then my pc restarted.  Had the choice of windows 7 and ubuntu (as it should)

selected ubuntu, grub came up and the only choice there is, is the windows boot loader.

Goes right back to the first selection.


help?

---

### Post by Coldfirex on 2010-05-01
I have this exact same issue.  Wubi with Ubuntu 10.04 on Windows 7 Professional 64 bit (UAC disabled).  Any ideas?

---

### Post by dino99 on 2010-05-01
why not a real install ?

ubuntu into a windows file  :lolflag:

better to run it with virtualbox

---

### Post by WatTwo on 2010-05-01
well the only reason im doing a wubi install is because this version just came out.


I'm not  doing a full until the bugs and sorted out.

But yeah.. i still have this problem, any help?

---

### Post by Mark Phelps on 2010-05-01
Go to the Installation forum and read through the posts on Testing Wubi 10.04.  They have some fixes posted for some of the problems.

---

### Post by Artstanding on 2010-05-07
Last reply could have been more specific....

Echoing the same problem. Previous Wubi installation went flawlessly and worked fine. Tried to upgrade to 10.04 using standard upgrade menu option in Ubuntu. Upgrade failed (froze midway through the process). Decided easiest option as a fresh Wubi installation. Uninstalled Wubi through 'uninstall' file in /ubuntu directory. 

Wubi installation SEEMED to go OK, but after rebooting the Windows Boot Manager gave me the correct 2 choices: Vista and Ubuntu. Selected Ubuntu, but then GRUB screen gave me no Linux kernel options (as it did on previous installation), but instead gave me just the Windows option ... which brought me back again the the Boot Manager screen.

Vista boots fine; and I can run a Live CD OK.

I'm wondering if the Boot Manager screen is actually a leftover from the prior Wubi install.

---

### Post by RedRaider1863 on 2010-06-03
Same problem here.  Anybody figure out a solution?

---

### Post by Toto Leung on 2010-06-04
Same problem here... Waiting for the solution:mad:

---

### Post by treanorj on 2010-06-23
Hi all,

I was having the same problem until this morning. I had uninstalled and reinstalled Wubi due to other issues. I re-downloaded the installer and then I had problems (second download on 21/06/10). After uninstalling again, I used the original installer (24/05/10) and Ubuntu starts up as normal now. Version numbers are the exact same in both and the size is the exact same in both but using the original installer has solved the issue for me. 

Hope it helps anyone

---

