---
title: "Laptop hangs at initial bootup screen"
date: 2010-05-25
forum: General Help
---

### Post by cokelly72 on 2010-05-25
I have Lucid running on a Toshiba Portégé R500. Last week it started hanging for just over one minute at the initial Toshiba screen. That is, the screen with the Toshiba logo and a series of boot-from options (HDD, CD, Network, USB) along the bottom. I don't know if the machine is even interacting with the OS at this stage. Also, neither Ubuntu nor the machine recognises the CD-ROM tray any longer. As in, I can't boot from CD and I also can't mount a CD when in Ubuntu. I can, however, boot from a USB startup disk (after the one minute delay).

I'm not sure how to collect helpful data on this sort of issue, especially since I can't see any threads that point to similar problems. The only strange thing I did the day this problem started was to forget to unmount a truecrypt-encrypted USB key before shutting the laptop off.

I've reinstalled Lucid but to no avail. I assume that whatever problem I have is a BIOS problem (and so strictly not for here)? As you can imagine though I want to make sure I've accounted for all other possibilities before fooling around with the BIOS. So if anyone has thoughts and/or suggestions on what I might have done (or on how I might get useful information) they'd be very welcome. Sorry I don't have so much for you to go on.

---

### Post by jre6 on 2010-05-25
Most probably this is a BIOS problem or a hardware problem. If you can get into the BIOS, can you see if the CD/DVD drive is disabled or not? And, if it is a BIOS problem indeed, some settings are interfering which leads to the initial screen hanging. Try pressing 'esc' (worked for me when my computer showed the initial screen and did nothing for 2 minutes(that was a BIOS problem), it differs from system to system) and paste whatever appears here (the screen will show various system checks are being run, CPU fan RPM, CPU temperature etc.)

You had mentioned that problems started after forgetting to unmount a truecrypt-encrypted USB key before shutting the laptop off. This is, according to me, truly a coincidence and has nothing to do with the USB drive.

Describe the problem in more detail, and I will be able to help you further.

---

### Post by cokelly72 on 2010-05-25
Hi Jre6 thanks so much for this: I know it's not easy when someone isn't producing helpful info. Pressing escape produces a beep (after the minute) and "Check system. Press F1" which brings me to the System Setup screen. I've attached two screen shots (had to use a camera for this!) of the two available pages. First, I can't seen an option for mounting the CD rom. Second, I don't think it's doing system checks etc: the drive is not running during the delay. So I presume it's waiting for something and then times out.

---

### Post by jre6 on 2010-05-26
The screenshots hardly reveal anything as the settings are fine(I assumed that it would reveal something). So, some amount of testing has to be done to detect the problem. Please be prepared to spend 2 to 3 hours with this problem. Please do not get frustrated and also prepare your camera.

Turn on your computer.

Let the initial screen appear. Do not press any key and do not make any intervention and let the computer be in that state for 10 to 20 minutes.
Most probably the computer will not stay in that state, and some other message will flash on the screen which will tell that an error has been detected (and it may also allow you to proceed to Ubuntu startup). If this occurs, take a screenshot of that. If this does not occur, turn your computer off and turn it on within 15 seconds. Or does it boot from HDD if left in that state?

Does the problem persist after restating?
If it does, boot from HDD, and log in to Ubuntu. Let the session persist for, say, 5 minutes. Then restart (within 15 seconds)

Does the problem still persist?
Now, repeat the earlier steps for at least 10 times.

Report back what has happened.

---

### Post by cokelly72 on 2010-05-27
Thanks again JD6: I'm slammed in work for the rest of the week so hence the slow response. I think I've done what you suggested already: the computer waits one minute and then boots to Ubuntu with no problem except the fact that it doesn't pick the CD-Rom up. That is, if you put a CD in the computer makes like it is reading it but then nothing happens and it doesn't mount. Same goes for booting from a CD.

I think I would conclude that there's a hardware problem here: that might also explain the calm minute's wait. Er, to put it in non-tech words, the CD-Rom is working OK in and of itself but the computer can't 'see' it. Given that there is absolutely nothing else wrong with the PC's workings, this might be the glitch.

Anyway, I'm experimenting with trying to boot to DOS from a USB key so that I can see if I can reinstall the bios. I think it's a long shot at this stage (and I'm not having much look so far) but the lack of error messages and the continuation of the problem after a total reinstall suggests that your earlier diagnosis is correct: the error isn't with Ubuntu.

---

### Post by jre6 on 2010-05-28
Have you tried pressing esc before the minute?

---

### Post by cokelly72 on 2010-05-28
Hi. Yes. If I press escape the computer waits the remainder of the minute, beeps once and produces the "Check system. Press F1" prompt. F1 brings me into the BIOS with what's in the pics above. No other key works.

I've attained a zen-like attitude towards it now: Ubuntu is still five times faster in booting up than the Windows machine in my office, even allowing for a minute's doze. And it's a far greater pleasure to use after that. :)

---

### Post by jre6 on 2010-05-29
Do you have a diagnostics utility on your laptop (this is preloaded by the manufacturer). It is usually accessible through the BIOS. However, in some laptops, this can be accessed by the GRUB boot menu. On my Dell laptop, however, there are two diagnostics utilities (both preloaded by Dell) : one accessible through the BIOS and the other through GRUB boot menu.

If you have such a utility, please run it and let us know the results.

Even if you don't have one, let us know.

---

### Post by cokelly72 on 2010-06-01
Hi there. Sorry for the delay in replying: busy++ at the moment.

I've run the BIOS diagnostic a few times and everything comes up OK. I'll video it on my camera at some stage today so you can see the stages for yourself. It completes the check then waits the remainder of the minute then boots into Ubuntu.

The only thing that strikes me is that the diagnostic tool doesn't seem to check peripherals (i.e. the CD-Rom). That's a surprise to me but there's no sign that it's supposed to so I don't think it's an indication of anything.

---

### Post by jre6 on 2010-06-04
There is no need for the shooting the video.

Please try to restart the computer as I requested earlier. Sometimes, on continued restarts the problem disappears, but the problem reappears when the computer is turned on again with a time interval of at least an hour (This is occurring on my desktop, this is probably a hardware problem).

---

