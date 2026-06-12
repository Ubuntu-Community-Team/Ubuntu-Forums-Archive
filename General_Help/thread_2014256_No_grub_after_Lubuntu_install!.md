---
title: "No grub after Lubuntu install!"
date: 2012-07-01
forum: General Help
---

### Post by Kols on 2012-07-01
So, introducing my girlfriend to Linux, I decided to install Lubuntu 12.04 on her netbook while she's away.
My goal was to have a dualboot with Windows 7 Starter and Lubuntu. 

After having successfully installed Lubuntu from a LiveUSB, I was prompted to reboot as usual. Then my computer booted straight into Windows without starting grub at all!
I was able to re-enter Lubuntu from the LiveUSB, but that's still the live version, not using what I've just installed.

Details about installation

/sda/sda6 -where I installed Lubuntu AND bootloader, mounted on /
/sda/sda5 -swap-area

TL;DR - Dualboot Win/Lubuntu, GRUB missing after Lubuntu install

Please advice quickly, or else girlfriend will think I'm a total newb=P

---

### Post by drs305 on 2012-07-01
Kols

Welcome to the Ubuntu Forums.  :-)

Boot into the LiveCD, install Boot Repair, and click the 'Recommended Repair' button.

If that fails to fix the problem, there is an option to run the boot info script. Post the link it provides so we can take a look at your setup.

The link to Boot Repair is in my signature line.

Perhaps we can get this sorted out before your GF even notices.

---

### Post by Kols on 2012-07-01
> **drs305 said:**
> Kols

Welcome to the Ubuntu Forums.  :-)

Boot into the LiveCD, install Boot Repair, and click the 'Recommended Repair' button.

If that fails to fix the problem, there is an option to run the boot info script. Post the link it provides so we can take a look at your setup.

The link to Boot Repair is in my signature line.

Perhaps we can get this sorted out before your GF even notices.

Thanks for quick reply!

Will your solution work, even though I'm not actually IN the installed version of Lubuntu, but the LiveUSB session that I used
to install it?

I've had a similar problem before, you see - when while booting I was prompted with Grub Rescue, without being able to boot into neither Win or Lubuntu. The solution then, was to use the LiveUSB, boot into the installed Lubuntu, and install Boot Repair from there.

Thanks again for the reply!

---

### Post by drs305 on 2012-07-01
> **Kols said:**
> Thanks for quick reply!

Will your solution work, even though I'm not actually IN the installed version of Lubuntu, but the LiveUSB session that I used
to install it?

I've had a similar problem before, you see - when while booting I was prompted with Grub Rescue, without being able to boot into neither Win or Lubuntu. The solution then, was to use the LiveUSB, boot into the installed Lubuntu, and install Boot Repair from there.

Thanks again for the reply!

Yes, the Boot Repair app will work from the Live Desktop (USB, CD, DVD). The chroot procedure should not be necessary, and if it is BR can walk you through it.

---

### Post by Kols on 2012-07-01
> **drs305 said:**
> Yes, the Boot Repair app will work from the Live Desktop (USB, CD, DVD). The chroot procedure should not be necessary, and if it is BR can walk you through it.

This did the trick -thank you!
Reading the BR-documentation, it DOES state that it runs live, so that my bad for asking before reading=P

I've been a Linux Ubuntu/Lubuntu-addict now for a couple of months, learning more and more - but every now and then, I come across problems like this, and then I'm very grateful for forums, and resourceful people to help out. 

So once again, thank you for solving my problem!
GF will continue to think I know everything=P

-Kols

---

### Post by drs305 on 2012-07-01
> **Kols said:**
> This did the trick -thank you!
Glad it's working.

If you don't have any other issues please mark the thread SOLVED via the Thread Tools link near the top right of the first post. It helps the helpers concentrate on unresolved issues and helps others with problems find relevant threads.

> 
GF will continue to think I know everything=P


We are a very tight lipped group.  ;-)

---

