---
title: "STUCK IN GRUB...please help"
date: 2010-02-08
forum: General Help
---

### Post by IchBinWamphyri on 2010-02-08
okay, so im running win7 and ubuntu 9.10 on a dual boot and everythings been running fine for like 2months since i got them, last night i shut my pc down as usual. when i woke up i turned on the computer and selected ubuntu as my OS i got this :

                                      GNU GRUB VERIZON 1.97~BETA4
[ Minimal BASH-like line editing is supported. For the first work, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>

and this is where i am stuck i dont know where i can go from here execpt windows.... and i loathe windows, please any help guys?

---

### Post by Leppie on 2010-02-08
hi and welcome to the community,

what does the command "set" give as output?
also, is this a wubi install (ubuntu within windows)?

---

### Post by IchBinWamphyri on 2010-04-09
** Solution**

 **Warning:  The solution below is only for Wubi 9.10. It will make older versions unbootable.** 
Boot into Windows and click on the following link to download the file "wubildr": 
[wubildr]("http://launchpadlibrarian.net/36920146/wubildr") 
Don't try to open the file. Move the file to "C:\" to replace the faulty "C:\wubildr". (to get to "C:\" go to "My Computer" or "Computer" and double click the "C:drive") 
If Wubi is not on the C:drive, you might need to place wubildr into the partition containing Wubi. So if Wubi is not on the C:\drive, repeat the above instructions, using the drive letter of the partition containing Wubi in place of "C:".

---

### Post by prodigy_ on 2010-04-09
Edit: nevermind.

---

