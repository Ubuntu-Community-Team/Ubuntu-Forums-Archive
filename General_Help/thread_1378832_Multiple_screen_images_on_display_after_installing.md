---
title: "Multiple screen images on display after installing Nvidia resticted drivers"
date: 2010-01-11
forum: General Help
---

### Post by CaKiwi on 2010-01-11
I have a Compaq Presario CQ60 laptop with an Nvidia 8200M graphics card. When I try to enable visual effects I am asked to install the Nvidia restricted driver. When I do this and reboot, I get 6 copies of the Ubuntu screen on my display. Does anyone know what is causing this? I'm not sure which version it installed, I assume either 173 or 185. I have downloaded version 190 from the Nvidia web site. Should I install that version? If so, it is a .run file, how do I install it?

Also, how do I reinstall the old driver. I fixed the problem this time by reinstalling Ubuntu, but that will get old if I have to do it too often.

Thanks in advance

---

### Post by CaKiwi on 2010-01-19
This is still a problem, does anyone have any suggestions?

---

### Post by CaKiwi on 2010-01-23
Anyone?

---

### Post by garv_sk9 on 2010-02-02
hey, if your problem is still not solved,

From the Menu, open Terminal. 
Type the command below and press enter: 
 
    sudo vi /etc/X11/xorg.conf 
 
Enter your system/root/administrator password to open the file. 
At the bottom is a section labelled "Device", which ends with a set of Option entries. 
Arrow down to the last Option entry in that section, then press A (make sure it's a capital A) then enter. 
Press TAB to move below the Option above and type (with quotes): 
Option (press TAB) "ModeValidation" (press TAB) "NoTotalSizeCheck" (press Escape) 
Type two capital Z's to save and exit, close Terminal and reboot from the menu. 

i donot take the credit as the original solution provider, i found this while searching for a solution to the problem at [www.nvnews.com](www.nvnews.com). do not remember the address of the forum though.
this problem is specific to the Nvidia cards and ubuntu based OSs. this works perfectly!!!

if you re unfamiliar with the VI editor then it might be very dificult for you. then install the Gedit on your system. it is very easy text editor!

---

### Post by CaKiwi on 2010-02-03
Thanks for the reponse, garv_sk9. I will let you know how it turns out when I get a chance to try it.

---

