---
title: "Fresh install of 10.10 appears to have disallowed me to access bios"
date: 2010-12-20
forum: General Help
---

### Post by Jemeyr on 2010-12-20
I had freshly installed 10.10 6 weeks or so ago and learned to get by with ubuntu after a long time as a guy who knew just windows but knew it pretty well.

I have an Asus C90S and I replaced my hard drive today. I booted from an ubuntu cd, and partitioned my hard drive and installed ubuntu 10.10 to one of the partitions. I intended to install Windows from a flash drive, but upon rebooting, discovered that the screen in which I normally access the bios is no longer there.

When I boot, a cute animated "Asus" logo appears, then I am given the option to "Login to <computer name>:" However, this disappears rather quickly, and is replaced with the pretty graphical login screen.

Briefly between the Asus logo finishing and the text Login screen, I am able to type, but my normal smash-the-f-keys-and-delete method of getting into the bios yields only a long string of these guys: [^22

Has installing ubuntu somehow updated my bios without my knowing? Am I missing something extremely simple? I need to install windows and installing it from a cd appears to be much more of a hassle than it's worth (netbook cd drive and pre-installed windows 7 drivers don't want to get along)

Thanks.

Oh, and everything is 64 bit, if that makes a difference. Also, apologies if there is a more specific section for this that I missed.

---

### Post by garvinrick4 on 2010-12-20
Does not have anything to do with Ubuntu. Have to be quick but should be same keys.
Like F2 or F10 or some esc key.

---

### Post by argedion on 2010-12-20
> 
I have an Asus C90S and I replaced my hard drive today

> Does not have anything to do with Ubuntu. Have to be quick but should be same keys.
Like F2 or F10 or some esc key.

garvinrick4 is right. Ubuntu or any OS does not affect the BIOS. I believe the culprit is probably that hard drive you just replaced. You probably need to go to the Asus web site and see if there is an updated BIOS for that computer.

---

### Post by mastablasta on 2010-12-20
you wrote that you replaced the hard drive. it might be that asus was using something from it when booting. check the Asus site on bios update and instructions on how to access bios correctly.
 
as already mentioned OS can't do anyhtign to BIOS as bios is on motherboard. you can reinstall or flash it. but check for instructions for that, because they all do it differently.

---

### Post by Jemeyr on 2010-12-20
Thanks guys, Figured it out.

The window of time in which I had to press F2 to enter the bios was extremely small. 

After about half a dozen reboots I was able to get it. I think that ubuntu was just loading  too damn fast.

---

