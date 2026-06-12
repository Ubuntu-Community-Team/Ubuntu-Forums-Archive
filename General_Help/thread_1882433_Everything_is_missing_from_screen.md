---
title: "Everything is missing from screen"
date: 2011-11-17
forum: General Help
---

### Post by clucas on 2011-11-17
Don't know what I did but this is my problem: The only thing that shows up on the screen when I boot up is the wallpaper and "File..Edit..View..Go..Bookmarks..Help". That is all! No date, time, icons for the network or Bluetooth. No programs listed along the left. I have to shut down the computer. There's no way to even restart or exit out.

Using 11.10.

The only thing I did just before it happened was I had Compiz open and was just looking things over. I don't think I enabled or disabled anything. When I closed that the screen showed up as I described above.

---

### Post by raja.genupula on 2011-11-17
try to reset unity panel

unity --reset
unity --reset-icons

and try again. make sure that you have enabled unity plugin in ccsm.

---

### Post by clucas on 2011-11-17
I'd love to try that but how do I do that? I can't get a terminal or any app.

---

### Post by DeMeNt3d on 2011-11-17
(Ctlr+Alt+t) Opens up a new terminal try that, i had the same problem and i just ended up rebooting the whole os.

---

### Post by clucas on 2011-11-17
I was able to get to CCSM and made sure the unity plugin was enabled. That worked!! Thanks!

---

### Post by Mark Phelps on 2011-11-17
If the reset commands don't fix it, then you will need to follow the steps in the link below:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

