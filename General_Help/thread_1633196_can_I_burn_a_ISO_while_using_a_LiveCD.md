---
title: "can I burn a ISO while using a LiveCD?"
date: 2010-11-29
forum: General Help
---

### Post by 0949er on 2010-11-29
As the title suggests, I am stuck on my ubuntu LiveCD with a faulty burn of ubuntu. I was wondering if it is possible (while booted up in the ubuntu liveCD) to burn a new cd with a (hopefully) non-faulty image? I need to do this while using the liveCD because I have a computer without any operating system on the hard drive to burn a new image of ubuntu (*deep breath*)

any help? thanks guys.

---

### Post by jocko on 2010-11-29
If you only have one optical drive there is no way. The live cd system needs to be able to read from the cd.
But you can make a bootable usb (System-->Administration-->Startup Disk Creator).

---

### Post by dcstar on 2010-11-29
> **0949er said:**
> As the title suggests, I am stuck on my ubuntu LiveCD with a faulty burn of ubuntu. I was wondering if it is possible (while booted up in the ubuntu liveCD) to burn a new cd with a (hopefully) non-faulty image? I need to do this while using the liveCD because I have a computer without any operating system on the hard drive to burn a new image of ubuntu (*deep breath*)

any help? thanks guys.

Try adding this to the kernel boot string:
```
toram=filesystem.squashfs
```
This allows my GPARTED boot image to be fully loaded into RAM and gives me access to the unlocked partition, so it might also allow access to the drive after you boot up the Live CD.

Let us know if it works.

---

### Post by Robert Lutken on 2010-11-29
If you have a second DVD drive yeah?

---

### Post by 0949er on 2010-11-29
hey I will try your option on the loading to ram, however, this is going to sound stupid, but how do I give parameters to the LiveCD startup? It goes into the GUI automatically and do not really see an option of adding custom parameters. Plus, once I do add custom parameters, how do I continue with loading ubuntu?


No I do not have access to a second drive (my only one)

---

### Post by madjr on 2010-11-29
> **0949er said:**
> hey I will try your option on the loading to ram, however, this is going to sound stupid, but how do I give parameters to the LiveCD startup? It goes into the GUI automatically and do not really see an option of adding custom parameters. Plus, once I do add custom parameters, how do I continue with loading ubuntu?


No I do not have access to a second drive (my only one)

press scape before it starts loading the live desktop?

heh this should be interesting, i love all the weird things we can do

---

### Post by wilee-nilee on 2010-11-29
> **0949er said:**
> hey I will try your option on the loading to ram, however, this is going to sound stupid, but how do I give parameters to the LiveCD startup? It goes into the GUI automatically and do not really see an option of adding custom parameters. Plus, once I do add custom parameters, how do I continue with loading ubuntu?


No I do not have access to a second drive (my only one)

If you have a thumb drive that is at least 2 gigs you can load the Ubuntu with unetbootin, then use it to boot, then download another Ubutnu ISO and or burn the original not the one running the thumb to a cd.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by 0949er on 2010-11-29
ok I downloaded a liveCD and am currently download a 64bit version of ubuntu (is this ok? to run 64bit? I do have a 64 bit processor). 

the liveCD I am using (dont remember the name, downloaded it at the GF's house) loads into RAM so that I can mount and unmount the CD-rom drive. I will try to reburn the image at SLOW speeds to see if that helps any. if not, I will then try the USB option (I have a 2.0 GB usb drive). I will keep you guys posted.

Just real quick, should I do a 64bit version? or is it overkill? I have 2 GB of ram. (DDR2)

---

### Post by jmszr on 2010-11-29
0949er,

64-bit will work fine, I've been using 64-bit Ubuntu for a couple+ years.

---

