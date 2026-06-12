---
title: "How to image a Windows hard drive?"
date: 2010-04-30
forum: General Help
---

### Post by jubantu on 2010-04-30
I have an unused laptop computer with an WindowsXP installation lying around. I decided to use this computer with Ubuntu for the next few months but it is absolutely crucial to preserve the current WindowsXP state somehow. Is there a safe way to "conserve" that very Windows installation as an image so I can recopy it later on? I'd like to clean out the computer completely to install Ubuntu afterwards. After using Ubuntu I want to install the old WindowsXP again as it was before. Is that even possible? Power on and XP boots as before? I mean driver, accounts, passwords etc? What would you recommend?

---

### Post by limey_rick on 2010-04-30
So I think you have a couple of options:

[1] Boot into XP and create a backup that you can restore onto the same PC
[2] Create a drive image that you can copy back to the PC

For [1], you should be able to do this with the XP backup tool to an external USB drive for example. 

For [2], use something like Clonezilla to create a boot CD and then create a drive image on the USB drive which you can restore later. 

[http://www.clonezilla.org/](http://www.clonezilla.org/)


Not sure if that's exactly what you needed, but let me know if this helps (or not).

---

### Post by jubantu on 2010-04-30
Hey thanks, I forgot to mention a few things. The laptop is a corporate pc and I'm very restricted inside of WinXP. No admin rights etc... Maybe it is best to boot a Linux live cd and create the image from there including the MBR. I haven't done anything like this before but it is absolutely crucial that the system works and boots as before once the original settings are recopied. Any ideas on that?

---

### Post by Megaptera on 2010-04-30
As it's a corporate machine, have you asked your IT team for their help in what you're trying to do?

---

### Post by dino99 on 2010-04-30
you feel like a kid trying and testing everything, let me know your boss email i'll beg him more rights because you have some time to waste  :lolflag:

---

### Post by conradin on 2010-04-30
Ask your Boss if before modifying company hardware. Instead of cloning your hard drive, why not take out the hard drive and place an new hard drive in the computer and install Linux to that?

Other options include dual booting, where later, you could use a live CD and gparted to resize the windows partition to its original size. But again, if you want to leave your original intact, just don't modify it at all and use a different hard drive.

---

### Post by robert shearer on 2010-04-30
Well, if it were me then I would buy another hard drive and physically swap it out for the current one.

Load and use Linux from the new one.

Then, when the time comes, swap back in the old one.

Thats an acceptable > absolutely crucial  fix for me.

Existing hard drive and set-up unaltered.

---

### Post by jubantu on 2010-04-30
> **robert shearer said:**
> Well, if it were me then I would buy another hard drive and physically swap it out for the current one.


The best solutions are often simple, yet unexpected. *:) *
Thanks!

---

