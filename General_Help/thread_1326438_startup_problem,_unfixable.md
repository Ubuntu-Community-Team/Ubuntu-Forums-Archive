---
title: "startup problem, unfixable?"
date: 2009-11-14
forum: General Help
---

### Post by tristen620 on 2009-11-14
okay so first i gotta give some information.
  laptop w/ vista 64.
  4 partitions on hard drive.
    #1 nfts containing windows.
    #2 recovery partition for windows.
    #3 nfts with a fresh install of kubuntu 8.1**
         ** It's an old copy, but i figured i would just upgrade after getting it installed to the new 9.1
#4 nfts for storage from the windows partition.


the thing is, after installing everthing was good, got to grub, could switch from one to the other lots of fun.  but then instead of selecting boot windows vista/longhorn i accidentally went into the system recovery for windows.

it loaded up okay, clicked the exit button to leave, then it just froze, i waited about 25 minutes in case it was just being stupid, then i hit Just enter, waited.. then escape, f1.  none of those evoked a response so i restarted it.

it loaded the initial boot screen fine, then when that goes away to switch to grub all i get is a black screen with a single white underline in the top left.  i said to my self, well that sucks. 

i popped in my kubuntu disc to try a live load from the disc and then just repair, won't work cant get past that silly black screen after boot, tryed boot order, selecting which to boot first, all sorts of different ways.

i'm currently looking for my vista disc to try that but i cant get to anything other than the bios or select which device to boot first (hdd/cd/etc).

so really my question is, is there Anything you or someone thinks i can do on my own, or am i going to have to go deal with Bestbuy and make them fix it.

---

### Post by tom4everitt on 2009-11-14
So if I understood you correctly:

You can access BIOS as normal.
You can't boot from harddrive in any way.
You are unable to boot from kubuntu 9.10 live cd (even after setting primary boot to cd in bios).
You are unable to boot from Windows Vista DVD (even after setting primary boot to cd in bios).

If this is correct it actually seems like you would have to go to your reseller. Before that I would try booting from one or two other live cds: try fedora or ubuntu, 32 or 64 bit (the one you didn't have in kubuntu). 

There's a slight chance that will save you. 

All this sounds really weird though, not even windows should be able to mess up your booting that bad :D

---

### Post by tristen620 on 2009-11-14
that what i was thinking as well, but it's just so weird that grub/my recovery partition didn't like each other that much.  :/

---

### Post by tristen620 on 2009-11-14
that what i was thinking as well, but it's just so weird that grub/my recovery partition didn't like each other that much.  :/

oh, i am posting these replies off my other laptop :D

but... i dont have any other discs to be able to try other live boots, and this laptop doesnt have a burner :(

---

### Post by tristen620 on 2009-11-14
could it be that the default os is now kubuntu and it does'nt have the driver/s for my video card (nvidia) so the black screen with the single blinking underscore is just what i get with that.   i really hope i can get this fixed i dont want to deal with the bestbuy guys /sigh Or have to reinstall all my stuff again -groan- (their answer is almost always well we will reformat it and reinstall and that should fix it).

---

### Post by tristen620 on 2009-11-14
well, i guess i'll just go to bestbuy :/ i'm so not patient, Thanks though, i'll see if i can get it working some other time.

---

### Post by tom4everitt on 2009-11-14
In case you didn't go yet, you don't actually have to burn! You can put it on a USB!

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by tom4everitt on 2009-11-14
Also, I don't believe that the problem is that Kubuntu is your default OS, cause that shouldn't matter when you try booting directly from a cd. Whatever's on your hard drive won't matter at all. 

What I think happened is that the Windows restore thing overwrote the bootloader on the hard drive (the code that boots your computer) in a bad way. This is easily fixed though by starting from some linux live cd. So if you could just get this working, I can guide you to get it going in 10 min or so actually.

---

### Post by tristen620 on 2009-11-14
sorry for the long absence, i fixed it.  all though i'm not exactly sure what the "it" was.

i removed my HDD put in the kubuntu 8.1 cd and viola it would actually load so then i knew it was directly related to my dumb hdd (was pretty sure anyways but still).  then i put it (the hdd) in my wife's laptop alone and tried it, and instead of just blackscreening i got grub error 17, so then i had something to go off of!

long story short my laptop is an OS racist, haha i don't think that kubuntu or any other unix/linux  is going to be working with it... i'll just remove grub and my kubuntu partition i guess, unless anyone's got tips on how to add drivers to my kub partition from windows  (both partitions are nfts).

---

### Post by tom4everitt on 2009-11-15
Okay, great! I was worrying you had already run off to best buy :)

The fact that it says grub error, rather than nothing at all, indicates that there's something wrong with your kubuntu installation.

I'm pretty sure a reinstallation of kubuntu would solve this. A few tips before you go ahead with this though:

-Do a manual install, so you can keep your windows partitions and remove the old kubuntu partition and replace it with a new one. 

-Don't choose ntfs as your kubuntu file system! Choose ext3 (if you want to be able to acces it from windows) or ext4 (if you want the best performance). This will most likely stop your windows restore thing from ruin your linux installation, as well as making linux run better.

-The problem is not actually drivers, but that you're kubuntu installation was messed up by windows restore. If it was driver issues, they would probably be solved in the latest kubuntu.

---

