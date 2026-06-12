---
title: "Should I reinstall ubuntu?"
date: 2010-03-29
forum: General Help
---

### Post by mikeprosceo on 2010-03-29
Below is my post from a few days ago.  I have not gotten any reply help so I am assuming it is a puzzling question.  My question then is should I re-install ubuntu?  If so should I delete the old one first and then reinstall 8.04 or try to upgrade to the next version?  Thank you for any help. - Mike Prosceo

I am using Ubuntu 8.04. Most of my Administration functions have stopped working. If I click on Hardware Drivers, Hardware Testing, Log In Window, Software Sources, Synaptic Package Manager, and Windows Wireless Drivers my pointer turns into the timer wheel, so I know it is working, but then it just disappears and nothing happens. When I click on Update Manager my computer freezes. If I try to update through the red Updates Available arrow at the top of my screen my computer freezes. I can update through terminal but the red arrow never goes away. I also have 17 updates that won't update. I have tried them one at a time through terminal but they just freeze the computer. The only way to unfreeze it is to shut the computer down. Please can anyone help me get these functions back? I am a basic novice but follow instructions real well. Thank you for your help. - Mike Prosceo

---

### Post by Jay Car on 2010-03-29
I don't know what sort of computer you are having the problem with, but I encountered nearly the same thing on a Dell 9 mini netbook last week. Same version of Ubuntu, same behavior. It ended up being hardware problem.  They are replacing the SSD.  

What sort of computer are you having the problem with? Have you tried booting from a Live CD?

---

### Post by mikeprosceo on 2010-03-29
I am running an HP Pavilion dv5000 laptop. No I will try that.

---

### Post by ghostborg on 2010-03-29
Check to see if your hard drive is full, during an encoding bug a file in my tmp directory kept growing until the disc was nearly full. I had to go in and manually delete it.

---

### Post by samborambo on 2010-03-29
Yeah, check and see if the root filesystem is full first:

```
df -h
```

The root filesystem, "/", should be at the top of the list. Make note of the device that the root FS is on. You'll need that in the next step.

If it's not full, reboot the computer and choose the single user mode recovery console from grub. Once at the console run fsck on the root filesystem to check for any filesystem corruptions:

```

mount -o remount,ro /dev/sda1
fsck -V /dev/sda1
```

/dev/sda1 is the likely device holding the root FS. Change this as necessary.

The mount command remounts the root filesystem as read only so that you can check it with fsck. If fsck reports inconsistencies, boot the computer from a live CD and run fsck again with the -a option to automatically fix the errors.

If that fails, reinstall the latest ubuntu. An install only takes 20 minutes anyway.

Sam.

---

### Post by mikeprosceo on 2010-03-29
Sam thanks, I did as you said and it said my device was clean.  I guess that means installing the newest ubuntu.  Do I uninstall the old one first?  If not, will I lose everything on my current ubuntu when I install the newest one over this one?  I thought I read that you have to upgrade in steps?  Is that correct or can I go directly to the newest version?  Again, thanks for your help. - Mike

---

### Post by 2hot6ft2 on 2010-03-29
You would have to upgrade in steps as far as I could tell. I usually do fresh installs but I did and upgrade from 8.10 to 9.10 on a usb install and it only gave an option for the next version up at each step.

---

