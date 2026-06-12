---
title: "Ubuntu ATI Radeon X300"
date: 2010-04-30
forum: General Help
---

### Post by shah_vm on 2010-04-30
Hello 

I have installed ubuntu lucid on dell inspiron 6000 i noticed that latest version of ubuntu does not support ati x300 graphics card. is there any 3rd party drivers that i can install. 

Thanks in advance

---

### Post by dino99 on 2010-04-30
xserver-xorg-video-radeon ? or fglrx ?

---

### Post by shah_vm on 2010-04-30
> **dino99 said:**
> xserver-xorg-video-radeon ? or fglrx ?

thanks for the reply. i thought fglrx does not work on 8.4 and later.

---

### Post by gwpritch on 2010-04-30
You are correct, the fglrx will not work. If you have installed lucid and its working, it has probably already set up the correct driver for you.

---

### Post by shah_vm on 2010-04-30
> **gwpritch said:**
> You are correct, the fglrx will not work. If you have installed lucid and its working, it has probably already set up the correct driver for you.

i have installed lucid and it is working but i am unable to select extra under visual effects anymore. it says that my hardware does not support. I was able to select extra in karmic version of ubuntu.

---

### Post by gwpritch on 2010-04-30
Does it allow you to select normal effects ie is compiz working?

---

### Post by shah_vm on 2010-04-30
> **gwpritch said:**
> Does it allow you to select normal effects ie is compiz working?

compiz is not yet installed. i have not tried normal effects will try once i reach home.

---

### Post by shah_vm on 2010-04-30
> **shah_vm said:**
> compiz is not yet installed. i have not tried normal effects will try once i reach home.

it does not stays at normal effects. It revert backs to none. I also tried installing xserver-xorg-video-ati_6.13.0-1_i386 then it says that i have newer driver installed. 

I also installed compiz that is also not working.


It was working fine in karmic version. Dont understand what is going wrong. Any help?

---

### Post by dazcaz on 2010-05-01
I have a problem with the same card where when the comp wakes from sleep the screen is unreadable. I have to re-start to be able to use the computer.
what is the better driver for the X300?

---

### Post by shah_vm on 2010-05-01
> **dazcaz said:**
> I have a problem with the same card where when the comp wakes from sleep the screen is unreadable. I have to re-start to be able to use the computer.
what is the better driver for the X300?

i feel like to rollback to previous version of ubuntu. until i get some help.

---

### Post by shah_vm on 2010-05-02
> **shah_vm said:**
> i feel like to rollback to previous version of ubuntu. until i get some help.

i solved the issue. problem is when external display is connected thru vga then i m unable to select extra or normal option under appearance. i removed external monitor connection and restart ubuntu and everything is working.

---

### Post by steliosv on 2010-05-03
mind passing your xorg.conf file along? i've lost X with my lucid upgrade and have the latest drivers installed to. will switch to an nvidia card if i can't get this working. i always had to monkey with ATI cards and will never buy them again.

---

### Post by steliosv on 2010-05-03
nevermind. looks like i rebooted with no display attached. still only getting 720p but that's a different problem.

---

### Post by sylvester_0 on 2010-05-06
My uncle recently auto upgraded his machine with an X300 to Lucid and experienced some strange artifacts. His effects set to Normal were previously working in Karmic but when the upgrade to Lucid was done he had no more context menus (a right click menus!) There was a shadow outline of where the menu should have been but no menu. I walked him through enabling remote desktop and took a look for myself. Disabling all visual effects remedied the problem. Man I dislike ATI products...

---

### Post by savebart on 2010-05-06
> **sylvester_0 said:**
> My uncle recently auto upgraded his machine with an X300 to Lucid and experienced some strange artifacts. 

I also reported some graphical artifacts, for example the boot screen shows green "rays" all around the Ubuntu logo.

> His effects set to Normal were previously working in Karmic but when the upgrade to Lucid was done he had no more context menus (a right click menus!) There was a shadow outline of where the menu should have been but no menu. I walked him through enabling remote desktop and took a look for myself. Disabling all visual effects remedied the problem. Man I dislike ATI products...

About the right click menus, I see exactly the same effect but only on the Thunderbird3 menus.
That's ugly!

---

### Post by patrickcage on 2010-05-10
I have to report exactly the same activity as 'savebart'.
My Ubuntu boot up logo has a green aura around it and the thunderbird3 is unusable with any visual effects enabled.
I'm would consider a roll back to Karmic, but that isn't really solving the problem - I don't wish to dwell on the Koala for an eternity :P.

I tried downloading the driver from ATI's website but I get an error when trying to install it:

> "Error: ./default_policy.sh does not support version default:v2:i686:lib::none:2.6.32-22-generic; make sure that the version is being correctly set by --iscurrentdistro"

---

### Post by savebart on 2010-05-18
Have you found some solution, Patrickcage?
I am still looking for some help... and problem with video still is there!

---

### Post by patrickcage on 2010-05-19
@savebart
No, I'm afraid I am no further on either. Still have the same problems - the Koala is looking ever more enticing! :)

If I come across a solution I will post it here.

---

### Post by /usr/bin/hacked? on 2010-05-21
I have 2x radeon x300se in my computer. both are pci-e. They won't work for some reason. they are known working cards, and when linux starts up, the ubuntu loading screen shows up on them, so i know that ubuntu is able to do something with them. I get the same error as patrickcage, but have no idea what it means or how to fix it. I'm going to go down to 9.10 and see how that works for me. Any help would really be appreciated. 
Thanks!

---

### Post by _Duhhh on 2010-06-11
I upgraded from Karmic to Lucid on my system with an X300. Display worked OK, but I can't use 1920x1200 on both monitors. I'm stuck at 1920x1200 on one, 1600x1200 on the other.

It also reverts to NONE on visual effects whenever I try to change the setting. It says it looks for a driver, asks me to confirm the change, but when I check the setting, it reverts to NONE.

---

### Post by Mark Phelps on 2010-06-11
> **_Duhhh said:**
> I upgraded from Karmic to Lucid on my system with an X300. Display worked OK, but I can't use 1920x1200 on both monitors. I'm stuck at 1920x1200 on one, 1600x1200 on the other.

It also reverts to NONE on visual effects whenever I try to change the setting. It says it looks for a driver, asks me to confirm the change, but when I check the setting, it reverts to NONE.

My guess it that it reverts because the unfortunate truth is that the open source drivers already installed are the ONLY drivers that will work with the x300 and current versions of Ubuntu.  ATI dropped fglrx driver support for that chipset over a year ago.

---

### Post by a1an on 2010-11-15
> **Mark Phelps said:**
> ATI dropped fglrx driver support for that chipset over a year ago.

That's why I'm glad I dropped ATI several years ago, unluckily I still have an x300 card and cannot use any decent acceleration with Ubuntu.

At least xrandr support is quite convenient in setting multiple screen configuration, once you have found the correct set of options, try it to solve the resolution difference on dual monitor.

---

### Post by clhsharky on 2010-11-15
a1an

> That's why I'm glad I dropped ATI several years ago
Not Me, I still have 2 ATI legacy cards in Ubuntu boxes.
ATI Radeon X550(rv4xx)fanless and X1650(rv5xx).
>  I still have an x300 card and cannot use any decent acceleration with Ubuntu
x300 is a rv/rs X4xx chip and they have never had any hardware acceleration, only software acceleration and that is CPU bound.
Acceleration works decent for me with X550 card, 2GHz duel core CPU, and r300g OSS driver on 10.10 Ubuntu.

Sharky

---

