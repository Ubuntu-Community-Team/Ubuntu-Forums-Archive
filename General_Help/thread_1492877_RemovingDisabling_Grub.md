---
title: "Removing/Disabling Grub"
date: 2010-05-25
forum: General Help
---

### Post by iCraig2009 on 2010-05-25
Hello All,
 
I am hoping someone can help me.
 
I have upgraded my motherboard and CPU and need to boot a CD-ROM to reinstall my OS. However I am unable to as Grub takes over and tries to load it self but fails.
 
How can I remove/disable grub to stop it doing this? 
 
I have already changed the bios to boot from CD Rom first but it still loads Grub and its getting frustrating now.
 
Please help!
 
Craig

---

### Post by philinux on 2010-05-25
There's a problem with the livecd you're using as it's not booting or it's the cdrom. Grub only shows up as the machine is trying to boot from the hard drive.

---

### Post by BoneKracker on 2010-05-25
> **philinux said:**
> There's a problem with the cdrom not booting. Grub only shows up as the machine is trying to boot from the hard drive.

The system's boot order may be set up in BIOS to try the hard drive first, or to only try the hard drive (as it would be in a properly-secured machine).

At any rate, there are a couple of things that can be tried:


a. If you haven't done so before, run an integrity check on the CD, or try it in other machine.

b. If you have two optical drives, try the other one (some BIOS will only boot from the first drive, which is often the DVD).

c. If your BIOS shows you a quick option to select a boot disk (typically "F12"), use it and select CDROM, bypassing GRUB.

d. If not, use the "setup" option (typically "F2" or "Esc"), and check in the BIOS to make sure the optical drives are being recognized and that booting from CDROM is not disabled.  If it's not disabled, try moving it to the top of the boot order.

e. Ensure cables to the optical drive are properly seated on both ends.

f. Install another optical drive to see if yours is bad.

g. Replace the cables.

h. Have the CMOS battery checked and replaced if it has a low charge (<30%).

g. Get a new motherboard.

h. Drink a pint of Wild Turkey and smash the computer with a baseball bat.

---

### Post by philinux on 2010-05-25
> **BoneKracker said:**
> The system's boot order may be set up in BIOS to try the hard drive first, or to only try the hard drive (as it would be in a properly-secured machine).


He's changed the bios to boot from cd. 
> I have already changed the bios to boot from CD Rom first but it still loads Grub and its getting frustrating now.


---

### Post by warfacegod on 2010-05-25
i. Glare at it in a mean and diabolical fashion.

I agree with these guys. Either the CD is bad or there's something wrong with the drive. I suggest using a USB jumpdrive instead of CD for installing.

Another thing to check is the CD-ROM's cable. Make sure it's securely connected to the board and the drive.

---

### Post by BoneKracker on 2010-05-25
Yeah, I think I was editing when you guys responded.  See above.

I missed where he said he had changed the order (so that invalidates a couple of those suggestions).

---

### Post by warfacegod on 2010-05-25
By the way, removing GRUB isn't likely to fix this problem. It *will*, however, probably make a bad situation much worse.

Like jumping off of a boat to escape a firing squad only to find out that there are 5,000 starving sharks in the water.

---

### Post by 98cwitr on 2010-05-25
You could always disconnect the HD and boot to disk to make sure it works.

---

### Post by mk1w86 on 2010-05-25
Can the machine boot any CD's? :-s

If it can try the Ubuntu CD in another machine and if that doesn't work try burning another one at a lower speed.

You should also check the MD5 sum of your downloaded iso image in case it is corrupt.  There is a guide here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by BoneKracker on 2010-05-25
Those are both good suggestions.

lol warfacegod

---

### Post by warfacegod on 2010-05-25
> **BoneKracker said:**
> Those are both good suggestions.

lol warfacegod

You'd be surprised at how many times a glare with a hint of bodily harm has worked for me. I'm becoming increasingly convinced that computers are more "aware" than we give them credit for. I've got my wife on an *old* Gateway AMD that I'm certain spends most of its time daydreaming about being a Mainframe.

---

