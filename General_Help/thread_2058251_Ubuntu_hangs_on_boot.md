---
title: "Ubuntu hangs on boot"
date: 2012-09-15
forum: General Help
---

### Post by osarusan on 2012-09-15
Ubuntu x64 / AMD Athlon II / 16 gb of RAM

I've had this problem for a long time now, and I've just ignored it thinking it might get fixed, but it's been probably over a year or more that I have had this.

Frequently when I boot, Ubuntu will hang on the purple screen. Sometimes it will hang even for an hour or more, sometimes 10 minutes, before going to the desktop.

I have no idea what's causing it. This has happened over and over again on every fresh install I've done, even other Ubuntu derivatives like Linux Mint. I just fresh installed yesterday and have the same issue.

During the purple screen hang, USB devices don't register yet either (I can tell this because when the hanging is finished, if my phone is plugged in, it beeps when it begins to charge).

The strange thing, and the reason I haven't posted anything for the longest time, is that whenever it hangs like this, if I press the PC's power button once or twice, it stops hanging and continues booting. I'm fairly sure that's not such a good thing to do and I have no idea why it works...

Can anyone help me?

---

### Post by Epodx64 on 2012-09-15
Are you using a proprietary graphics card like nvidia or ati?

---

### Post by osarusan on 2012-09-15
ATI card. Radeon HD 4770.

This happens whether I use the proprietary drivers or the open source drivers, though.

---

### Post by osarusan on 2012-09-16
*bump*

Does this have something to do with the ATI card? Or the driver? Or could it be something else altogether?

I'm not sure what I would have to do in order to figure out what is causing this. Any suggestions?

---

### Post by Dy1anW on 2012-09-16
Hi, I've had this problem recently as well. I've been booting fine for ages and now, quite inexplicable, bootup hangs at "Stopping Mount network filesystems". It was fine the last time I booted, and I didn't even upgrade anything.

Anyone know how to solve this?

Edit: nevermind, after a fair amount of hair pulling, cursing (because that always helps) and tinkering, I've finally got it working again. It seems there was a problem loading the display manager. Reinstalled gdm seemed to help, but the problem would persist if I tried to boot into lightdm. That issue is solved now too.

---

### Post by osarusan on 2012-09-17
So what did you do? Just remove ldm?

---

### Post by Dy1anW on 2012-09-17
I simply reinstalled gdm, and set lightdm as default.

```
sudo apt-get --reinstall install gdm
sudo dpkg-reconfigure lightdm
```

This worked for me since my copy of gdm had 'broken' somehow (still unsure how), but I don't think this is the case for you, especially since it occurs even after a fresh install.

When you say your computer hangs at the purple screen, do you mean the splash screen with the scrolling dots? When you hit Esc, what line does it stop at?

You should probably post your boot.log here, and hopefully someone with a much better understanding than me will know what to do.

---

### Post by osarusan on 2012-09-17
It hangs at the part where the screen is all purple. I think it's called Plymouth?? Maybe? When it hangs, I can't hit escape. The keyboard is completely unresponsibe. No ctrl-alt-delete, not even numlock works. The only thing to do is press the power button a few times, then I can hear the computer begin to think, and then it resumes the boot.

I'm attaching my boot.log.

---

### Post by f8l_0e on 2012-09-17
Did you install 12.04 clean or have you upgraded from a previous version?

Have you tried clicking the ubuntu logo next to your username on the gdm window and selecting gnome classic mode, then reboot and see what happens?

You might also try adding the nomodeset option to the grub boot settings.

---

### Post by osarusan on 2012-09-17
This has happened with upgrades and with clean installs. This one now is a clean install.

I'll try it with Gnome Classic, though I do prefer Unity.

What would setting nomodeset do?



--
edit: Using Gnome Classic and Unity 2d did not help. Still hangs at boot.

---

### Post by f8l_0e on 2012-09-17
nomodeset disables kernel mode setting of the video card's resolution and color depth, it apparently has been responsible with boot hangups for ati, nvidia, and intel drivers.

---

### Post by osarusan on 2012-09-18
I'll give it a try. Would disabling it reduce functionality at all?

---

### Post by f8l_0e on 2012-09-18
Yes, but the setting can be undone just by removing the line from the grub config file.  See if that is the problem, then we can work from there.

---

### Post by osarusan on 2012-09-18
I tried nomodeset, but it still hangs at the same moment -- on the purple screen before the ubuntu loading logo appears.

---

### Post by f8l_0e on 2012-09-18
Ok, try this.  Edit /etc/default/grub 
change the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT=""

then run sudo update-grub2

When you reboot, it will disable the plymouth boot splash screen so you can see 
boot messages if it still hangs, what was the text on the last line where it hangs?

---

### Post by Wim Sturkenboom on 2012-09-19
> **f8l_0e said:**
> Ok, try this.  Edit /etc/default/grub 
change the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT=""

then run sudo update-grub2

When you reboot, it will disable the plymouth boot splash screen so you can see 
boot messages if it still hangs, what was the text on the last line where it hangs?

You must be joking :) System can't boot so how can OP get there.

The alternative:
[LIST=1]
[*]If you normally see a grub menu, go to 2. Else after the POST, keep <shift> pressed till you see the grub menu.
[*]Press 'e', go to the line that contains 'quiet splash' and remove those words.
[*]Press <ctrl>x to boot
[/LIST]

Personally, I would replace 'quiet splash' by 'text'. This will (or at least should) get you to a console where you can login (note that you will not see anything when you type the password). Next use _sudo lightdm start_ (12.04) or _sudo gdm start_ (10.04) to (try to) start the graphical environment; I don't know for other versions.

Please give an accurate description of what happens. If starting of the graphical environment fails, you can check /var/log/Xorg.0.log to see what fails.

---

### Post by f8l_0e on 2012-09-19
No, I'm not joking.  The OP states that the system eventually gets to GDM after a long wait, so it is no completely hung.  I'm trying go one step a time to avoid missing clues as to what can be causing the problem.

---

### Post by osarusan on 2012-09-19
Yes, I can boot -- I just have to hit the power button once or twice during boot to break it out of its freeze. Been like this for over a year now, even on fresh installs.

So I just removed quiet and splash from grub. It booted, but right after grub it still hung on the purple screen a bit. This time it ended by itself after about 15-20 seconds before boot continued. After the purple screen ended, the boot text went up so fast I couldn't read it, but the top to lines both started with fsck.

Strangely enough, last night when nomodeset didn't work, I went back and removed nomodeset from grub, and then restarted, and the system booted twice perfectly with no hanging. Then on the 3rd reboot, the hang returned, and again this morning it hanged. This sort of off-and-on hanging has been the norm. I would say it hangs 90-95% of the time, but then there is 5-10% where I turn it on and it boots up on 20 seconds or so.

---

### Post by kimberlite on 2012-09-19
> **osarusan said:**
> 
So I just removed quiet and splash from grub. It booted, but right after grub it still hung on the purple screen a bit. This time it ended by itself after about 15-20 seconds before boot continued. After the purple screen ended, the boot text went up so fast I couldn't read it, but the top to lines both started with **fsck**.

I would suspect HD errors. To exclude this possibility could you check your "SMART data" of the disk with "disk utility"?

---

### Post by f8l_0e on 2012-09-19
You could try ```
dmesg | grep 'fsck'
``` to check the kernel boot messages to see if it contains the messages about fsck.

You could also do ```
dmesg | less
``` to use the up/down or pg up/pg dn keys to go through the kernel boot log.  Press "q" to leave less when you are done looking.

---

### Post by osarusan on 2012-09-19
I did both of the commands. grep turned up no messages about fsck, and a combing over of dmesg | less didn't reveal anything to me, although admittedly I don't know enough about what most of that output means to be able to catch much.

I'm checking the SMART data now... will edit this post with results later.

---

### Post by osarusan on 2012-09-20
I ran all of the SMART checks, and they all came up green on my primary HD.
I have a secondary HD which is NTFS and I use for a Windows install. It's an older drive and came up with a few warnings on the SMART check, but I don't boot from that drive or even auto-mount it at start up, so I don't know if that would be causing this hang...

---

### Post by f8l_0e on 2012-09-20
I wouldn't think so.  You could always try disconnecting that drive and boot to see what happens.  You could also run dmesg > dmesg.txt from your home directory and then post that file to pastebin and put a link here so people can review it for errors.

---

### Post by osarusan on 2012-09-20
Sure, I'll attach my dmesg to pastebin. Here's the link:

[http://pastebin.com/s9GzriLq](http://pastebin.com/s9GzriLq)

---

### Post by f8l_0e on 2012-09-20
I don't see any significant errors.  I have a few questions though?
Has your iPhone been connected every time you boot with the 15-20 residual boot delay? Are you intending to tether the 3g connection to the computer, if not, you might turn that off to see a quicker boot time.  What's your setup regarding the wireless internet connection?  It seems that there are two nics, the first is an Atheros based nic and the second is a Broadcom 43xx series.  The Atheros on wlan0 tries to connect first. It authenticates but doesn't associate.  Then the second one authenticates and associates.  Are you trying some fancy setup?

---

### Post by osarusan on 2012-09-20
Nothing fancy, just an ordinary setup.

The iPhone isn't always plugged in, and no tethering. The reason it's plugged in here is because it's a good notification of whether my PC is frozen or still booting -- if the iPhone beeps because its receiving power from the USB, then I know that the PC is continuing to boot and I can wait. If the iPhone never beeps, then I know my PC is frozen and I have to hit the power button once or twice to get it to continue booting.

As for the modems, one is a PCI card internal modem and the other is a wireless USB. I had some trouble with various cards (the Broadcom doesn't work out of the box on Ubuntu, so I bought the Buffalo; but the Buffalo doesn't work in Windows so I haven't removed the Broadcom from the computer). I generally connect with the Buffalo USB, but sometimes for some odd reason it just stops working in Ubuntu, so when that happens I connect with the Broadcom.

The freezing problem has been happening for well over a year now, but I have only had the second modem for a couple months, and I rarely boot with the iPhone plugged in unless I happen to be rebooting mid-day. I would be surprised if either of those are the cause of the freezing.

I think during my last boot, I waited about 20-30 seconds before pressing the power button (as the iPhone didn't beep). If it would be helpful, I'll unplug the iPhone and USB modem and reboot again, and I won't hit the power button unless it freezes for over an hour. Do you think that might give some more insight?

---

### Post by kimberlite on 2012-09-20
I do not have better idea: run a memory test from grub menu to exclude a memory failure.

---

### Post by f8l_0e on 2012-09-20
As a general rule of thumb, if I'm experiencing an issue that needs troubleshooting I try to removal all outside possiblities.  If it were me, I would disconnect all external devices and use a ps/2 keyboard and mouse during troubleshooting if you have the ports and an old keyboard and mouse.  In this case, I would also go so far as to remove the wireless nic from the equation.  In one of the other threads the guy was having USB problems and it turns out there is an issue with AMD SB600 and early versions of the SB700 chipset regarding USB freezes.  This may be your issue and have little to do with video subsystem.

---

### Post by osarusan on 2012-09-20
Okay, an update:
I took out both modems and rebooted, and the system booted properly. Rebooted and it booted quickly and without problems.

I added the USB modem, and it went back to the old way -- freezing until I pressed the power button twice.

I took it out and added the PCI modem. It also froze as before.

I moved the PCI modem to a different slot. This time, instead of freezing, there was about an 8 second delay during plymouth, then the machine booted normally. However, for some reason, the modem could not find any networks when in this slot. It appeared to be detected by the system properly, just no networks showed up.

Does that makes sense to anyone? What are my options here? Is there a fix to this or am I going to be stuck with no wireless? I can't imagine that pumping the power button every single boot could be good for the machine.....

---

### Post by f8l_0e on 2012-09-20
Quickly pressing the power button doesn't hurt the machine.  The power switch is a software switch that triggers an interrupt, which is probably why it resumes from whatever hangups during boot.  The only way you'd be putting stress on the board is if the you pressed the power switch long enough to force a power down and then turned it right back on.  As far as why it boots normally now; that might just be that the card isn't connecting to the network allowing for a quicker boot time, or the board is actually operating better in that slot.  The only way to know for sure would be to do a clean install and get it back on the network to see if it still boot normally.

---

### Post by osarusan on 2012-09-20
Well I need the wireless so I put the card back in... if it's not harming the machine that's a relief, but it does suck to have to babysit every single boot of the machine. Like I said earlier, its not just a long boot time, its a total hang during boot. Nothing responds except for the power switch.

---

### Post by ilyvm1 on 2013-06-21
> **osarusan said:**
> This has happened with upgrades and with clean installs. This one now is a clean install.

I'll try it with Gnome Classic, though I do prefer Unity.

What would setting nomodeset do?



--
edit: Using Gnome Classic and Unity 2d did not help. Still hangs at boot.

I did not experience joy with my 12.04 setup (problems with
boot, plymouth, gdm, unity) until as root, I:
# cd /boot; grep -lr CONFIG_ACPI_PROCFS_POWER * 2>/dev/null |sort

then, in the generic file above (the one you're booting!)
change:
CONFIG_ACPI_PROCFS_POWER=y
to:
CONFIG_ACPI_PROCFS_POWER=n

all seems ok now.

---

