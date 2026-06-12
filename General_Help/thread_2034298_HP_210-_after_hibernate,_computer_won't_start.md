---
title: "HP 210- after hibernate, computer won't start"
date: 2012-07-28
forum: General Help
---

### Post by ftkatyowser on 2012-07-28
I'm new to Linux, so sorry if I mess up some terminology.  I've looked all over google and can't come up with anything.

I'm running xubuntu 12.04 on HP mini 210.  I clicked "hibernate" from the menu (where you click your username) and the screen went blank, with te backlight on.  I closed the lid (system is set to suspend when lid shuts, if that matters).  Went to resume this morning, and it won't boot up.  The computer appears to start (I can h.ear the hard drive whiz) but nothing appears on the screen- it doesn't even light up.  I put in a new screen figuring maybe that was the problem, but it's still the same.  Is there a such thing as bricking your harddrive? because I'm pretty sure that's the equivelent of what I did.  I tried unplugging and leaving the battery out for a couple hours, but that didn't work either.

I never turned on hibernate like I've read that you have too.  The option was there, so I clicked it. 

Thanks for any help

Edit: As a side note, I can plug on usb devices and they recognize they are plugged in (my droid 2 and sansa fuze both say connected)

---

### Post by daslinkard on 2012-07-28
The first thing that I would suggest trying would be to unplug the power cord from the laptop and then remove the battery.   Next hold down the power button for 30 seconds then proceed to plug in the power cord with the battery remaining out.  Push the power button and verify the PC turns on.  If not, let me know the results.

---

### Post by ftkatyowser on 2012-07-28
> **daslinkard said:**
> The first thing that I would suggest trying would be to unplug the power cord from the laptop and then remove the battery.   Next hold down the power button for 30 seconds then proceed to plug in the power cord with the battery remaining out.  Push the power button and verify the PC turns on.  If not, let me know the results.

The hard drive is spinning, and the light on the power switch is on, but the hard drive indicator light is not blinking.  No screen response

---

### Post by daslinkard on 2012-07-28
> **ftkatyowser said:**
> The hard drive is spinning, and the light on the power switch is on, but the hard drive indicator light is not blinking.  No screen response

Do you hear any kind of clicking noise when the PC tries to boot up?

---

### Post by madjr on 2012-07-28
try just using suspend instead of hibernate.

more on the hibernate issue:

[http://www.ubuntuvibes.com/2012/04/hibernation-disabled-by-default-in.html](http://www.ubuntuvibes.com/2012/04/hibernation-disabled-by-default-in.html)

[http://www.howtogeek.com/113923/how-to-re-enable-hibernate-in-ubuntu-12.04/](http://www.howtogeek.com/113923/how-to-re-enable-hibernate-in-ubuntu-12.04/)

---

### Post by ftkatyowser on 2012-07-28
> **madjr said:**
> try just using suspend instead of hibernate.

more on the hibernate issue:

[http://www.ubuntuvibes.com/2012/04/hibernation-disabled-by-default-in.html](http://www.ubuntuvibes.com/2012/04/hibernation-disabled-by-default-in.html)

[http://www.howtogeek.com/113923/how-to-re-enable-hibernate-in-ubuntu-12.04/](http://www.howtogeek.com/113923/how-to-re-enable-hibernate-in-ubuntu-12.04/)

Which I'll do as soon as I can boot the os.

---

### Post by ftkatyowser on 2012-07-28
Oops.  Double post

---

### Post by daslinkard on 2012-07-28
When you have the power cord plugged in does this light up or is it not lit either?

---

### Post by ftkatyowser on 2012-07-28
> **ftkatyowser said:**
> Oops.  Double post

> **daslinkard said:**
> When you have the power cord plugged in does this light up or is it not lit either?

That's lit.  It's orange atm because it's charging the battery.  If I take the battery out it turns white.

---

### Post by daslinkard on 2012-07-28
Personally I believe it is the HD....I've seen where other people have had the same issue and they have suggested taking the entire PC apart, disconnecting all components, reassembling and then rebooting.  In one forum there was a person jumping through all kinds of hoops to find out it was the HD that went bad.

---

### Post by ftkatyowser on 2012-07-28
> **ftkatyowser said:**
> Oops.  Double post

> **daslinkard said:**
> Personally I believe it is the HD....I've seen where other people have had the same issue and they have suggested taking the entire PC apart, disconnecting all components, reassembling and then rebooting.  In one forum there was a person jumping through all kinds of hoops to find out it was the HD that went bad.

That's what I was thinking.  I just wanted to  make sure before I went and got a new one, honestly.

---

### Post by daslinkard on 2012-07-28
Good luck....I'm subscribed to the post so if you have any questions or if I can be of assistance just let me know.

---

### Post by humor_76 on 2012-09-15
I have same trouble. After hibernate from Lubuntu 12.04 my HP Mini 210 won't start. When power on I have HDD led lighting 3 second and then off, but netbook is still working with blank screen and nothing happend.
Sorry for my English if I made a mistake(s).

---

### Post by yojimbosteel on 2012-12-24
Have you tried booting linux from a CD or flash-drive?

---

### Post by DrKaoliN on 2013-02-25
> **daslinkard said:**
> Personally I believe it is the HD....I've seen where other people have had the same issue and they have suggested taking the entire PC apart, disconnecting all components, reassembling and then rebooting.  In one forum there was a person jumping through all kinds of hoops to find out it was the HD that went bad.

I have the same problem, but most certainly it isn't caused by hardware malfunction. Otherwise, I wouldn't be able to write this from my alternative OS.

---

### Post by Toz on 2013-02-25
> **DrKaoliN said:**
> I have the same problem, but most certainly it isn't caused by hardware malfunction. Otherwise, I wouldn't be able to write this from my alternative OS.

Are you having the same problem on the same system as the original poster - running hibernate on a HP 210 and unable to get a running system afterwards? If so, you may be stuck in a resume loop. One way to get out is to use the **noresume** kernel boot parameter. This will wipe the resume image from the swap space, return swap to its original state, and restart the system. You can follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions [here]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") on how to temporarily boot with the **noresume** parameter.

---

