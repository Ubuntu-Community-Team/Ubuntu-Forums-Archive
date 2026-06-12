---
title: "Need Help bad please"
date: 2010-06-29
forum: General Help
---

### Post by ToxicBurn on 2010-06-29
Hi guys I need to install Ubuntu 10.4 and my problem is the cd boots fine up to the boot screen with the Ubuntu logo and then My monitor says its going to sleep and i can not get past that because my monitor is off.
 
I tried this with the latest opensuse RC and the same thing .
 
the problem i think is my new motherboard and cpu 
 
I have a Gigabyte board with the H55 intel chipset 
and a Core i 5 750 cpu.
 
Im not sure but i think it may be a kernel issue because Alpha 1 of 10.10 works i just want to run stable 
 
Is there a way i can install 10.4 with a updated kernel in it ?
 
i have tried all options at boot with zero luck
 
i really want to use this distro but im forced to run windows right now 
 
please help.
 
thanks

---

### Post by Iowan on 2010-06-29
Have you checked your BIOS for power-saving options?

---

### Post by ToxicBurn on 2010-06-29
no i have not what type of options should i look for in power 
 
and should i try to turn them off ?

---

### Post by cariboo on 2010-06-29
Have you tried starting with nomodeset? At the main screen, the one with the little man and keyboard, press any key to see the usual menu. Once at the menu screen press F6 and select nomodeset, once this is selected, you should be able to boot to the desktop.

BTW, your title really gives no inkling as to what your problem is.

---

### Post by ToxicBurn on 2010-06-29
Yes i tried the nomodeset and still monitor goes to sleep 
 
I can see the white dots turn to red and so on then 10 sec later monitor goes to sleep
 
I have turned off any power options and still no luck :(

---

### Post by Windows Refugee on 2010-06-29
If you are using an external monitor or LCD, does it have a configuration screen you can access from the controls on the monitor itself?  Perhaps it is your monitor, and not your computer, which is turning off the display.

One way to verify this might be to wait until the screen goes dark, and then power the monitor off and then on again.  If the display comes back on (even if only for a short time before going dark again), then your issue is with your monitor's settings, not your BIOS or Ubuntu's settings.

Hope that helps.

---

### Post by ToxicBurn on 2010-06-29
no its not the monitor because just 2 weeks ago i was running ubuntu fine i just did an upgrade to the new motherboard and cpu so nothing has changed but the motherboard and cpu .
 
thats why i think its a chipset support issue the H55 is pretty new along with the core i 5 .
 
not sure why the latest Maverick Meerkat alpha works and not the 10.4 LTS

---

### Post by Windows Refugee on 2010-06-29
It may indeed be due to your motherboard upgrade, but if your system is telling the monitor to enter a power-saving state, a quick fix just might be to configure your monitor to not enter the sleep / suspend / low power state, or whatever it refers to it as...  at least until you can iron out the issues with your hardware.

---

### Post by hackerseraph on 2010-06-29
its going into sleep mode because the display is out of range. do you have another monitor in your house that you can use to change your display settings to something lower and then plug in the other monitor and reconfigure everything?

---

### Post by ToxicBurn on 2010-06-30
Hi thanks for the reply ,
 
only thing is that the monitor and videocard worked perfect 2 weeks ago with a diff motherboard and cpu . 
 
so why would it do this now ?
 
also i turned off all power save features in bios and on the monitor now the monitor does not turn off but now says just after the ubuntu logo splash 
 
( No Source input ) 
 
is there a way to install 10.4 in a virtual box and update it then make a usb boot image from with-in the virtual os.
 
i have a feeling a strong feeling its my new intel chipset being Not supported in 10.4

---

### Post by arpanaut on 2010-06-30
What video card? same as before or on-board.

Have you thought of trying the Alt. Install iso?
It is usually less affected by video glitches.

---

### Post by ToxicBurn on 2010-06-30
I have a ATI HD 5770 and my motherboard has no onboard graphics and worked perfect until I upgraded motherboard and cpu

---

### Post by ToxicBurn on 2010-06-30
And yes I tried the alt and the net install same issue with both also tried opensuse

---

### Post by ToxicBurn on 2010-06-30
Ok im in ubuntu and working great ,

after a few hours of reading around i found that The new Core i 5 and Core i 7 intel chips do not work with Turbo Boost enabled in bios , well not with the stock kernel that shipped with 10.4 so once i turned off Turbo boost everything booted fine.

thanks for trying to help all of you in the end i got it to work 

thanks again

---

### Post by Clever_Username on 2010-06-30
Video card issue maybe?

---

### Post by hackerseraph on 2010-06-30
sounds like a video card issue with the turbo boost. Overclocking always seems to cause one issue or another with external video cards and the amount of boost you get is only a few MHz and isn't worth it anyways.

---

### Post by ToxicBurn on 2010-07-01
i think you may have thought i over clocked the videocard and thats not the case .
 
The new Core i 3 / Core i 5 / Core i 7 cpu's have a feature that is turned on by default in most BIOS called turbo boost that over clocks the cpu depending on the demand so if i was just sitting at my desktop running at 2.6ghz and then launched world of warcraft the cpu over clocks itself to 3.2ghz while running the game.
 
this feature is supported by intel and i could not get ubuntu to boot untill i turned off Intel turnbo boost in my bios .
 
just wanted to post an update to clear things up.
 
thanks

---

