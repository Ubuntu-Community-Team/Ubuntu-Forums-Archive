---
title: "Cannot Access BIOS on Laptop Xbuntu 11.10"
date: 2012-07-03
forum: General Help
---

### Post by helobubba on 2012-07-03
Hello All--

Having some difficulty simple entering the BIOS on my Envy 14 Laptop with 11.10 involved.  I am trying to boot from my Live USB to install 12.04....  Running Xubuntu 11.10.   Also using solid state drive as my hard drive.  When I boot up, for about a half second, it flashes "Hit ESC for BIOS."  I have tried the following things to try and enter the BIOS, and all have been unsuccessful:

Tap ESC once when it says "HOLD ESC"
Tap ESC continually during the entire bootup process
Hold ESC, then press power, and keep holding

Tap FN-ESC once when it says "HOLD ESC"
Tap FN-ESC continually during the entire bootup process
Hold FN-ESC, then press power, and keep holding

Tap F10 once when it says "HOLD ESC"
Tap F10 continually during the entire bootup process
Hold F10, then press power, and keep holding

Tap FN-F10 once when it says "HOLD ESC"
Tap FN-F10 continually during the entire bootup process
Hold FN-F10, then press power, and keep holding

I am running out of things to try, and afraid that my BIOS is somehow inaccessible...has anyone seen anything like this before?  Thanks very much for your help!

- Bubba

---

### Post by SlugSlug on 2012-07-03
try tapping F1 or delete

---

### Post by bryncoles on 2012-07-03
Well, if you already have a version of Grub installed on your computer you can simply 'chainload' the usb to the bootloader, and run it from there.  [check this page out](https://help.ubuntu.com/community/BootFromUSB).  Look for the section 'Booting via GRUB'.

---

### Post by sudodus on 2012-07-03
I saw several links with tips when searching the internet for ***keys for bios menu***. Try some of those tips!

---

### Post by elliotn on 2012-07-03
f1, f2 or del normally works in most brands

---

### Post by pbrane on 2012-07-03
searching with google: (*Envy 14 laptop BIOS key*)

"To access, completely power off your Envy.
Press the power button and press F10"

---

### Post by helobubba on 2012-07-03
Thanks to all who posted for your suggestions.  The Grub loading method I will use as a last resort...I would still very much like to be able to access my machine's BIOS.  I have tried all combinations (using in conjunction with FN key, tapping, holding, rapid-tapping, etc.), of ESC, DEL, F1, F2, F10.

However, from the "BIOS KEY" google search, all indications point to the ESC key being the one to use on HP laptops - this would be reinforced by the fact that my splash screen does say "Press ESC for BIOS" at startup.  Would welcome any other suggestions, if anyone has seen this before, but I am afraid my only option is to Grub to 12.04 and hope that somehow that clears this...malfunction?

Thanks Again,
Bubba

---

### Post by SlugSlug on 2012-07-04
if poss plug a usb keyboard in and hit ESC on that

---

### Post by lolpenguin on 2012-07-04
You mentioned a SSD, and since they are very fast, I barely see my POST, BIOS, GRUB and Plymouth screens, so knowing the key to access the boot menu and CMOS settings is handy. Try pressing the key before the "Press [key] to [etc]" message is shown.

---

### Post by helobubba on 2012-07-05
Keyboard: great idea, thanks!  I will have access to one next week and can try that out.  Nice thought about the SSD as well; I never thought about it but you're right, the bootup is faster so why wouldn't the keypress window be faster...but...I have tried many different taps of ESC, sooner, later, faster, slower, so I don't think that is it!  Will report back if the USB keyboard is a winner.  Appreciate all the suggestions....

---

### Post by helobubba on 2012-07-22
PROBLEM SOLVED!

Slug...way to think outside the box.  Nothing worked...till I finally got access to a USB keyboard (tough where I work sometimes).  Plugged it in, hit power button....the BIOS blurb flashes and I hit ESC on the USB keyboard and BAM!  Instant BIOS access.

I may never know why xubuntu/linux decided to lock out my keyboard during the bootup sequence, but I am glad this simple workaround was a success.  Many thanks to all the contributors for your help!

With Much Gratitude,
Bubba

---

