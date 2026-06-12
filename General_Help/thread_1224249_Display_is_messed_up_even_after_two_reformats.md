---
title: "Display is messed up even after two reformats"
date: 2009-07-27
forum: General Help
---

### Post by thelinx on 2009-07-27
I've never had this issue before but after trying out
gNewSense and then installing ubuntu again,
 by the time I get to the login screen, the display messes up.
[http://picasaweb.google.com/m/viewer#photo/thelinxswe/5351839807207934513/5363082251581594578](http://picasaweb.google.com/m/viewer#photo/thelinxswe/5351839807207934513/5363082251581594578)
Any ideas? I've tried reinstalling two times already.

---

### Post by coffeecat on 2009-07-27
> **thelinx said:**
> [http://picasaweb.google.com/m/viewer#photo/thelinxswe/5351839807207934513/5363082251581594578](http://picasaweb.google.com/m/viewer#photo/thelinxswe/5351839807207934513/5363082251581594578)

I'm getting the Picasa Web Albums sign in page with some generic pictures. No sign of your screenshot - I guess that's what you intended. Can you provide another link or, better, upload the image to your post with the Attach Files > Manage Attachments utility you can find under 'Additional Options' below the message field when you compose your post.

---

### Post by thelinx on 2009-07-27
Attached picture

---

### Post by t0p on 2009-07-27
Wow!  What a pretty display.  Though I doubt that's what *you* think when you want to log into your box,huh?

The only time I've seen something like this on my own machines is sometimes when I hit [**Alt+SysRq+REISUB**]("http://en.wikipedia.org/wiki/REISUB").  Maybe that will suggest a possible cause/solution to someone more *au fait* with this stuff than me.

The fact this problem has recurred after 2 disk reformats makes me suspect this is a hardware issue rather than an ubuntu configuration problem.  But what do I know?  Very little.

First of all, I guess we should see if this problem affects just the graphical desktop display or all *tty*s.  So, try pressing **Ctrl+Alt+F1**, **Ctrl+Alt+F2** **Ctrl+Alt+F3**, etc etc.  Do you get a command-line terminal screen (ie white text on a black background, a login prompt)?  The answer to that may help narrow this down.  (To return to the original screen - the one that's currently all fscked up - hit **Ctrl+Alt+f7**.)

---

### Post by Taus on 2009-07-27
i'm sure that it's gfx driver issue... i had that excact screen on my laptop after upgrading the ATI drivers.

what gfx card are you using?

---

### Post by thelinx on 2009-07-27
> **t0p said:**
> 
First of all, I guess we should see if this problem affects just the graphical desktop display or all *tty*s.  So, try pressing **Ctrl+Alt+F1**, **Ctrl+Alt+F2** **Ctrl+Alt+F3**, etc etc.  Do you get a command-line terminal screen (ie white text on a black background, a login prompt)?  The answer to that may help narrow this down.  (To return to the original screen - the one that's currently all fscked up - hit **Ctrl+Alt+f7**.)

No change.

> **Taus said:**
> i'm sure that it's gfx driver issue... i had that excact screen on my laptop after upgrading the ATI drivers.

what gfx card are you using?

ATI Radeon 9600. But it used to work...

---

### Post by coffeecat on 2009-07-27
I see what you mean.

Did you install from the live or alternate CD? If you used the live CD, was the display OK with that? Since gNewSense is simply Ubuntu with all the non-free stuff stripped out, if your display was working with gNewSense, it *ought* to work with Ubuntu - theoretically.

A thought. You say that the display messes up by the time you get to the login screen. That implies that the usplash boot splash is displaying OK. Am I right? Because, if so, that might partly explain it. The login screen appears just after the xserver starts, whereas usplash is using - um - whatever usplash uses, which means that the output being sent to the monitor changes at that point. Possibly, the monitor is failing to tune to the new signal. My monitor displays certain messages (which I ignore) at this point. If that's a flat-screen monitor, try pressing the 'Auto' or Autotune' button on the monitor. If you haven't got an auto button, have a look in the monitor configuration menu.

---

### Post by thelinx on 2009-07-27
I installed with the alternate cd but I used ubuntu a lot before trying gNewSense.
When I press auto it says NO ACCESS on DVI and it just moves it around a bit on VGA.
USplash works, though.

---

### Post by coffeecat on 2009-07-27
Which version of Ubuntu were you using before gNewSense and which version are you having trouble with now? If you were using an earlier version of Ubuntu before, I wonder if the open source driver for your ATI card has changed between versions.

You could try this, but no guarantees it will work. You'll need to boot up in recovery mode and insert the following line in the "Device" section of /etc/X11/xorg.conf:

```
     Driver "vesa"
```... and then reboot which will give you the generic vesa video driver. It won't be a particulary good display but hopefully your monitor will make sense of it. And then if you can get into a GUI, you will be able to install whatever proprietary driver is available for your ATI card. Whatever that might be - sorry I have very little experience of ATI.

If you need help editing xorg.conf from recovery mode, just post back.

---

### Post by Taus on 2009-07-27
FYI i upgraded my bios and everything worked perfectly afterwards.

I'm running ATI Radeon 9700 (m) thats the same driver as the 9600

give the update a spin and see where it takes u

---

### Post by thelinx on 2009-07-27
Vesa worked! Thank you very much.

---

### Post by coffeecat on 2009-07-27
> **thelinx said:**
> Vesa worked! Thank you very much.

I'm glad. But you won't get compiz or anything fancy with vesa. You'll need the proprietary drivers for that - if there are any suitable for your card.

Good luck!

---

