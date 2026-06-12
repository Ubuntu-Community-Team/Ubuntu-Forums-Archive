---
title: "How to transfers file from ubuntu to G1 phone?"
date: 2010-05-10
forum: General Help
---

### Post by thisisspeedy on 2010-05-10
Help please would like to put some music on my phone before I leave town thanks.

---

### Post by Nxion on 2010-05-10
From what i have found you should just be able to plug into your machine and Ubuntu will see it, are you getting an error?

---

### Post by thisisspeedy on 2010-05-10
I don't see it any where. I see when I go into disk utilities. But thats about it.

---

### Post by gsgleason on 2010-05-10
once you plug it in, there should be a notification on your phone to mount.  Do that, then it should show up on the desktop.  Works for me just fine.

An alternative is to enable USB debugging on the phone and get the android SDK for linux and use adb push.

---

### Post by thisisspeedy on 2010-05-10
ok thanks again guys. You are the best always so fast to answer as well.

---

### Post by Nxion on 2010-05-10
1. Connect your G1 to your PC via USB cable
2. Look at your G1 and in the Notifications bar (top-left) you will see a new icon that should appear
3. Slide the notification down to view the information and select "Mount..." 

Then it should show up on Ubuntu. if not let us know

---

### Post by adobrakic on 2010-06-16
For me, the Mount option on the phone doesn't show up. I have a G1 also, with Ubuntu 10.04. I'm not sure why it's not coming up, for it worked fine under Windows.

---

### Post by adobrakic on 2010-06-17
bump

---

### Post by twizler on 2010-07-01
Double bump -- when i attach my usb cable it seems that my G1 google phone doenst see it as being attached to a usb cable only shows as charging. 

BUMP!!

---

### Post by twizler on 2010-07-01
G1 android mount usb solved Ubuntu 10.04 usb mount solved fixed g1 mount issue Ubuntu 

**Solution:** 
> 1. Unmount your SD Card in phones settings.. .GO TO Settings-->Phone Storage -> Unmount SD CARD 
2. Turn off you g1 phone while plugged into the computer <long press red phone button> 
3. Turn on you G1 phone while plugged in and the magic MOUNT USB storage icon shows on phone! WOOT WOOT -->> click on new mount notification -- mount that puppy!!  

I also used an old XP computer first and did the settings unmount sd CARD -> Turn off phone -- turn on phone while plugged in and it came up with the mount option!! 

WOOT -- hope it works for the rest of you!. 
SOLVED! How to mount USB g1 on 10.04 Ubuntu -- i did every type of lsusb demesg and nothing would work ... i am an experienced Linux user and getting USB drives going back in the early days was not so simple ...  I tried all of what i KNEW and the damn thing would not mount   -- NOTHING! Turn off phone with sd unmounted turn on and magic -- why ?? no clue but it works! :) 

All else fails -- REBOOT the phone while plugged in?? sure WHAT THE HELL  rebooted everything else ?? magic ...

---

