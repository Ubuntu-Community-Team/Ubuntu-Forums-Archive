---
title: "Screen blinks after BIOS"
date: 2012-06-02
forum: General Help
---

### Post by kabeza on 2012-06-02
Hi

I've a Samsung RV420 laptop w/ dual boot Win7 Ultimate 64b and Ubuntu 12.04.
It has been working great until yesterday:

When laptop powers on, it shows bios info, etc. and then screen begins blinking indefinitely.

I've been able to make it boot by using a 12.04 LiveCD and then reinstalled, reupdated grub correctly without errors, etc. (just in case), but this option didn't work

1) Could be this a hardware problem?

2) The disk shows no errors, I could see and mount partitions (in liveCD)

3) Laptop boots from liveCD but no from harddisk.. :-s

4) The laptop has a recover functionality (F4) but seems it requires booting from HDD, and doesn't work because screen begins bliking

What could be wrong? Any ideas?

Thanks a lot...

---

### Post by adiabloiiifan on 2012-06-02
> Hi  I've a Samsung RV420 laptop w/ dual boot Win7 Ultimate 64b and Ubuntu 12.04. It has been working great until yesterday:  When laptop powers on, it shows bios info, etc. and then screen begins blinking indefinitely.  I've been able to make it boot by using a 12.04 LiveCD and then reinstalled, reupdated grub correctly without errors, etc. (just in case), but this option didn't work  1) Could be this a hardware problem?  2) The disk shows no errors, I could see and mount partitions (in liveCD)  3) Laptop boots from liveCD but no from harddisk..   4) The laptop has a recover functionality (F4) but seems it requires booting from HDD, and doesn't work because screen begins bliking  What could be wrong? Any ideas?  Thanks a lot... 
Want to +1 this

---

### Post by kabeza on 2012-06-02
> **adiabloiiifan said:**
> Want to +1 this


do you also have the same problem?

---

### Post by Mark Phelps on 2012-06-03
IF it boots into a graphical desktop using a CD, that rules out any video hardware problem.

It sound like once the POST messages are displayed on the screen, it won't boot into an OS selection menu, right?

And, you were able to reinstall GRUB and it did work?  For how long did it work, and what did you do right after that?

---

### Post by kabeza on 2012-06-04
> **Mark Phelps said:**
> ...And, you were able to reinstall GRUB and it did work?  For how long did it work, and what did you do right after that?


I've reinstalled and re-updated GRUB correctly without errors, but no luck. Still the blinking, so I've finally decided to try booting with win7 dvd and reinstall it.

The win7 installation went fine but, after the 1st reboot, it begun halting in win7 logo, so I told my brother to go store with warranty paper and claim a new replacement unit so hope they have stock

PS: I've never seen a screen blink that way after bios, and yes, I was such a dumba** I didn't film it with my phone

---

### Post by dino99 on 2012-06-04
you might try booting by adding some options: first add "nomodeset" to the grub boot line; or "noacpi"

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

