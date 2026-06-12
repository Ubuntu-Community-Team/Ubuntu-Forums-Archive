---
title: "Can't boot from CD."
date: 2010-05-27
forum: General Help
---

### Post by dragos240 on 2010-05-27
From some reason I cannot boot from a livecd. I was able to load the vmlinuz and the initrd.img from the cd. The CD even got to "ready.".

Nothing happened after this. This is with a liveCD and a liveUSB. I'm not sure what's happening, because I've installed countless distros, and I'm not sure why, but it's just this laptop.

---

### Post by irv on 2010-05-27
There are only three things that cause this problem.
1. CD/DVD not set to boot from CMOS
2. Bad CD/DVD
3. Bad CD/DVD Drive.
You can eliminate the first two if you can boot with another Bootable CD/DVD. (Like a Windows install CD).
If you can't then start by checking to make sure you are set to boot from the Drive in your CMOS and also that it is set to boot first.
If you can boot from another bootable CD then download a new ISO image of Ubuntu and re-burn a new CD.

---

### Post by dragos240 on 2010-05-27
What's really odd though is other devices can boot the CD. Other devices can boot the USB as well. THIS computer can boot a CD to "Ready.", but won't go any farther. Same with a liveUSB. I also tried using an external CD drive, it only booted to "ready" as well. The external CD drive works on my netbook, the USB drive worked on the netbook as well, and even the livecd worked on the netbook. I'm not sure what's happening with this laptop/tablet hybrid. It's an averatec c3500, if that helps.

---

### Post by irv on 2010-05-27
> **dragos240 said:**
> What's really odd though is other devices can boot the CD. Other devices can boot the USB as well. THIS computer can boot a CD to "Ready.", but won't go any farther. Same with a liveUSB. I also tried using an external CD drive, it only booted to "ready" as well. The external CD drive works on my netbook, the USB drive worked on the netbook as well, and even the livecd worked on the netbook. I'm not sure what's happening with this laptop/tablet hybrid. It's an averatec c3500, if that helps.

I'm not fully understanding what you mean by "Ready." Are you saying you can't boot and run the live CD in this laptop but you can in the netbook? And do you mean by ready that you can read the CD in a up and running OS but can't boot from it?

---

### Post by dragos240 on 2010-05-27
After loading the initrd and vmlinuz, it will say "ready.". I think I solved the issue, it *seems* to have been a bad burn.

---

### Post by irv on 2010-05-27
That's the first thing that came to my mind. I have had this happen to me also.

---

### Post by dragos240 on 2010-05-27
"Disabling lock debugging due to kernel taint"

And then it stops. It won't go any farther. Let me check the CD again.

---

### Post by dragos240 on 2010-05-27
Nope, it's not the CD. Works on another computer.

---

### Post by dragos240 on 2010-05-27
Isn't this a known issue?

---

### Post by dragos240 on 2010-05-27
[Wait, I got it.]("http://forums.linuxmint.com/viewtopic.php?f=46&t=47130")

---

### Post by dragos240 on 2010-05-27
Yep, It's installing now. Adding nomce worked. No idea why I needed that. But it works now.

---

