---
title: "Ubuntu freezes after monitor goes to sleep - no log data?"
date: 2009-12-27
forum: General Help
---

### Post by fowie on 2009-12-27
Linux 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
Ubuntu 9.10

Abit Il90-MV motherboard, 2GB RAM, on-board Intel GMA 945 video (uses Intel i950 GPU drivers).

The computer seems to run fine while I'm using it, but occasionally after I've left it alone doing something (like, say ripping a DVD overnight, or even just sitting idle), the monitor will go to standby and then the whole computer becomes unresponsive and requires a hard reset to get it back.  I've checked dmesg, messages, syslog, daemon.log, Xorg.log, pm-suspend, pm-powersave, and even debug log, and none of them show any activity when it locks up.  The last message I get in any is in syslog and messages, and all it is, is:
```

Dec 26 23:29:23 fowie-desktop kernel: [ 3695.694926] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 26 23:29:23 fowie-desktop kernel: [ 3695.694930] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 26 23:33:35 fowie-desktop kernel: [ 3947.442617] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 26 23:33:35 fowie-desktop kernel: [ 3947.442621] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 26 23:33:35 fowie-desktop kernel: [ 3947.569520] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 26 23:33:35 fowie-desktop kernel: [ 3947.569524] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 08:21:03 fowie-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.

```
(Stopped using computer around 23:33 on Dec 26, rebooted Dec 27th at 8:20 AM, computer stopped responding sometime after 23:33 on Dec 26).

Are there any other logs I can check or debug flags I can set to get more information as to why it's freezing?

Power management settings are to turn off display after 10 minutes, but that's all, never suspend, never hibernate, never spin down drives.

Help!

---

### Post by dcstar on 2009-12-27
> **fowie said:**
> 
........
Are there any other logs I can check or debug flags I can set to get more information as to why it's freezing?

Power management settings are to turn off display after 10 minutes, but that's all, never suspend, never hibernate, never spin down drives.


Set up temp and CPU monitoring to see what is happening with the hardware.

---

### Post by Mahngiel on 2009-12-27
it's a known bud w/ 9.10.  Until it gets fixed, it's best to set up your system w/o hibernation or sleep.  i'll look for the bug report link for you, so you can get on board.

Here it is: [https://bugs.launchpad.net/ubuntu/+bug/468850](https://bugs.launchpad.net/ubuntu/+bug/468850)

---

### Post by fowie on 2009-12-28
My system doesn't do hibernate or sleep, it only puts the video to sleep (powersave mode, not suspend or hibernate).  

What program would you suggest for logging cpu temp?  I've got lm-sensors installed, but conky doesn't do logging...

---

### Post by samoul on 2010-01-11
I have the same exact problem, when the monitor go to sleep, mouse, keyboard and even the power button stop responding. Have you find any way to fix this? I disabled the timer so that the monitor never goes to sleep, i'll have to manually power off the monitor when i'm away ... not so cool fix!

---

### Post by spiderbatdad on 2010-01-11
I believe this is an acpi error. You can disable it at boot, but you may loose battery monitor for example. Some pci devices may work better...audio card perhaps.

---

### Post by fowie on 2010-01-11
That's the same workaround I've been using.  I think it might be a bug in gnome-screensaver.  I just noticed that recently there was an update to it, so I was going to re-enable it and see if things worked correctly again.  Just by chance, what screensaver were you using before you disabled it?

---

### Post by fowie on 2010-01-11
@spiderbatdad, which acpi option would you recommend using at boot? just acpi=off?

---

### Post by spiderbatdad on 2010-01-11
> **fowie said:**
> @spiderbatdad, which acpi option would you recommend using at boot? just acpi=off?

That's what I was thinking.

---

### Post by samoul on 2010-01-12
I haven't disabled the screen saver, i disabled the "Turn display to sleep ..." in the power management preference. That's why i don't think it's a bug in gnome-screesaver... As for now, it work. I'll try switching acpi to off and reable the display sleeping thing.

---

### Post by addicted68098 on 2010-02-14
I was facing similar problems, I updated to the 10.4 alpha and they are gone.

I feel in my situation it had something to do with the Ethernet drivers, I never encountered a crash while the port remained actively used when say Transmission was running.

---

### Post by dsfitzpat on 2011-01-09
This might be a bit late to chime in on this thread, but did anyone ever get anywhere with this?  I set up a new computer for my parents over the holidays and installed Ubuntu 10.04 (I've had them running Ubuntu for a couple years now since their XP install had crawled to a near halt and they can use it for email and the internet as long as I've set everything up for them!) and of course three days after I leave my dad emails me to complain that it's freezing when the monitor powers off.
I've never had this problem myself, and I'm not likely to get useful debugging information from my parents!  Their new computer is a pretty basic setup; an Intel Core i3 on a Gigabyte board, using the integrated graphics, with no expansion cards.
I'll probably just tell them to disable the monitor shutdown and use a blank screen as the screensaver, but if there's a solution I'll try walk my dad through it.

---

### Post by Zneiva on 2011-05-20
Not sure if there is anyone still following this thread, but I just wanted to add that my 10.04 box just started doing this.

Before, the box was working fine; but then I did two things:

1) I replaced a LG 19" CRT with a a 23" BENQ LCD

2)  Changed my monitor power-off time from 30 minutes to 1 minute and made that the default.

Now my computer freezes up sometimes when it goes to sleep.  No network activity can occur either; it requires a hard reboot.

I've gotten around it for now by changing the time to NEVER for when to turn the monitor off.

Not the best solution.

---

### Post by linuxinstalledfromhdd on 2011-05-20
if there is no log that this is happening, it could be hardware "backlight" on your monitor failing.

---

### Post by Zneiva on 2011-05-20
> **linuxinstalledfromhdd said:**
> if there is no log that this is happening, it could be hardware "backlight" on your monitor failing.


I wouldn't expect that to cause by web server to stop responding and the ssh daemon to no longer work.

---

### Post by linuxinstalledfromhdd on 2011-05-20
well it should be on the log somewhere..  hhmmmm

---

### Post by dsfitzpat on 2011-05-21
I visited my parents recently and tried to figure out what was going wrong with their computer, but without much success.  I filed a bug report with the xsession errors but my guess is 10.04 bugs aren't getting much attention from the devs these days.
The problem on my parents' computer might be different - it turned out what was happening was that when the system went to power down the monitor, it caused some sort of GPU hang, and the system went into an infinite loop where Xserver would crash (I'm guessing) and throw things back to the gdm screen, but the gdm would also crash, etc etc.  (The tip-off that this had happened was hearing the 'drum beat' ready sound that Ubuntu plays when the gdm loads over and over again.)
I was able to hit Ctrl+Alt+F1 (or F2) to get into a virtual terminal, log in, and then shut down the computer from there.  I can't recall if it occurred to me to try running startx.  In any case, I didn't have enough time to figure it out, so I filed the bug report (still no response), and changed the settings back to have the monitor never shut off.

---

