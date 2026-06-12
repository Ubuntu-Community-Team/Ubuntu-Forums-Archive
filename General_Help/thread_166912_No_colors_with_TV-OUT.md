---
title: "No colors with TV-OUT"
date: 2006-04-27
forum: General Help
---

### Post by tomplast on 2006-04-27
I have edited my xorg.conf so I have cloned my monitor to my TV but on the TV I only get a grayscale picture :/. Can anyone tell me why it's like this? I live in Sweden (PAL-B I think) and I'm using a S-VIDEO cable and I have a Samsung HD-READY tv.

---

### Post by coolclassic on 2006-04-27
I had this problem but it was a long time ago so I can't remember how I fixed it. But what I do remember was It was a very simple fix, it was either the output channel in your software or input channel on you tv av1 or av2 ect.

---

### Post by Jason_25 on 2006-04-27
S-video will only carry a 480i signal.  You will need component, vga or dvi/hdmi.  Living in europe you might need a special scart cable I think.

---

### Post by Mr Green on 2006-04-28
You should check and see if it works in Windows just to make sure you have all the cables right. I have the same problem with black and white and can't get it to work under Linux. But if you make it work, please post your xorg.conf file. At least if you are using an ATI card!

---

### Post by tomplast on 2006-04-29
Yeah it's working with a COMPOSITE cable but the quality isn't the best :/

---

### Post by axm on 2006-06-04
Could not test anything yet (TV/resolution is not recognized), but after 2 days searching I got:

a) Try, if your video card supports Composite instead of S-Video (as you did), black-white on TV means the TV interpretes the S-Video signal as Composite.

b) In your case you should try a different port on your TV. if there is any. There was a guy replying to the nvidia-tvout-newbie-howto who had a black/white one a color bad quality and a color good quality port (hope I remember correctly).

---

