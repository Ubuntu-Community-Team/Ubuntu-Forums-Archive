---
title: "Booting suddenly fails"
date: 2011-11-04
forum: General Help
---

### Post by miss-sawa on 2011-11-04
Hi, 

'simple' problem: since yesterday, my Laptop won't boot. The last things I did was installing updates and uninstalling unity, but I don't think that's what caused the problem.
I get as far as choosing my linux version and getting to the first ubuntu splashscreen. after that, this is what happens:

[http://img830.imageshack.us/img830/9697/img8632i.jpg](http://img830.imageshack.us/img830/9697/img8632i.jpg) (It's huge.)

Waiting for 5 minutes doesn't help.
A friend of mine who's more into the entire programming stuff got as far as finding out that there is also some 'chip ID error' somewhere, but I don't know how he found that or what it means.

Also, the thinkfan problem is probably not it, I guess. I've had it before some week ago and it didn't actually keep the PC from booting.

Booting in recovery mode doesn't work either, it freezes at the same spot.

I'm running on a TP x220T, in case that matters.

Any help and ideas will be appreciated. Try to keep it newb-friendly though! (:

---

### Post by hwttdz on 2011-11-04
If you alt+ctrl+f2 do you get to a working terminal you can login at?

If you "sudo service lightdm start" at that terminal do you get a working login screen, what if you replace lightdm with xdm? gdm?

---

### Post by whilo on 2011-11-04
Got you here :-) Can you boot in another environment like failsafe, other distro, livecd and get the log files of the broken system? /var/log/messages or /var/log/kern.log would be interesting. Also if you can ask your friend for the error and where he got it, it would be helpful :-)
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by miss-sawa on 2011-11-05
> **hwttdz said:**
> If you alt+ctrl+f2 do you get to a working terminal you can login at?

If you "sudo service lightdm start" at that terminal do you get a working login screen, what if you replace lightdm with xdm? gdm?

Yes, I can open all the terminals available.
sudo service lightdm start does apparently work, but changes nothing about the freezing. It jumps to the frozen screen and that's it. xdm can't be found and gdm gives me the same results as lightdm.


> Can you boot in another environment like failsafe, other distro, livecd  and get the log files of the broken system? /var/log/messages or  /var/log/kern.log would be interesting. Also if you can ask your friend  for the error and where he got it, it would be helpfuThis is a copy of my kern.log from Nov. 3 and on (had to zip it because it's too huge). I dare to assume that what happened before it is not that important, since 3rd was the day it stopped working. If it is, I can add it.
My friend's gone during the weekend, so I can't ask him before tomorrow somewhen.

---

### Post by whilo on 2011-11-05
One quick unrelated note first:
> 
ACPI FADT declares the system doesn't support PCIe ASPM, so disable it

Once your system runs again you might want to try and add "pcie_aspm=force" to your kernel boot parameters. Since you use SandyBridge graphics, you might also want to try "i915.i915_enable_rc6=1". Both have a considerable effect on battery life time, but might still fail to work in some circumstances. I hope a ThinkPad is safe. Just don't add it to the failsafe kernel, so you have a safe way to remove them if they break something.

> Nov  3 09:18:21 ThinkPad-med-kuken kernel: [   18.269868] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  3 09:18:22 ThinkPad-med-kuken kernel: [   19.339094] init: failsafe main process (871) killed by TERM signal
Nov  3 09:18:22 ThinkPad-med-kuken kernel: [   19.389584] init: gdm main process (1073) killed by TERM signal
Nov  3 09:18:23 ThinkPad-med-kuken kernel: [   19.435764] init: apport pre-start process (1052) terminated with status 1
Nov  3 09:18:23 ThinkPad-med-kuken kernel: [   19.437470] init: apport post-stop process (1082) terminated with status 1

or

> Nov  5 11:27:17 ThinkPad-med-kuken kernel: [   21.095742] init: failsafe main process (825) killed by TERM signal
Nov  5 11:27:17 ThinkPad-med-kuken kernel: [   21.097704] init: apport pre-start process (925) terminated with status 1
Nov  5 11:27:17 ThinkPad-med-kuken kernel: [   21.099817] hdaps: supported laptop not found!
Nov  5 11:27:17 ThinkPad-med-kuken kernel: [   21.099819] hdaps: driver init failed (ret=-19)!
Nov  5 11:27:17 ThinkPad-med-kuken kernel: [   21.112445] init: apport post-stop process (953) terminated with status 1
Nov  5 11:27:17 ThinkPad-med-kuken kernel: [   21.120447] init: gdm main process (967) killed by TERM signal

and only a second later:

> Nov  5 11:27:18 ThinkPad-med-kuken kernel: [   21.996147] init: anacron main process (975) killed by TERM signal
Nov  5 11:27:19 ThinkPad-med-kuken kernel: [   22.898716] init: lightdm main process (961) terminated with status 1

Looks like the best candidate. It happens several seconds before the fan driver causing the error message is loaded, so the fan is not related. Somehow the failsafe process gets killed first pulling gdm, anacron and lightdm with it. Now we need to find out what kills them and why. Maybe you can attach /var/log/messages? 

Seeking for the first error: "init: failsafe main process" gives these similar hits
[http://askubuntu.com/questions/67998/reboot-shutdown-fails-with-ubuntu-11-10](http://askubuntu.com/questions/67998/reboot-shutdown-fails-with-ubuntu-11-10)
[http://ubuntuforums.org/showthread.php?t=1869545](http://ubuntuforums.org/showthread.php?t=1869545)
[http://forum.ubuntuusers.de/topic/ubuntu-10-04-startet-nicht-mehr-1/#post-2519219](http://forum.ubuntuusers.de/topic/ubuntu-10-04-startet-nicht-mehr-1/#post-2519219)

The last poster has reinstalled, because he had removed too many packages. Can you post /var/log/apt/history.log from the Unity uninstall till now as well?

This is some work. If you feel stressed or need the machine working and don't feel like tracking this 'bastard' down, you can first try reinstall Unity and see if this magically fixes the issue and if not reinstall the system. If you don't like Unity anyway, how about chosing a different Ubuntu blend from the start? Usually adding/removing desktop environments works, but for sake of simplicity and quick access to your machine this might bear the least frustration :-) Do you need the machine or feel like tracking the bug down?

Gruß
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by miss-sawa on 2011-11-05
/var/log/messages doesn't exist for some reason, but I got the history attached ;)

Assuming reinstalling Unity would help (just for having the files and letting them rot anyway), how can I do that? 
I do depend on the computer for school, so I'd like to avoid having to reinstall the system.

---

### Post by whilo on 2011-11-05
Hmm, only unity packages in there. Either Ubuntu has some problem with packaging these or this is unrelated. For now I'd assume the later, can you pin point that the first time this problem occured was directly after you uninstalled Unity or has it happened before? You uninstalled Unity on the 3.11. and the boot log suggests that error has happened since that every time. What confuses me is that every boot since the same time has a 20-30s break in boot logs, always after /dev/sda2 has been mounted:

> Nov  3 12:13:52 ThinkPad-med-kuken kernel: [    2.117722] usb 1-1.3: new full speed USB device number 3 using ehci_hcd
Nov  3 12:13:52 ThinkPad-med-kuken kernel: [    2.281519] usb 1-1.4: new full speed USB device number 4 using ehci_hcd
Nov  3 12:13:52 ThinkPad-med-kuken kernel: [    2.293325] ata2: SATA link down (SStatus 0 SControl 300)
Nov  3 12:13:52 ThinkPad-med-kuken kernel: [    2.457128] usb 1-1.6: new high speed USB device number 5 using ehci_hcd
Nov  3 12:13:52 ThinkPad-med-kuken kernel: [    2.629011] usb 2-1.5: new full speed USB device number 3 using ehci_hcd
Nov  3 12:13:52 ThinkPad-med-kuken kernel: [    2.675605] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Nov  3 12:13:52 ThinkPad-med-kuken kernel: [   31.906446] Adding 7812092k swap on /dev/sda4.  Priority:-1 extents:1 across:7812092k
Nov  3 12:13:52 ThinkPad-med-kuken kernel: [   32.096383] type=1400 audit(1320318831.217:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=697 comm="apparmor_parser"
Nov  3 12:13:52 ThinkPad-med-kuken kernel: [   32.096390] type=1400 audit(1320318831.217:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=800 comm="apparmor_parser"
Nov  3 12:13:52 ThinkPad-med-kuken kernel: [   32.096680] type=1400 audit(1320318831.217:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=697 comm="apparmor_parser"
Nov  3 12:13:52 ThinkPad-med-kuken kernel: [   32.096685] type=1400 audit(1320318831.217:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=800 comm="apparmor_parser"
Nov  3 12:13:52 ThinkPad-med-kuken kernel: [   32.096868] type=1400 audit(1320318831.217:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=697 comm="apparmor_parser"
Nov  3 12:13:52 ThinkPad-med-kuken kernel: [   32.096875] type=1400 audit(1320318831.217:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=800 comm="apparmor_parser

Is root on /dev/sda2? Have you connected some "weird" USB devices?

If messages is missing maybe /var/log/daemon or /var/log/syslog exist? Puuh, now I really should get back to my maths stuff, hope this helps to track it further down. 
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by miss-sawa on 2011-11-05
It definitely only occured after I uninstalled Unity. Before that it  booted fluently, apart from the one time where it gave me the thinkfan  message but booted anyway. That was a one time-happening.
I uninstalled Unity during Maths class, shut down the computer because I  was writing an exam in the next lesson and after the exam the error  occured for the first time.

sda2 is my root, yes. No USBs or SD cards were attached (since I set USB on top of the boot list).

no daemon, but syslog:

---

### Post by whilo on 2011-11-05
Does sound work? The pulseaudio error looks serious and happens before failsafe and the other processes are killed: > [pulseaudio] module-alsa-card.c: Failed to find a working profile. Use cvlc to test from command line for example. This shouldn't kill the boot process though, so try first to find out about this:

> Nov  3 12:08:17 ThinkPad-med-kuken kernel: [   20.772004] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Nov  3 12:08:17 ThinkPad-med-kuken kernel: [   20.772389] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  3 12:08:17 ThinkPad-med-kuken kernel: [   20.776844] init: apport post-stop process (1020) terminated with status 1
Nov  3 12:08:17 ThinkPad-med-kuken anacron[1025]: Anacron 2.3 started on 2011-11-03
Nov  3 12:08:17 ThinkPad-med-kuken cron[1026]: (CRON) STARTUP (fork ok)
Nov  3 12:08:17 ThinkPad-med-kuken cron[1026]: (CRON) INFO (Running @reboot jobs)
Nov  3 12:08:18 ThinkPad-med-kuken anacron[1025]: Will run job `cron.daily' in 5 min.
Nov  3 12:08:18 ThinkPad-med-kuken anacron[1025]: Jobs will be executed sequentially
Nov  3 12:08:18 ThinkPad-med-kuken kernel: [   20.912947] init: alsa-restore main process (997) terminated with status 99
Nov  3 12:08:18 ThinkPad-med-kuken kernel: [   20.946155] hdaps: supported laptop not found!
Nov  3 12:08:18 ThinkPad-med-kuken kernel: [   20.946158] hdaps: driver init failed (ret=-19)!

Try to run apport manually, check how to do that with ```
man  apport
``` I guess it is ```
sudo apport
```, but don't have  Ubuntu here atm. It might tell you about the program that crashed and  where it did.

The cron startup also looks suspicious: 
> 
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.821918] Console: switching to colour frame buffer device 170x48
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.821937] fb0: inteldrmfb frame buffer device
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.821938] drm: registered panic notifier
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.823750] acpi device:01: registered as cooling_device4
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.823991] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.824077] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.824278] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.824319] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.824371] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.824400] HDA Intel 0000:00:1b.0: setting latency timer to 64
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.854067] hdaps: supported laptop not found!
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.854069] hdaps: driver init failed (ret=-19)!
Nov  3 12:06:47 ThinkPad-med-kuken cron[963]: (CRON) INFO (pidfile fd = 3)
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.868753] init: failsafe main process (845) killed by TERM signal
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.869108] init: apport pre-start process (949) terminated with status 1
Nov  3 12:06:47 ThinkPad-med-kuken acpid: starting up with proc fs
Nov  3 12:06:47 ThinkPad-med-kuken acpid: 32 rules loaded
Nov  3 12:06:47 ThinkPad-med-kuken acpid: waiting for events: event logging is off
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.879588] init: apport post-stop process (972) terminated with status 1
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.882010] init: gdm main process (980) killed by TERM signal
Nov  3 12:06:47 ThinkPad-med-kuken anacron[998]: Anacron 2.3 started on 2011-11-03
Nov  3 12:06:47 ThinkPad-med-kuken cron[1009]: (CRON) STARTUP (fork ok)
Nov  3 12:06:47 ThinkPad-med-kuken cron[1009]: (CRON) INFO (Running @reboot jobs)

It starts up only to get killed a second later. It says something about reboot jobs. Have you shutdown cleanly after the package removal has successfully finished or quickly put it off(!)? Run ```
sudo apt-get update && sudo apt-get -f dist-upgrade
``` and if this does not do anything or fixes the problem run ```
sudo crontab -l
``` and look into /etc/cron* if any cleanup jobs are left in there. I am a bit clueless, because there is no direct error output in the logs. Cron definitely has not enough time to run any jobs, but the killing of failsafe also happens before cron startup, so the cause is elsewhere. 

If this does not help then maybe the fan really is the reason for an emergency shutdown killing failsafe and the other boot processes:

> 
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.566234] thinkpad_acpi: THERMAL ALERT: unknown thermal alarm received
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.566237] thinkpad_acpi: unhandled HKEY event 0x6050
Nov  3 12:06:47 ThinkPad-med-kuken kernel: [   20.566239] thinkpad_acpi: please report the conditions when this event happened to [email]ibm-acpi-devel@lists.sourceforge.net[/email]

Have you tried to boot with/without power plugged in? Clueless attempt though...
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by miss-sawa on 2011-11-09
Oh well. I just gave up in the end and reinstalled the system, after I managed to save my files.
Anyway, thanks for your help and efforts :)

Also, extra huge thanks for the Kernel-thing! A friend did it for me and now my battery life is back on its 9 hours. After I reinstalled Ubuntu it suddenly only had 3 hours. I'm happy now <3

---

### Post by whilo on 2011-11-11
Likely this was best. 9 hours, wow, now I am jealous... I have two and a bit on my SandyBridge laptop, but my laptop is also rather focused on power than on battery life, so I have to live with it... 9 hours... :-D
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

