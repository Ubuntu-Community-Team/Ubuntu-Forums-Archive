---
title: "Any body using an Arduino with a usb to serial cable?"
date: 2009-10-30
forum: General Help
---

### Post by hanzomon4 on 2009-10-30
I've having issues loading my board. It works in OSX on the same machine+board but not in linux, I keep getting this error```
Native lib Version = RXTX-2.1-7
Java lib Version   = RXTX-2.1-7
Binary sketch size: 896 bytes (of a 14336 byte maximum)

avrdude: stk500_recv(): programmer is not responding
avrdude: stk500_recv(): programmer is not responding

```

Through testing I figured that it must be something with the ftdi driver. I came to this conclusion because it worked with Karmic alpha6 through beta. So I did a search and found this [bug report]("http://www.pubbs.net/kernel/200910/12236/").

The important part is this ```
 2) a couple of regressions in 2.6.31 (stalled reads and unthrottle race)
    due to changes in the tty layer.

Please have a look at it so we can get something back-ported to stable as the
ftdi-sio driver is currently completly broken and unusable due to the stalled
reads.

```

Does that mean that arduino over ftdi is borked for the current kernel?

---

### Post by bbikebbs on 2009-11-12
Anyone??  I'm looking at buying a kit but now I'm not so sure.

---

### Post by gatonero on 2010-01-07
Anybody knows a solution for this?

---

### Post by gatonero on 2010-01-08
Following all the instructions on [https://bugs.launchpad.net/ubuntu/+source/avrdude/+bug/228670](https://bugs.launchpad.net/ubuntu/+source/avrdude/+bug/228670) burning the bootloader via USBtiny and arduino-017 I was able to upload sketches again without any errors :D

---

### Post by mountain_goat on 2010-03-08
Hey peoples,
You've probably sorted this problem out by now.
I cam across the post as I have put Lucid on my small Dell D420 and want to get back into programming my Arduino again.

I had been previously using 9.04 and arduino-0017 on the bigger Dell D830 and all was good with programming and developing. Even on my mac mini I can plug th eArduino in and run up the Arduino IDE and all is well.

My problem is with Lucid and trying to get the Arduino-0018 IDE to communicate to the board.

I am not able to select a communication port in the Arduino IDE.

I known the FTDI drivers are there, I have removed brltty as suggested on the Arduino 'Getting Started' section.

---

### Post by Pschmitz on 2010-06-27
Having similar issues, thought Id bump this thread while I continue the search!

---

### Post by mountain_goat on 2010-06-27
Hey pschmitz,
if you are still having troubles, I will try connecting to my Arduino.
Just need a few days as I am currently in the French Pyrenees  for a local fete and will be back in my neck of the woods on late Tuesday, so will be able to try for you on Wednesday.
What version of ubuntu are you using and on what type of system.
I use a Dell D830 laptop and since my last post I have been able to get it working ok again. May possibly have been a kernel issue, though not sure.

---

### Post by Ocxic on 2010-06-27
just to point out, the new arduino's are USB no serial required.

---

### Post by wasutton3 on 2010-07-09
Yes, but there are still some older devices floating around that use the usb to serial cable. I know i am having issues with my sanguino with that right now.

---

