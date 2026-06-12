---
title: "Input fields stopped working in Firefox"
date: 2009-07-13
forum: General Help
---

### Post by jaclynL on 2009-07-13
Randomly I noticed most Firefox widgets stopped working last night.  For example, clicking submit/login buttons and using the search bar now result in no action whatsoever.  This doesn't correspond to any new updates being installed or even a restart of the Firefox application.

I noticed this at the same time as a few other problems, which makes it a bit disturbing.  The issue seems to have occurred in the middle of converting a large number of audio files and happened at the same time as [this Nautilus display issue]("http://ubuntuforums.org/showthread.php?p=7608523#post7608523").  Not sure if the three are connected, but it's certainly bizarre that they've happened at the same time.

Any ideas where I could start looking in my logs or config files?

---

### Post by ghostborg on 2009-07-13
Probably not helpful, but do you have a wireless keyboard and mouse setup? Check Batteries- duh. Try a complete power down and not just a reboot.
Try another browser like Opera to help isolate the problem.
Try running update just in case.
The only thing I had similar to your problem was while I was running VirtualBox.
Try to uncheck your internet connection or disconnect while Firefox is open to a page with an input box and see if you can type into an input box. That might indicate a problem with anything going on between Firefox and your internet.
Sorry that's all I got.

Good Luck

---

### Post by prshah on 2009-07-13
> **jaclynL said:**
> Randomly I noticed most Firefox widgets stopped working last night.  For example, clicking submit/login buttons and using the search bar now result in no action whatsoever.  

I've faced a similar situation when my modifier keys (Ctrl, Alt, Shift and/or Win) seem to have got "stuck" virtually; tapping each (both right and left sets) once or twice usually clears it up.

Typically (not always) this occurs when I interrupt the screensaver with a modifier key rather than the spacebar or some such.

---

### Post by lovinglinux on 2009-07-13
Try **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

---

### Post by jaclynL on 2009-07-15
Actually, turned out to be a hard drive space issue.  Some stuff was dumping onto my main filesystem drive and filled it up -- once I moved my files to the appropriate drive the problem disappeared.  Ooops :oops:

Thanks for your help everyone :)

---

