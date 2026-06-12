---
title: "System Tray Icons Messed Up"
date: 2010-05-04
forum: General Help
---

### Post by Majorflam on 2010-05-04
I'm running Ubuntu 10.04. 

I just installed HP drivers for my printer tonight, and now my laptop is acting a little "buggy".

Some applications have froze, and my system tray icons are getting messed up. Sometimes the little power button dissapears and my username appears there instead, but it's not clickable. This means I have to shut down by using the power button on my laptop.

Also, as I am typing this message, the letters onscreen are lagging quite a bit behind my actual typing. It's as if there's something running in the background that is slowing everything down and messing things up.

Any help appreciated.

---

### Post by spiky001 on 2010-05-04
just to help with 1 of the problems you can use terminal

```
sdo halt
```
```
sudo reboot
```

save hard shutdown

you could try" top" in terminal to see whats happening

---

### Post by Majorflam on 2010-05-04
Just to add to this, sometimes when I try to restart or shut down I get redirected to the login screen. I need to power my laptop off in order to shut down.

---

### Post by Majorflam on 2010-05-04
Here is a screenshot of "top"

---

### Post by spiky001 on 2010-05-04
Has your pc started working better as you have shut a few things down?

found this I noticed Desktop couch running 3 times before 

[https://bugs.launchpad.net/desktopcouch/+bug/563738](https://bugs.launchpad.net/desktopcouch/+bug/563738)
dont know if it has anything to do with it

---

### Post by Majorflam on 2010-05-05
Hi, problem is persisting with the tray icons. Here's a couple of screenshots to explain better:

On the first screenshot, the date and time appear twice, as does the network icon... and there is no logout button.

On the second screenshot, it's pretty similar but not the same. It seems a bit random as to what icons get messed up.

---

### Post by Jags_FL on 2010-05-18
Gosh! same here... i'm too having messed up icons in system tray in a fresh install of Ubuntu Lucid 64-bit. I don't know if this makes any difference or not but it's under VirtualBox.

---

### Post by phompe on 2010-06-29
I'm having exactly the same, with the system tray icons! It seems completely random. I work with my laptop at home, as a laptop, and at work with a 24" (1920x1200) monitor attached as main (and only) screen. I thought it had to do with changing the resolution all of the time. Now, I have switched to mint and... having the same problems!! I have mint installed for two days now. It started after, again, attaching my external monitor and having an icon extra in the system tray for quick and easy access to monitor settings. After that the system tray icons were messed up.

Just my two cents
Peter

---

### Post by Dustout on 2010-07-11
I am experiencing the same issue, while not that bad today a sample is attached.

---

### Post by eagleton on 2010-07-11
What happens if you simply type 
```
killall gnome-panel
```
in the terminal?

Normally this helps against distorted icons, just try it a few times.
If it works, place a starter on the panel, and just click it if needed.

---

### Post by Majorflam on 2010-07-14
> **Dustout said:**
> I am experiencing the same issue, while not that bad today a sample is attached.

Do you have HP printer drivers installed?

---

