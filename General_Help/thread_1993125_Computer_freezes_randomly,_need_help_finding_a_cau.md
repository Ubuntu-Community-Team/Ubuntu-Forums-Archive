---
title: "Computer freezes randomly, need help finding a cause, and hopefully a solution"
date: 2012-06-01
forum: General Help
---

### Post by pmheideman on 2012-06-01
My HP DM1Z  has been freezing since I installed Ubuntu 12.04 64-bit on it.  I'm dual booting with Windows 7 64 bit, and though I don't use it super often, I have no freezing problems with windows.  At first I thought the problem in Ubuntu was related to the wifi, since it always seemed to happen when I was either downloading something or using firefox.  However, in the last few days it has happened even when I have the wifi turned off.  Last night I did a fresh install, hoping this would take care of whatever was the matter.  Unfortunately it did not, and I've had two freezes today.  It's an extremely hard freeze, immune to magic REISUB.  It happens once or twice a day, and I have to do a hard reset each time.  Not exactly easy on the hard drive, so I'm eager to get it fixed.

If anyone has any suggestions for how to go about troubleshooting this, I'd really appreciate it.

---

### Post by dragonfly41 on 2012-06-01
I am in dual boot configuration (Vista + Ubuntu 10.10).

In Ubuntu I now run Firefox in safe mode which seems to reduce the frequency of crashes.

Go to Firefox toolbar > Help > Restart with Add-ons Disabled

and select Safe Mode after Firefox restarts.

I've moved my Firefox plugins out of the mozilla folder into a backup folder.

You could try enabling Add-ons or Plugins one at a time to see if any is the problem.

Or you could try Opera instead of Firefox.

Flash seems to be one suspect.   Do you access flash sites?

You might try bleachbit to clean out caches.

---

### Post by ajgreeny on 2012-06-01
Could be all sorts of reasons.

Have you run **memtest86+** from grub?  If not do so and leave it running for several hours, or overnight, and look for any error notes on the bottom line.  You have to manually stop the test as it runs until stopped.

Alternatively make sure you have the correct and most up-to-date video drivers for your graphic card, as bad drivers can also cause this type of freeze.

Power supply may be the next thing to check, but I have no idea how to do that from within a ubuntu or windows OS..

---

### Post by pmheideman on 2012-06-01
Thanks for the replies!   I'll try running memtest tonite and see what comes up.  That's pretty nasty if firefox is causing whole system crashes.  Is there any good way to find out what process it was that locked everything up?

---

### Post by LinGNUbie on 2012-06-01
I have had this happen a few times, and as I am always tinkering with older hardware, it seemed to be a piece of hardware going into failure such as a HD, NIC, or other device. Just something to think about.

---

### Post by pmheideman on 2012-06-02
Memtest reports no errors.  There seems to be a lot of discussion here of this bug, but there's not much I can take from it: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187?comments=all)

---

### Post by pmheideman on 2012-06-08
I've switched to chrome over the last week or so, and have had no freezes.  Looks like it was indeed something to do with firefox.  Anyone else having the problem: don't use firefox anymore!

---

### Post by phosphide on 2012-06-08
Try running firefox from the terminal next time and see if it produces any errors. Most likely you will see all kinds of stuff show up but see if it freezes again and post any output.

Also, try running **top** in the terminal if possible. This will give you an indication of what programs are hogging your cpu or ram.

---

### Post by pmheideman on 2012-06-08
Just had a freeze again, and when I restarted (Magic REISUB worked this time), I got an error reporting window saying Ubuntu had an internal error.  I've had this before.

The executable path was:
/usr/sbin/bluetoothd

package:
bluez.498-2ubuntu7

title:
bluetoothd crashed with SIGSEV in g_main_context_dispatch()

more than that is an insane amount of typing (can't copy and paste from the error dialog).  Anything useful in there?

---

### Post by dakodako on 2012-06-14
i have the same problem,
with th hp dm1 and 12.04 

always when i see flashvideo

---

### Post by jonblund on 2012-07-21
Same problem with total freeze, no contact to system, not even the reset button works. Have to shutdown with power button and restart.
 Happens randomly, bur so far (new build) only in firefox.
 Could any one confirm this behavior in other applications?

---

### Post by RodneyLee on 2012-11-04
Been happening for me also, Firefox tabs vanish, desktop topbar icons vanish, firefox become slow to respond, have to poweroff to restart
trying unity 2d seeing if that helps....

---

### Post by okkadiroglu on 2012-11-04
I am using Ubuntu 12.10 on a AMD FX(tm)-4100 Quad-Core Processor × 4 computer. Ever since I upgraded to 12.10 I experience sudden and unexpected freezes. I have re-installed gnome, unity, compiz, etc. I still have random freezes. The screen gets smeared and neither the keyboard of the mouse works. I  have to restart the computer manually. Also I get lots of Ubuntu &#304;nternal error messages but in most cases I cannot report a bug since on account of some demon that is not working anymore. I mostly use GoogleChrome, Radiotray, JDownloader. How can I solve this nagging problem?

Best Regards

---

