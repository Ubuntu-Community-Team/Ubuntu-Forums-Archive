---
title: "grub"
date: 2009-09-11
forum: General Help
---

### Post by aman25292 on 2009-09-11
i have window xp and ubuntu 9.04. I reinstalled xp and the grub menu discontinued to appear. how can it reapper ?

---

### Post by ronparent on 2009-09-11
The xp reinstall overwrote the grub code in the MBR. You merely have to setup grub again. Boot from a live cd and open a terminal. From within the terminal enter this series of commands:

[B]sudo grub

find /boot/grub/stage1[/B]

Use the output of the find as follows (x and y are each probably 0 but write in whatever you get):

[B]root (hd,x,y)
setup (hdx)[/B]

Your grub MBR should now be restored and everything working as it should. Good luck.

---

### Post by chinmaya_n on 2009-09-11
See this page... 
[http://chinmaya_n.hyperphp.com/node/4](http://chinmaya_n.hyperphp.com/node/4)

Hope its clearly explains you!!

---

### Post by briantoumbs on 2009-09-11
Burn Super Grub Disk and boot from it. 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

And the How to 
[http://www.supergrubdisk.org/w/index.php5?title=Howto_Fix_Grub](http://www.supergrubdisk.org/w/index.php5?title=Howto_Fix_Grub)

---

