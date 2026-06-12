---
title: "noisy sound, possibly fan - Kubuntu 10.10"
date: 2010-12-04
forum: General Help
---

### Post by tpprynn on 2010-12-04
I'm a bit concerned about this. I've installed Kubuntu 10.10 tonight, and had tried it a week ago briefly without updates. Both times I've had this really loud sound which I'm guessing is the fan going a bit mad.

Is this related to a newer kernel or something? Is it dealt with easily?

This is a Toshiba Equium laptop from 2 1/2 years ago. I've got the Powersave setting on now in the hope this might stop it happening while I'm trying to read up on this and get advice.

After all the observed Linux progress since I've been using it I'd be quite annoyed if something botched in the OS kills my laptop.

The computer got quite hot, even though its feet are rested on a wooden board that normally prevents this.

Thanks.

---

### Post by tpprynn on 2010-12-04
Being delirious and in need of sleep I've just lost a follow-up post...

The gist was, after reading up on this matter to the best of my ability I think I need to add:

acpi=copy_dsdt

to etc/default.grub and run sudo update-grub in the terminal.

I just want to check the form - can I just add this line to that file anywhere minus a hash and it will become implemented after ...update-grub? (Or that and a reboot.)

Or does it go in a particular place in the file?

The temperature has gone down from 87 to 68 - my old Vista norm - since I turned off desktop effects, so I hope I've got this somewhere near correct, that I can re-enable them without the heat trouble once this kernel line's added, that is when I get up in a few hours...

If someone can confirm I'm doing the right thing. Thanks.

---

### Post by efflandt on 2010-12-04
The two lines below in /etc/default/grub are where you can put kernel boot parameters (space separated list within the quotes).  The 1st line is for regular boot, or the 2nd line (which has nothing set in it now) is for ALL boots including normal and (recovery):

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Use **gksu gedit** or **sudo nano** to edit **/etc/default/grub** (as root).  Then do **sudo update-grub**.

---

### Post by tpprynn on 2010-12-06
A blast of compressed air round the back copper-coloured vent has solved this. Temperature has remained 50-60 degrees for a long time and the machine is so quiet now it could almost be off.

Given all the stuff about this I wonder how much of what some of us have been reading is relevant. Still, at least it seems there's no need to have a grumble about Linux.

---

