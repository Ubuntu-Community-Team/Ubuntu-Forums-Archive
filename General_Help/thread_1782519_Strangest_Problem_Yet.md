---
title: "Strangest Problem Yet"
date: 2011-06-14
forum: General Help
---

### Post by pouldney on 2011-06-14
I have an Acer aspire 1551 notebook
  
  Ubuntu worked fine until now. 
  It will not boot.
  
  It boots until the music sounds, and the login screen
  is supposed to appear, then it just locks up.
  
  The strange part is that both the installed version and
  the USB ubuntu live version fail at the same point.
  I even tried two versions of Ubuntu live on USB.
  
  Windows 7 however works fine.
  
  I think something must have happened to the hardware
  That will not load ubuntu,but will load windows
  
       ANY IDEAS?

  About the only thing I did different on my last session was
  to install wine and then install Textpad in wine

---

### Post by ventrical on 2011-06-14
> **pouldney said:**
> I have an Acer aspire 1551 notebook
  
  Ubuntu worked fine until now. 
  It will not boot.
  
  It boots until the music sounds, and the login screen
  is supposed to appear, then it just locks up.
  
  The strange part is that both the installed version and
  the USB ubuntu live version fail at the same point.
  I even tried two versions of Ubuntu live on USB.
  
  Windows 7 however works fine.
  
  I think something must have happened to the hardware
  That will not load ubuntu,but will load windows
  
       ANY IDEAS?

  About the only thing I did different on my last session was
  to install wine and then install Textpad in wine

I just had the same problem on my Acer Aspire 3260 but I had updated the Linix Kernel to 32.32 and it wouldn't boot at all. I rebooted and chose the 32-31 kernel from GRUB and it booted just great.

---

### Post by pouldney on 2011-06-15
This problem gets stranger
  
   I tried ubuntu 11.4 and 10.04.2  on live USB 
  they would not boot failing at the same spot
  
   Today I tried ubuntu 9.10 Surprisingly it booted live.
  The screen was not quite right(the toolbars at top and bottom
  were missing) So I powered down and booted again.This time the
  screen was ok.
  
   I pulled out the USB stick and booted into the installed ubuntu 10.04
  This time it worked.
  
    I have no idea what Rel 9.10 did to fix it, as I did nothing but use the
  file browser while in Rel 9.10

---

### Post by pouldney on 2011-06-15
Further into this problem
    
    I discovered today what causes the problem.I closed the computer screen
  While in a Ubuntu session.
    After raising the screen the screen was dimly lit.
    
    I shutdown ,and when I rebooted into ubuntu, the boot seized in the same way.
  I now think this is how the problem happened the first time.  
  
    Hope this gives someone a clue on how to fix it.

---

### Post by pouldney on 2011-06-23
Today I went into System - Preferences - Power Management  
  and tried to adjust the screen brightness - the screen locked up 
 
 
     ** Finally found a Fix  ** 
      By reference to this site 
[http://linuxon1001p.blogspot.com/2010/03/fixing-brightness-controls.html](http://linuxon1001p.blogspot.com/2010/03/fixing-brightness-controls.html) 
 
     in terminal sudo gedit /ect/default/grub 
   edit the following line to 
 GRUB_CMDLINE_LINUX=" quiet splash acpi_osi=Linux acpi_backlight=vendor" 
  then in terminal  sudo update-grub 
 
  Although the brightness bar in power management disappears and 
  Fn+F5 and Fn+F6  does not work.So I do not know how to adjust brightness.
  It all works well in Ubuntu 9.10 ,so how do I get the settings into ubuntu 10.4.2

---

### Post by pouldney on 2011-11-17
Upgraded to Ubuntu 11.10 from live thumb drive Nov 2011
  The brightness control now works

---

### Post by Rubi1200 on 2011-11-18
Glad you finally managed to resolve these issues.

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy :-)

---

