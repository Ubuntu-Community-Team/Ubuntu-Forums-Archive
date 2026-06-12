---
title: "Making a Webcam Work  (Read details please)"
date: 2010-01-06
forum: General Help
---

### Post by teward on 2010-01-06
Okay, I've got a small webcam for my laptop that doesn't come with Linux drivers, only Windows drivers.

Any linux-based drivers that came with Ubuntu 9.04 that might work don't.  How do I make the Windows drivers for the webcam work with the hardware so I can use the webcam?

---

### Post by switch10 on 2010-01-06
I have a logitech cam that I couldent find "drivers" for, I then installed a program called "cheese" and it just worked.  

but I think you are looking for ndiswrapper to install windows drivers....  


good luck with that.

---

### Post by teward on 2010-01-06
yeah, i'm not a fan of looking at the tutorial for ndiswrapper, so if any techs can help with that if "cheese" fails, i seek your advice/information/knowledge for help.

---

### Post by iponeverything on 2010-01-06
ndiswrapper is for network drivers.

I don't think that there is a ndiswrapper like alternative for webcams, so your using windows driver is probably out of the question.

So, your alternative is to see if there is a native linux driver for the device.

---

### Post by teward on 2010-01-06
> **iponeverything said:**
> ndiswrapper is for network drivers.

I don't think that there is a ndiswrapper like alternative for webcams, so your using windows driver is probably out of the question.

So, your alternative is to see if there is a native linux driver for the device.

google does nothing for that.  I'll test and see if having "cheese" helps, if it does, then i'll mark this as resolved, if not i'll bump it up here again.

---

### Post by teward on 2010-01-07
Alright, it works now (its being detected), but through testing, the webcam adjusts the white balance to make the image viewable (i'm in a dimly lit room), then after a minute, it goes really dark and loses the white balance.  any ideas on how to fix it?

Another interpretation of this is that it autoadjusts for the darkness, then removes the autoadjust and makes everything dark.  Any idea on how I can correct this?

---

### Post by Sef on 2010-01-07
Read the [Ubuntu Wiki "Webcam"]("https://help.ubuntu.com/community/Webcam").

---

### Post by teward on 2010-01-07
looked at its solution, didnt help because it wouldnt run.  Aborted.

Need another solution if there is one.

---

### Post by teward on 2010-01-07
bump.

any solutions to the brightness adjustment?

New Info:  It basically stops recognizing colors, and goes into grayscale, but mostly white and black unless in a bright room, even then, its overly bright.

---

### Post by teward on 2010-01-12
bump.

---

### Post by Sef on 2010-01-12
What webcam do you have?

---

### Post by mywebbags on 2010-01-12
Pits:popcorn:

---

### Post by teward on 2010-01-13
Its a Logitech webcam that hooks onto the top of the laptop screen.  I think its a QuickCam, but I can't be 100% certain.

---

### Post by no2498 on 2010-01-14
open cheese click edit preferences 
set it

also look in the help files

---

