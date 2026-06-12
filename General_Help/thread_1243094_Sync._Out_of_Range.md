---
title: "Sync. Out of Range"
date: 2009-08-17
forum: General Help
---

### Post by alejandro.mc on 2009-08-17
No Sync. Out of Range
I'm trying to install Ubuntu, it boots from the dvd drive..then options appear, i choose to try Ubuntu without changes (livecd), because i wan't to use gparted before installing..

but after a few seconds the monitor sort of shuts down, and a sign comes up, that moves all over the screen..it says "No Sync. Out of Range".

My monitor is Samsung SyncMaster 551v, I'm trying to install Ubuntu 32bit in AMD64, with ATI HD3200 onboard.

I know it has to do with the frequencies of the monitor but i don't know how to solve this..

I've tried, NO ACPI, NO APIC, NO LAPIC, SAFE GRAPHICS MODE, NOSPLASH

Anything else I should try??

Thanks!

---

### Post by CatKiller on 2009-08-17
> **alejandro.mc said:**
>  Anything else I should try??

At the bottom of the menu you'll see a list of the Function keys and what they do. One of them is marked "VGA mode" or something similar (it might be F4, but it's a staggeringly long time since I looked at an install disk, so I could be completely wrong). That should let you choose a lower resolution, which will hopefully have refresh rate ranges that your monitor can handle. Once you've checked that everything else works and you decide to do a full install, we can try to help you find a permanent solution.

---

### Post by alejandro.mc on 2009-08-17
Thanks for replying CatKiller; little problem though..

I'm trying to install 8.04 LTS..

Options for F4 are:

Normal
Safe Graphics Mode
Use driver update CD
OEM install (for manufacturers)



So I've already tried them and none of the options get me pass through the monitor turning black with the sign "Sync. Out of Range"

I've tried them combined with and without NO APIC, NO ACPI, NO LAPIC, NOSPLASH in the F6 command line..

Any ideas??

Please don't think I haven't search the web, I did. There are a couple of solutions out there, which mostly involve those that I've already tried, and others that involve modifying the xorg.conf [of course you have to have Ubuntu already installed =)]

Thanks again!

---

### Post by CatKiller on 2009-08-17
> **alejandro.mc said:**
> Any ideas??

Not at the moment (it's twenty-to-five in the morning here; I should really be in bed). One option is to install from the alternate disk, which (IIRC) uses a text-based installer, so you can actually get it installed. Unfortunately, that means that you don't get to try everything out in the live environment. Or you could use a different monitor to check everything out and do the install. Neither option is especially optimal. If I think of a genuinely good solution, I'll let you know.

---

### Post by roharme on 2009-08-17
If u r using a TFT monitor.You will have a button to Switch from Analog to Dgital.
 
When u get Sync out of range error. press that once! It gets refreshed and you will get your screen back.

---

### Post by alejandro.mc on 2009-08-18
Thanks CatK, here in Buenos Aires is 1 AM..hope to hear from you soon then! =)

As to the TFT..as I said earlier it's a Samsung SyncMaster 551v, but thanks for replying though roharme..


So anyone else?

THX

---

### Post by Wim Sturkenboom on 2009-08-18
As suggested before, use the alternate CD.

---

### Post by alejandro.mc on 2009-08-18
Solved!!!

I couldn't believe it worked..

Here's how to..it's not fixed, but it's a handy workaround to the issue.

The problem I believe has to do with the frequency and the ATI "drivers" that handle the installation, my monitor couln't handle the frequency determined in there. So I found out in a post out this forums that there is a way to change the dynamic frequency (sorry if this is not correct, I just don't understand how it worked, but why it worked).

So what do you have to do? Once the "Sync. Out of Range" sign comes up (the monitor is down and you see nothing but the sign moving around the screen) you have to start trying to find the frequency by typing:

CRLT + ALT + "+"

and

CRLT + ALT + "-"

Do it slowly, press it once, see if anything changes, press the same combination again, see if anything happens, press it again...

Somehow the third or fourth time you change it (by pressing those key combinations) the sign will disappear and image will come up. 

BUT!!! Don't despair because of you are going to see! Image will not be perfect! It's going to look weird, but at least you will be able to see, much better, you'll be able to use the live cd, and install Ubuntu.

So, once you installed it, it asks you to restart, you do that, and when you restart, the same problem will occur. You will have to press CRLT ALT * or - to find the frequency again. 

So do you use Ubuntu like that, with all the screen messed up? NO, you install immediately the restricted drivers offered by Ubuntu. That way ATI will have the correct drivers, and after a reboot:

TARAAAAANNNNNN

Everything will look GREAT!!!

I hope this helps someone somewhere else in the world, because I went crazy with this one!!

Thanks to the repliers too!!!

Good luck!

---

### Post by Wim Sturkenboom on 2009-08-18
Thanks for the feed back. I do know the <ctrl><alt><+> / <ctrl><alt><-> trick but would never have thought of applying it during install.

Thanks again.

---

### Post by CatKiller on 2009-08-18
> **alejandro.mc said:**
> Solved!!!

Excellent :)

---

