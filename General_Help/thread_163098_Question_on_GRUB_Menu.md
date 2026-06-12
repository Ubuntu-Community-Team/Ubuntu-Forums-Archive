---
title: "Question on GRUB Menu"
date: 2006-04-20
forum: General Help
---

### Post by livinlinkin on 2006-04-20
Hi,

I have a dual boot laptop with Winxp and Ubuntu. I realize after updating that there are many Ubuntu kernels listed (excluding recovery). However, since I will never use those old, outdated OSes, and I find them aesthetically unpleasing, is there any way I can remove them to leave only to leave only the usual four (I believe they were Ubuntu, recovery, memory test?, and Winxp)? Sorry if this sounds odd. Thanks in advance. :)

---

### Post by krusbjorn on 2006-04-20
You can remove the entries from the /boot/grub/menu.lst file:

> sudo gedit /boot/grub/menu.lst

It's pretty self-explanatory, but if you need further instructions just ask :)

---

