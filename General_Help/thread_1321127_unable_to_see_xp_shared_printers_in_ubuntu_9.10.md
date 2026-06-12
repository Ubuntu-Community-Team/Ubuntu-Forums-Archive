---
title: "unable to see xp shared printers in ubuntu 9.10"
date: 2009-11-09
forum: General Help
---

### Post by User195 on 2009-11-09
I am new to Ubuntu so here goes.....
 I just installed 9.10 and would like to print to my printers that are shared on an XP machine. All the XP machines can print no problem. To start I goto printing in the System--Adminisration and click new. It searches for computers and I click network printers, then Windows printers via samba, then browse. In the small window I can see my network,the other XP machines and the computer the printers are connected to. I then click this computer but cannot see the printers (2) both HP's.
 I am new to Linux, am I missing something, does something need to be installed. Please help
 Thanks

---

### Post by nateperson on 2009-11-09
I had a similar issue the other day, had to install Print Services for Unix [http://technet.microsoft.com/en-us/library/bb457002.aspx]("http://technet.microsoft.com/en-us/library/bb457002.aspx") on my XP box in order to be able to see the printers from Linux...

---

### Post by CrusaderAD on 2009-11-09
Does your printer have an ethernet card? If so, plug it into your router and map the printer via it's IP. This has always worked for me.

---

### Post by ST3ALTHPSYCH0 on 2009-11-09
I had to do it the hard way with 9.10. Open your printers directory in the Control Panel. Id make sure to name your printer without spaces, but that's just because I don't know how to put spaces in the name in *buntu. Open printers>new>printer. Select "Windows Printer via Samba. In the address line enter your printer's name in this format: workgroup/computername/printername. Now click verify to make sure everything's hunky-dory.

---

### Post by User195 on 2009-11-12
> **ST3ALTHPSYCH0 said:**
> I had to do it the hard way with 9.10. Open your printers directory in the Control Panel. Id make sure to name your printer without spaces, but that's just because I don't know how to put spaces in the name in *buntu. Open printers>new>printer. Select "Windows Printer via Samba. In the address line enter your printer's name in this format: workgroup/computername/printername. Now click verify to make sure everything's hunky-dory.
 
That's for your suggestion ST3ALTHPSYCH0. I took the spaces out of the printer share name and both printers showed up right away.
 
I guess the saying "To close to the forest to see the trees" rings true.
 
Thanks again ST3ALTHPSYCH0.

---

### Post by ST3ALTHPSYCH0 on 2009-11-13
No problem. Any time I spend days figuring something out, I spam the boards with my solution. If I help one person I'm happy. And trust me, we all have those same situations with that blasted forest. Sometimes I feel as though I spend time cutting down the forest b/c it's between me and the trees!

---

### Post by CrusaderAD on 2009-11-13
> **ST3ALTHPSYCH0 said:**
> No problem. Any time I spend days figuring something out, I spam the boards with my solution. If I help one person I'm happy. And trust me, we all have those same situations with that blasted forest. Sometimes I feel as though I spend time cutting down the forest b/c it's between me and the trees!

Good stuff. :)

---

