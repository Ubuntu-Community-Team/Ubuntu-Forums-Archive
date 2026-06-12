---
title: "Black Screen LiveCD"
date: 2011-09-25
forum: General Help
---

### Post by bestbets1 on 2011-09-25
I downloaded Kubuntu the other day and burnt it to a CD. Popped it into my 2003 Toshiba TE2300 (1.5Ghz Pentium, 480MB RAM, 60GB HDD) and attempted to get started.
Got to the splash screen and selected the try out or install option. CD starts to load, but then flicks to a black screen and starts showing silly things scanning on the screen.
THe same occured with Xubuntu. For both, I downloaded the 11.04 (Natty) version.

Note that both LiveCD's work on other PC's flawlessly and that I tried the following commands after researching a bit:
[LIST]
[*]Remove quiet and splash
[*]Add either i915.modeset=1 or i915.modeset=0 I also tried VGA=771, that made a black screen and floppy.floppy=thinkpad didn't work either
[/LIST]
I tried the Ubuntu 9.04 Live CD and Xubuntu 7.04 and both worked without a hitch.

What could be the problem?

---

### Post by rodlph on 2011-09-25
2 things to try:

replace the cd drive (maybe a faulty cd drive)
boot kubuntu installer off a usb drive

it may be a problem with your cd drive so you could try either of the 2 options. also make sure you are using x86 version NOT x64

---

### Post by bestbets1 on 2011-09-26
I downloaded and tried using Xubuntu 11.04 and Kubuntu 11.04 on LiveCD. Neither worked on my 2003 Toshiba TE2300 (1.5GHz Pentium M, 480MB RAM, 60GB HDD). I would get scrolling lines of code (too fast to read).

After much searching, I tried using the acpi=off function in the F6 menu, as well as the modeset (or whatever function name it is). I got a weird looking splash screen, with Xubuntu written on it (black screen) and white dots coming on and off. Then, it made some white bars, coloured dots as the CD kept going. I tried restarting the Xsession (Alt+SysRq+k and Ctrl+Alt+Backspace) to no avail.

What could the problem be? Note that I have verified the CD on another PC where Kubuntu installed fine, and the Xubuntu CD loads. My CD's are fine, as well as the drive burnt with (my laptop, running Xp Home w/ SP3-disk loads and asks if I want WUBI)

All help appreciated,
bestbets1

---

### Post by nothingspecial on 2011-09-26
One thread per issue please.

Feel free to bump your thread back to the top every 24hours or so.

Thanks

Merged.

---

### Post by sanderd17 on 2011-09-26
Problems with Toshiba. I also had those with my old toshiba.

They can be solved with some boot options normally.

Try the option "acpi_osi=" (without quotes)

Although I think it's weird that the acpi=off option didn't work.

If you can't get it to work, try to download puppy linux and try to run it with vesa drivers.

---

### Post by bestbets1 on 2011-09-26
Hi All,

Thanks for the replies. I finally got everything to install! :) I used nomodeset, the ACPI one and i815modeset=1

Now, I get the black screen on booting. I tried using the above in GRUB, to no avail. Just get the flashing _ on the top left of the screen.

Many thanks for all yours help-

---

### Post by sanderd17 on 2011-09-26
Just note that the acpi option is dangerous.

acpi=off will turn all not-strictly-necessary hardware control off. So your fans won't start blowing when your computer becomes hot, or your fans will always blow. You won't be able to read your battery status and a few other things.

If you can work without acpi=off, it's definitely worth it.

Your computer won't overheat, but it's possible that you get a sudden shutdown when the CPU becomes too hot. And you won't be able to power him back up until it's cool again.

EDIT:

After a re-read, is it solved or not? You were able to boot via the live cd but not via the installed OS? Or did I read it wrong.

---

### Post by bestbets1 on 2011-09-26
The laptop's fan runs constantly on HI.

Anyway, there was a GRUB edit I was going to perform, and try to straighten it all out again.

Hoping it works-

P.S. I am reading this forum [http://ubuntuforums.org/showthread.php?t=1604899&highlight=Ubuntu+black+screen+book](http://ubuntuforums.org/showthread.php?t=1604899&highlight=Ubuntu+black+screen+book)

---

### Post by bestbets1 on 2011-09-26
> **sanderd17 said:**
> Just note that the acpi option is dangerous.

acpi=off will turn all not-strictly-necessary hardware control off. So your fans won't start blowing when your computer becomes hot, or your fans will always blow. You won't be able to read your battery status and a few other things.

If you can work without acpi=off, it's definitely worth it.

Your computer won't overheat, but it's possible that you get a sudden shutdown when the CPU becomes too hot. And you won't be able to power him back up until it's cool again.

EDIT:

After a re-read, is it solved or not? You were able to boot via the live cd but not via the installed OS? Or did I read it wrong.

No, not yet solved. Now I can't boot into Xubuntu... doesn't work without ACPI=off the other option (acpi_osi=linux) doesn't work. I get a black screen. ACPI=off is the only option I need-however in older distros i don't need any. I've tried Ubuntu 9.04 and Xubuntu 7.10-no trouble. Maybe it is some recent updates

---

### Post by sanderd17 on 2011-09-27
normally if you can boot the live CD, you can also boot the installed OS with the same boot options. Check my signature on how to do that.

And those boot options, those are caused by other kernel versions. I had to use acpi=off on 9.04 and 9.10, but not on older or newer distros.

---

### Post by bestbets1 on 2011-09-27
> **sanderd17 said:**
> normally if you can boot the live CD, you can also boot the installed OS with the same boot options. Check my signature on how to do that.

And those boot options, those are caused by other kernel versions. I had to use acpi=off on 9.04 and 9.10, but not on older or newer distros.

I finally managed to get booted and install the intel drivers necessary!!! Although, my only issue now is that I can't log off (goes to black screen) to edit the root to say "acpi_osi=linux." Since my laptop's fan doesn't really run higher than medium, although there is a chance me setting the processor to Dynamic had something to do with it.

Thanks for the help-i shall now mark this thread as resolved/solved

---

