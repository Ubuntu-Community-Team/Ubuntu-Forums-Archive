---
title: "When &quot;plug and play&quot; video... isn't?"
date: 2012-08-04
forum: General Help
---

### Post by ladasky on 2012-08-04
I just had my main computer's monitor go on the fritz.  It's a fairly recent model, a Hyundai W240D.  I was operating it at full resolution of course, 1920 x 1200.  I have sent it in for service (under warranty, thankfully).

I can accomplish some tasks on my main computer, using my laptop and *ssh*.  (I would love to have an *ssh*-type service which talks to my laptop's GUI, if such a thing exists.)  But for a few tasks, I need to access the computer's GUI directly.  I have been borrowing the monitor from my son's computer for a few hours at a time.  That monitor is a Samsung 204B, a little older than mine, but quite serviceable.  The transition from 1920 x 1200 to 1600 x 1200 does not seem to cause any problems.

Well, my son doesn't like being deprived of his video games.  So a friend lent me yet another monitor, a Gateway FDP1760, manufactured in April 2006.  I know that I won't get more than 1280 x 1024 out of this monitor, but it beats having to haul a monitor back and forth between two computers.

Well, it's a nice idea, but it isn't working.  The Gateway monitor behaves strangely.  When I start the computer, I see my BIOS screen.  Then I see my GRUB menu, which has small text and certainly looks like it's in a high-graphics mode.  But after the GRUB menu, my screen goes dark and it stays that way.  I've waited ten minutes for the Ubuntu splash page to appear.  Nothing happens.  Pressing Ctrl-Alt-F1, up to -F6, also brings up nothing.

In all cases, I am plugging the monitors into my NVidia 460 graphics card, using a DVI cable.

Was the DVI standard changed some time between 2006 and now?  I am quite puzzled by this behavior.

---

### Post by papibe on 2012-08-04
Hi ladasky.

If you X configuration file has some settings to the specifics of the working monitor it would be a good idea to rename it (so it doesn't get used).

Boot into recovery mode, and get a root prompt. Then run this:
```
mv /etc/X11/xorg.conf  /etc/X11/xorg.conf.Hyundai
```
Then restart your computer:
```
reboot
```
Let us know how it goes.
Regards.

---

### Post by ladasky on 2012-08-06
Arrgh!

I went back to using the Samsung monitor, and I got hung up at the same black (actually, aubergine) screen that I got when I plugged in the Gateway monitor.

Trying the recovery mode from GRUB, I get hung up for a while right after the text messages say that the system is creating a Firewire device.  And then, half of a message which pertains to my RAID failing to mount correctly flashes by and scrolls off the top of the screen.  Then the system dumps me out to initramfs.  Yikes.

OK, it looks like I have another, more fundamental problem.  Let me ask one question in this thread.  Could the mere act of plugging different monitors into my computer have affected my software?  And in such a fundamental way?  

Papibe mentioned the X configuration files.  If these files get overwritten in ways that cause a system to crash, just from swapping monitors, that would be VERY bad! :(

---

