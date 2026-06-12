---
title: "The Strange Case Of The Vanishing DVD"
date: 2010-01-20
forum: General Help
---

### Post by threedogs on 2010-01-20
I just bought an external USB DVD (ASUS SDRW-08D15-U) to use on a Kubuntu-based LinuxMCE system. The idea is to set up the computer in the basement and to retain the ability to play DVDs on the 2nd floor home theater. Unfortunately the DVD would not play movies, music, or show files when connected to the Kubuntu/LinuxMCE machine. I tested the drive on my windows laptop and it worked fine. Then I connected it to my Ubuntu desktop machine and got the same behavior as on the MCE machine.
This leads me to believe that my hardware is functioning fine, but I have an Ubuntu/Kubuntu issue. I figure if I can get the drive to work on my Ubuntu desktop, then I can apply the fix to my MCE machine.
I opened the Palimpsest Disk Utility (System>Administration>Disk Utility) and saw my internal DVD listed (ASUS DRW-1612BL). When I hot-plugged the external DVD it appeared underneath the internal drive. But here is the strange part - when I insert any type of media into the external drive it **Vanishes** from the list, accompanied by a repetitive pattern of clicking and whirring noises. Very mysterious.

---

### Post by phillw on 2010-01-20
Hi, 
a common 'gotcha' is not having (all) the codecs installed.

If you're at all unsure if you've got them all, head over here --> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)  

Regards,

Phill.

---

### Post by threedogs on 2010-01-20
I've been bitten by that one before. Everything is installed and the internal DVD plays pretty much as it should.

---

### Post by threedogs on 2010-01-21
Still trying to figure this out via Google. I've been reading alot about udev, fstab, and proc. I think udev is working because the device shows up correctly (until media is inserted). I don't think fstab is a factor because it only seems to deal with permanently mounted devices, not usb. Maybe /proc is where I need to look harder. Here are some screenshots that show what is happening before and after media is inserted in the usb dvd drive (The problem drive is at the bottom of the Palimpsest and /proc/scsi windows)

John

---

### Post by threedogs on 2010-01-24
Somewhat embarrassing but I connected it incorrectly. The drive has a special usb Y cable in order to supply power from 2 ports to the DVD. I had left this wrapped in its baggy and just used one of my straight usb connectors. In my defense, the instructions are unreadable (printed on small page in 35 different languages).

John

---

