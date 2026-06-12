---
title: "Making GRUB2 recognize both Windows partitions"
date: 2012-01-04
forum: General Help
---

### Post by Cakewalking on 2012-01-04
I had Ubuntu 10.04 LTS and Windows 7 installed and was dual-booting without any problem. Then I installed Windows XP along with them and a problem has developed.  After Windows XP wiped out the GRUB2 MBR, I re-installed it.. then I did 'update-grub'. Windows XP was not detected when I updated GRUB2 and now when I boot Windows 7 I get Windows XP.  I think what I need to do is set the &quot;set root&quot; parameters for GRUB2 to point to each correct address where each Windows resides on my computer. I am not sure how to go about doing this and hoping someone could help me out.  I have attached a screen shot of my hard disk: sda5 is Linux, sda7 is Linux swap, sda6 is Windows XP, and sda2 is Windows 7.  I have also attached a screen shot of grub.cfg  [http://i40.tinypic.com/1ovno6.png](http://i40.tinypic.com/1ovno6.png) [http://i41.tinypic.com/143gs2e.jpg](http://i41.tinypic.com/143gs2e.jpg)

---

### Post by dandnsmith on 2012-01-05
My experience suggests that what you really need to sort is the Windows boot arrangements. By installing XP, you messed up the Win7/XP boot structure, and now any amount of messing with grub won't get the Win7 back - what you need is a boot repair from the correct Windows utility (which is, unfortunately, beyond the things I have done).

Someone else may have a different opinion, but mine is based on trying to set up a boot of XP after messing up booting with Me and linux also on the same HDD.

---

### Post by coffeecat on 2012-01-05
It would be useful to get an overview of your whole system, including details of your Windows partitions. The boot info script provides this. Boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

