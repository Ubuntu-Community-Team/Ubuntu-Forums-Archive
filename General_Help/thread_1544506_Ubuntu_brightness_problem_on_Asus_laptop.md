---
title: "Ubuntu brightness problem on Asus laptop"
date: 2010-08-02
forum: General Help
---

### Post by kwbauson on 2010-08-02
I recently got an Intel Asus laptop, and I can't use the brightness applet, or the keys on the keyboard.  I've tried to run smartdimmer, but it says "init_nvclock() failed!"  When I usethe keys, the other fn keys stop responding also.
Does anyone have a solution?  Thanks!

---

### Post by Cavsfan on 2010-08-02
Did you obtain the manual from Asus? My daughter had an Asus laptop and you had to change the volume 
in the bios or it would be too quiet. Best bet download the manual.

---

### Post by TheNerdAL on 2010-08-02
Can you give us the exact model? Maybe this would help people who had the same issue as you have. :)

---

### Post by kwbauson on 2010-08-02
The sound problem only happens after I try to adjust the brightness.  It's an Asus K501.

---

### Post by Cavsfan on 2010-08-02
> **kwbauson said:**
> The sound problem only happens after I try to adjust the brightness.  It's an Asus K501.

Try this link. There are more than one K501
Click on Notebook on the left and then look for "K50 Series" and find your model and you should be able to download the manual

_[http://support.asus.com/download/download.aspx](http://support.asus.com/download/download.aspx)_

It seems kind of slow, but I'd give it time...

---

### Post by Cavsfan on 2010-08-02
If that doesn't do it, hopefully it's fairly new. I have heard there support people are very good!
Call their support number if you need to.

---

### Post by jasonodoom on 2010-08-02
Try the Brightness Applet, right click and add to panel on the Ubuntu panel to add it.

---

### Post by kwbauson on 2010-08-02
I've already tried the brightness applet.  When I try to click to change the brightness, the meter disappears.

---

### Post by SHL on 2010-08-02
> **kwbauson said:**
> I've already tried the brightness applet.  When I try to click to change the brightness, the meter disappears.

I have the same problem that the brightness applet disappears when clicking it, on my Asus UL30A, on Ubuntu 10.04. 

This has worked well on 9.04 and, I'm quite sure, on 9.10 too.

The Fn-keys works but with a HUGE delay, like 30-40 seconds or so (if stepping up the brightness multiple times, all steps come at once after 30-40 seconds or so).

---

### Post by kwbauson on 2010-08-02
On mine, the brightness notification shows up every once in a while showing that the brightness is changing, but it doesn't.

---

### Post by TheCowGod on 2010-10-28
Did any of you guys ever find a fix for this? I am having the same issues. I didn't update to Lucid because of this and just tried Maverick and still have the same issue. Everything worked fine in 9.10 and I have tried seemingly every fix I can find by googling. I am on an Asus P50IJ

---

### Post by kwbauson on 2010-10-29
The new kernel solved the problem for me (I tried out maverick alpha).  However, I am no longer using Ubuntu, so I don't know if the problem is still there.  Perhaps you could check for kernel updates, they often solve hardware problems.  I'm using an Asus K501, so we might be using different hardware.  I've got an Intel graphics card using the i915 kernel driver.  There also might be something in your hal configuration if you've not checked that out.

---

### Post by thusi87 on 2010-10-30
> **SHL said:**
> I have the same problem that the brightness applet disappears when clicking it, on my Asus UL30A, on Ubuntu 10.04. 

This has worked well on 9.04 and, I'm quite sure, on 9.10 too.

The Fn-keys works but with a HUGE delay, like 30-40 seconds or so (if stepping up the brightness multiple times, all steps come at once after 30-40 seconds or so).

The same problem with asus f5gl. It worked well with 9.04, but since then the delay is present. But the brightness applet seemd to work well until now. In 10.04 some times the applet dissapears from the panel randomly. When i log out and re-log on the applet re-appears. Furthermore the Top panel becomes messy and jumbled some times as well. Getting a bit annoyed with ubuntu lately coz of this issue.

---

### Post by Cavsfan on 2010-10-30
> **thusi87 said:**
> The same problem with asus f5gl. It worked well with 9.04, but since then the delay is present. But the brightness applet seemd to work well until now. In 10.04 some times the applet dissapears from the panel randomly. When i log out and re-log on the applet re-appears. Furthermore the Top panel becomes messy and jumbled some times as well. Getting a bit annoyed with ubuntu lately coz of this issue.

I don't have a laptop and do not have any brightness problem other than my video flickers sometimes when it comes out of sleep 
mode. I think that is the nVidia driver. Maybe I'll down grade it sometime if it annoys me enough,

But, one thing I can say about applets and panels disappearing or windows looking messy. Install the Compiz Icon. I have Cairo Dock 
and there is the icon in it and when I move my mouse over it, there is a "Reload WM" (windows manager) button that fixes my stuff 
when it becomes messed up. You might try that.
I used to reboot, but found this fixes it w/o rebooting.

---

### Post by kwbauson on 2010-10-30
With mine, I couldn't adjust the brightness at all.  It'd pause for 40 seconds, then a message would popup saying the brightness changed, but it didn't.  I made do with binding "xset dpms force off" to a key combo, and running it whenever I didn't use my laptop for short while.

---

