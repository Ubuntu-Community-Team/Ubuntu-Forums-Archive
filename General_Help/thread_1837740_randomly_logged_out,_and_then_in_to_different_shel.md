---
title: "randomly logged out, and then in to different shell"
date: 2011-09-02
forum: General Help
---

### Post by F.G. on 2011-09-02
hey folkes,
so i posted about this a while ago, but didn't get any replies.  it has just happened again, on a different laptop with a different version of Ubuntu.

the issue is on my laptop (toshiba satellite pro L300 with natty narwhal) and now just happened with my netbook (Asus 1005-px with 10.04).

what happens is that, without any warning my screen goes black and i see some boot style text.  then i'm faced with a log in screen (NOT cmd line but with xserver running and full GUI).  it turns out if i press 'Ctrl+Alt+F7' i can see the aforementioned text, and i'm actually logging into the 'F8' (tty8\) shell.

the text ends something like:
```
 
*starting VirtualBox module
*starting the Windbind kernel windbind
PulseAudio configured for per-user sessions
saned disabled; editing /etc/default/saned

```
but is tricky to copy, for obvious reasons.  
so, i think this looks like startup text, which has now just hanged.

does anyone know what this is about?  it happened quite a few times with my laptop, and i thought it might be a hardware issue, as its quite a used and abused machine. but this netbook is really quite new, and should have nothing physically wrong.  also i'm surprised to find the same thing happening again if it isn't some other problem.

thanks for any help.  its quite unnerving working on a computer which can effectively logout without notice.

---

### Post by F.G. on 2011-09-02
so, i found the full version of the text displayed , in var/log/boot.log, here it is:
```
fsck from util-linux-ng 2.17.2
udevd[330]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-avarice.rules:4


udevd[330]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-avarice.rules:7


udevd[330]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/70-bob.rules:6


udevd[330]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/70-crossconnect.rules:6


/dev/sda1: clean, 338372/15081472 files, 11430777/60307456 blocks
 * Starting AppArmor profiles       [80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

[74G[ OK ]
Loading the saved-state of the serial devices... 
 * Setting sensors limits       [80G 
[74G[ OK ]
 [31m*[39;49m Not starting jetty - edit /etc/default/jetty and change NO_START to be 0 (or comment it out).
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Starting VirtualBox kernel modules       [128G 
[122G[ OK ]
 * Starting the Winbind daemon winbind       [128G 
[122G[ OK ]
 [33m*[39;49m PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned

```

---

### Post by F.G. on 2011-09-02
hmm... bump? 

__.-^-.__

---

