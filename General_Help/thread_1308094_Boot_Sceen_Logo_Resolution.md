---
title: "Boot Sceen Logo Resolution"
date: 2009-10-31
forum: General Help
---

### Post by jonathanysp on 2009-10-31
Hi! Just installed karmic on my nice new 1tb hdd. Everything is great so far but the boot screen bit where theres the ubuntu logo in black and white (not the xsplash part) does not seem to be in the correct resolution. I know this is kinda picky but i want to  make my ubuntu install perfect! What is this part of the boot proccess called and how can i change its resolution? (i have a nvidia gfx card)

Also, sometimes when opening the home folder in nautilus, the folders show up but the files in the home folder takes a while to load. What is slowing it down?

thanks!

---

### Post by Muley63 on 2009-11-06
I have the same problem. I've been searching everywhere for a fix, but can't find one. I should have know better and waited for Lynx (10.4) and done a clean install since not one upgrade from 8.04 to Karmic has gone smoothly. I like and care about Ubuntu, but their upgrades are horrible. Xsplash is in the wrong resolution. I can't figure a way to config the GDM (I just want to change the color). The "fastuserswitcher" applet was broken. Linux and Ubuntu decided to abandon ACX100 wireless drivers...it sure would have been nice if Ubuntu compiled a module or at least warning before I upgraded. 

I'm looking hard at doing the min install version because I don't need GDM, or XSplash or USplash or Gnome. I've been using OpenBox lately and once I got the hang of it, light bulb moment, I really don't need all that stuff. I was mainly interested in UbuntuOne, but it wasn't all that. I was going to sync docs from my Dell Mini 9, but the upgrade path was from 9.04 and the Mini is at 8.04. So now I'm stuck with a funky opening, a GDM I don't like, wireless network and my mem resource went up 40 MB. It's not all bad, I now have 6 months to backup my stuff, buy a new wireless card and learn more about OpenBox. However, I will install 10.04 because I really do like Ubuntu, but going forward, I'm not upgrading anymore. It's too risky to do so on my main computer.

---

### Post by freddybob on 2009-11-06
> **jonathanysp said:**
> the ubuntu logo in black and white (not the xsplash part) does not seem to be in the correct resolution

I have the same minor problem and have as yet been unable to find the answer.  My screen is 1680x1050.  My graphics card is nvidia.

---

### Post by Minsky on 2009-11-09
I think that the solution lies in **/etc/usplash.conf**. From what I can gather, the boot process displays a usplash screen, which is the black & white Ubuntu logo, before the xsplash screen is displayed, and the screen resolution is stored in **usplash.conf**. Open the file and check if the values match your screen resolution. If not, make a backup of the file and then edit the file by changing the values accordingly using Root privileges, and then run **sudo update-initramfs** in a terminal window. Hopefully, that should work.

---

