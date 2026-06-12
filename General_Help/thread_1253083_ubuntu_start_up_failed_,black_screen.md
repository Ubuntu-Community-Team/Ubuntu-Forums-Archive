---
title: "ubuntu start up failed ,black screen"
date: 2009-08-29
forum: General Help
---

### Post by jfloria on 2009-08-29
I have both ubuntu and kubuntu at start up kubuntu loads then screen go's to black.ctrl -alt delete to restart and it just repeats itself. Before this happened I was in sypnostic manager downloading programs for graphics. I am new, but I still believe.
Thanks Joe

---

### Post by NoaHall on 2009-08-29
Did you by any chance download the ati driver?

---

### Post by jfloria on 2009-08-30
Embarrassed I'm not sure, I realize this is all my fault.Blind folded with stupidity. 
Next time I see that I should keep a log on what I do.
When I try and load up at boot through kernel mode I get a screen that trys to auto adjust my screen settings and then it says out of range then thin lines run up and down my screen.
Thanks Joe

---

### Post by Liolikas on 2009-08-30
Can you still enter simple terminal login with ctrl+alt+F1?

---

### Post by NoaHall on 2009-08-30
Can you boot into recovery mode? If so, can you run "sudo dpkg-reconfigure xserver-xorg" and then if that doesn't fix it, try "sudo dpkg-reconfigure -phigh xserver-xorg"

---

### Post by jfloria on 2009-08-30
I will try these options, I am at work right now so I will try this later tonight. update you later 
Thanks
Joe

---

### Post by GSF1200S on 2009-08-30
> **jfloria said:**
> I will try these options, I am at work right now so I will try this later tonight. update you later 
Thanks
Joe

Ctrl+Alt+F1 to log into a command line session. While the above suggestion to use dpkg to reconfigure will likely work, you alternatively could go to the "Driver" line in your xorg.conf and replace ati or nvidia with vesa.

```
sudo nano /etc/X11/xorg.conf
``` 

Then scroll down to the line that says "Driver" and replace ati/nvidia with vesa.

Ctrl+O and Ctrl+X, then do:

```
sudo /etc/init.d/gdm restart
```

And see if you have any errors. If you get this far, understand you will be on 2d drivers. We will need to troubleshoot a little to get the 3d working, but at least you can use the computer!

**EDIT** If you cant get to a command line login, you can do everything ive listed from booting recovery mode. I think it even has an option to try and fix X for you (X is what you are having an issue with). Your looking for "Drop to root shell" or something similar. Good luck ;)

---

### Post by jfloria on 2009-09-02
Well I think its time to reload ubuntu! no problem though, everything is backed up.
I tried the boot codes and /etc/X11/xorg.conf told me I did not have authorization,and /etc/init.d/gdm restart - will restart my computer and my screen will have colored lines  up and down.
This forum is a wealth of information. Thanks for all the help everyone.
Joe

---

