---
title: "Webcam LED turns on/won't turn off after sleep or suspend"
date: 2010-08-10
forum: General Help
---

### Post by nihilion on 2010-08-10
Hello,

My webcam LED turns on whenever my Asus P50IJ laptop wakes up from sleep or suspend, and subsequently will not turn off. I can't tell if my webcam is actually activated or not, and furthermore the light beams right into my eyes and makes my lappy not so usable.

If someone knows why this might be happening or could possibly help me fix it that would be very much appreciated. I'm really trying hard to stick with Linux, but little things like this are making it difficult. I'm kind of a noob, but I'm trying so please be nice.

Thanks,
Nick

---

### Post by nihilion on 2010-08-10
bump

---

### Post by no2498 on 2010-08-11
i do not know how to fix it !

but webcam's use the usb ports 

so if you can find how to unmount/turn off that usb port the light will go off

hope i pointed you the right way

---

### Post by nihilion on 2010-08-11
> **no2498 said:**
> i do not know how to fix it !

but webcam's use the usb ports 

so if you can find how to unmount/turn off that usb port the light will go off

hope i pointed you the right way

Thanks, appreciate it. No idea how to do that, though. How do I mount and unmount things?

---

### Post by no2498 on 2010-08-12
make a new ?
you wont get much help on this 1
something like how do i mount/unmount usb things

---

### Post by chichken on 2010-09-18
If you have a cam with driver uvcvideo, you can rmmod/modprobe it, then the lights turn off.

In my case SL300 and SL500:
dmesg|grep  uvcvideo

[    8.016178] uvcvideo: Found UVC 1.00 device USB2.0 UVC PC Camera (17ef:480a)

rmmod uvcvideo ; sleep 2; modprobe uvcvideo

---

### Post by kanaida on 2010-10-15
I get the same thing in linux mint. It sucks, didn't happen at first, or at least I didn't notice. Some update caused it I think. Been trying different kernels trying to see if it helps, but nothing.

As a workaround I open cheese, then close it.

I also notice sometimes I get an "out of swap" error with some usb ahci something or other, guessing it's related.

---

### Post by GameboyRMH on 2010-12-12
Hey all, I had the same problem on an Asus P50IJ-X2, and here's how I fixed it (I'll make the instructions noob-friendly)

Open a terminal, and enter:

cd /etc/pm/sleep.d/
gksudo gedit 99-uvc-webcam-reset

Then paste the following code:

```

#!/bin/bash

case "$1" in
    thaw|resume)
        rmmod uvcvideo; sleep 2; modprobe uvcvideo
        ;;
    *)
        ;;
esac
exit $?

```Now save and close. In the same terminal run:

sudo chmod a+x 99-uvc-webcam-reset

And that's it! The webcam LED will turn itself off a couple of seconds after the laptop wakes up.

---

### Post by Bazilio on 2011-01-17
Works for Kubuntu 10.10 on Asus G1S!
Thank you!

---

### Post by chriswhat21 on 2011-02-19
Thank you [GameboyRMH]("http://ubuntuforums.org/member.php?u=915195").  I've been using the "open/close cheese method" for a few weeks now, Awesome.
Ubuntu 10.10 on my ASUS K50IJ
Now if I could just figure out my speaker/headphone problem...

---

