---
title: "Unsupported Webcam works temporarily, out of box?"
date: 2009-08-24
forum: General Help
---

### Post by kestal on 2009-08-24
**Hardware:**
- Intel CS430 Webcam

**Programs/Scripts Tested:**
- Camorama
- Cheese
- Easycam 2
- Emesene 1.5
- spca5xx drivers

**Whats Going On?**
- I installed Emesene 1.5 and out of the box, my webcam works? The catch is, that if I close the window and re-open it. It turns all messy.
- The webcam does not work in any other software that I tested.
- I tried a few drivers, but to no avail.

**Video**
- I made a video, its [right here ( link)]("http://www.youtube.com/watch?v=B2n31QP88SE&fmt=18")

**lsusb**
> Bus 006 Device 002: ID 0733:0430 ViewQuest Technologies, Inc. Intel Pro Share WebCam


**lsmod | grep video**
> video                  25360  0 
output                 11008  1 video
videodev               41600  1 gspca_main
v4l1_compat            21764  1 videodev


So is this a fluke? This webcam never worked for me, now all of a sudden for the first time when I turn on my computer, I can run my webcam once? what does that mean? lsmod | grep video doesn't change before or after.

Weird thing is, I tried spca5xx after and nothing changed.

---

### Post by P4man on 2009-08-24
I had the same with a logitech fusion. It would work ONCE, and once only.
Its a problem with the firmware, and the only known "solution" was to hook it up to windows, then, sometimes, it would work on ubuntu again... once !

The better solution for me was tossing the cam in a bin and buying one that actually works.

---

### Post by kestal on 2009-08-27
Though wouldn't the fact that it works, even temporarily, mean something else may be going on? I mean, could it be something with libmimic?

I normally would just dismiss this but the picture (after some gamma setting changes) looks crystal clear.. I just do not expect that from a webcam that is not supported at all. Whatever causes it, lets me go on webcam. Isn't there some way around this, even partially, to trick webcams into thinking that its the first time since restart? or finding out what changes between the initial attempt vs the next?

Previously, this never happened to me, and I've been playing around with Ubuntu since before Gutsy.

---

### Post by P4man on 2009-08-27
I dont remember the specifics, but I had to look VERY hard to find an explanation. What I found sounded a lot like this:

[http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities](http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities)

but with an added comment that the linux driver could not reset the webcam's undefined state for some reason, firmware bug or lacking info,  and the only workaround (at least back then) was plugging it in a windows machine and the windows's driver included the necessary code to "reset" the cam and make it working again.

Anyway, considering what a webcam costs, I couldn't be bothered to spend too much time on it. Might be different if yours is integrated in a notebook tho

---

### Post by kestal on 2009-08-27
nope, not integrated. just seems off to me. I dont even have to boot into windows, I can just restart, or even just ctrl+alt+backspace and its fine again, and only in emesene. (not cheese, camorama, etc).

True point about getting a new one, I will just have to make sure that I get one that is supported lol. Thanks for the replies.

---

