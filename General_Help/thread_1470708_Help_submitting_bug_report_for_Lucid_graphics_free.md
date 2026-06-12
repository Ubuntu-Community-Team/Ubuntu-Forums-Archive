---
title: "Help submitting bug report for Lucid graphics freezing / NVIDIA"
date: 2010-05-03
forum: General Help
---

### Post by frappe1 on 2010-05-03
Okay so I'm running a fresh install of Lucid x64 on an Intel i7 with a NVIDIA GT260 and two monitors. Every few hours, the displays will completely freeze, with the exception of the cursor which stays active. The problem seems to be biased towards when user interaction is actually happening. I can leave it alone and it will run for many hours fine, but use seems to set it off, with aggressive clicking and moving being a real problem.

The system is not frozen because I can ssh in and everything is running normally. The problem only affects the actual X session. I also can't break out to a terminal and issue any commands.....its like all input except for the cursor is being trapped and discarded.

The system is using the default noveau driver because the NVIDIA specific driver available in hardware drivers won't load, and neither will the driver package supplied by NVIDIA. Both of them when activated fail on bootup and go to the dialog asking about graphics errors at which I have to revert to last configuration and reboot.

What logs should I be looking in for documentation of the crash so I can help the developers with a well formatted and complete bug report? I want to help fix this issue but I don't know where to look and what information I need to have ready so the developers can know what is going on.

---

### Post by frappe1 on 2010-05-03
If it helps I should mention that I was running Karmic for ages with never a problem.

---

### Post by GSF1200S on 2010-05-03
> **frappe1 said:**
> Okay so I'm running a fresh install of Lucid x64 on an Intel i7 with a NVIDIA GT260 and two monitors. Every few hours, the displays will completely freeze, with the exception of the cursor which stays active. The problem seems to be biased towards when user interaction is actually happening. I can leave it alone and it will run for many hours fine, but use seems to set it off, with aggressive clicking and moving being a real problem.

The system is not frozen because I can ssh in and everything is running normally. The problem only affects the actual X session. I also can't break out to a terminal and issue any commands.....its like all input except for the cursor is being trapped and discarded.

The system is using the default noveau driver because the NVIDIA specific driver available in hardware drivers won't load, and neither will the driver package supplied by NVIDIA. Both of them when activated fail on bootup and go to the dialog asking about graphics errors at which I have to revert to last configuration and reboot.

What logs should I be looking in for documentation of the crash so I can help the developers with a well formatted and complete bug report? I want to help fix this issue but I don't know where to look and what information I need to have ready so the developers can know what is going on.

I dont know if you know this, but to avoid having to do hard reboots, hit the following key combination when the X screen freezes:
Left Alt + SysRq (print screen on some keyboards) + k

This will basically restart the X server. Have a buddy running that vid card just fine on Nvidia drivers, so it would be interesting to find out why you are having an issue. Another thread has had an exhausting time trying to fix that problem ([http://ubuntuforums.org/showthread.php?t=1466150&goto=newpost](http://ubuntuforums.org/showthread.php?t=1466150&goto=newpost)). I would include:
> /var/log/Xorg.0.log
and possibly:
```
/var/log/messages
```

That has been fine for me in the past. You might want to check your home folder for the .xsession-errors file and see what it contains. Perhaps it can tell you whats going on?

---

### Post by dino99 on 2010-05-03
Nouveau is still in development :(

is your xorg.conf customized ?

to report bug, you need to create an account on Launchpad, then into console:
 ubuntu-bug xserver-xorg-video-nouveau
(to report against "nouveau") or:
ubuntu-bug video
(to report about a video problem without knowing the real faulty package)

[http://manpages.ubuntu.com/manpages/lucid/man1/alt-nvidia-current-xconfig.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/alt-nvidia-current-xconfig.1.html)

To search about errors and logs:
into /home/.Xsession-errors (hidden file, unhide it into menu)
into menu: system-admin-log viewer

Could it be system missing power (psu or card not linked) ?

---

### Post by frappe1 on 2010-05-03
> **GSF1200S said:**
> I dont know if you know this, but to avoid having to do hard reboots, hit the following key combination when the X screen freezes:
Left Alt + SysRq (print screen on some keyboards) + k

Thank you, I will remember that combination and try it.

> **GSF1200S said:**
> 
This will basically restart the X server. Have a buddy running that vid card just fine on Nvidia drivers, so it would be interesting to find out why you are having an issue. Another thread has had an exhausting time trying to fix that problem ([http://ubuntuforums.org/showthread.php?t=1466150&goto=newpost](http://ubuntuforums.org/showthread.php?t=1466150&goto=newpost)). I would include:
That thread didn't help a bit :(

I should mention that the driver never loaded immediately after installation. After the fresh install, literally the first thing I did after entering my WPA key was trying to enable the proper driver....and nothing. So the system was basically as fresh as it could get and didn't take. I'm not sure if that info helps in resolving the bug, but I do know it can't be anything user-specific in software....hardware likely explains it. 

> **GSF1200S said:**
> 
and possibly:
```
/var/log/messages
```That has been fine for me in the past. You might want to check your home folder for the .xsession-errors file and see what it contains. Perhaps it can tell you whats going on?
There are no display related messages in /var/log/messages

The relevant .xsession-errors contains:
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-VDieGF
GNOME_KEYRING_CONTROL=/tmp/keyring-VDieGF
SSH_AUTH_SOCK=/tmp/keyring-VDieGF/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-VDieGF
SSH_AUTH_SOCK=/tmp/keyring-VDieGF/ssh

(gnome-settings-daemon:1899): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
Window manager warning: Failed to read saved session file /home/<redacted>/.config/metacity/sessions/<redacted>.ms: Failed to open file '/home/<redacted>/.config/metacity/sessions/<redacted>.ms': No such file or directory
** (nm-applet:1915): DEBUG: old state indicates that this was not a disconnect 0

(polkit-gnome-authentication-agent-1:1922): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1922): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:1917): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.0/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x11469e0'
Initializing nautilus-gdu extension

(nautilus:1914): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Unable to find a synaptics device.

(gnome-terminal:2013): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

** (gnome-screensaver:2089): WARNING **: screensaver already running in this session
** (update-notifier:2224): DEBUG: Skipping reboot required

```I don't know if this contains an actual reportable problem or if it lies elsewhere.

---

### Post by frappe1 on 2010-05-03
> **dino99 said:**
> Nouveau is still in development :(

is your xorg.conf customized ?

to report bug, you need to create an account on Launchpad, then into console:
 ubuntu-bug xserver-xorg-video-nouveau
(to report against "nouveau") or:
ubuntu-bug video
(to report about a video problem without knowing the real faulty package)

[http://manpages.ubuntu.com/manpages/lucid/man1/alt-nvidia-current-xconfig.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/alt-nvidia-current-xconfig.1.html)

To search about errors and logs:
into /home/.Xsession-errors (hidden file, unhide it into menu)
into menu: system-admin-log viewer

Could it be system missing power (psu or card not linked) ?
I'm using a completely stock xorg.conf.

Everything else is stock as well, except for me changing the display setup to spanning instead of mirroring in System > Preferences > Monitors

The system ran completely clean on Karmic for ages and was stress tested / memtested before this thread was submitted, all with no errors. Temps are carefully monitored and nowhere near trouble.

Is it appropriate to put any video bug in ubuntu-video when the package is unknown? I don't even know that a driver is to blame, but I suspect it because the system won't load the proper NVIDIA driver.

I can't even pinpoint what exactly is causing the trouble and where it might be in the logs. That basically makes a report at this point hopeless which is why I needed a bit of help identifying the relevant log entry before I submitted a report which can't help the developers.

---

### Post by dino99 on 2010-05-03
ubuntu-bug video will automatically grab all the necessary info to built the report, dont worry, you may report it (a bug not reported is not a bug)

the main log is : Xorg.0.log

into console: sudo rm -f /etc/X11/xorg*

googling around: [http://www.nvidia.com/object/linux-display-ia32-195.36.24.html](http://www.nvidia.com/object/linux-display-ia32-195.36.24.html)

---

### Post by frappe1 on 2010-05-03
According to the release notes, there are [bugs in the new kernel video architecture]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture"). Are these specific bugs something which could cause the problems I'm having, or do those bugs apply to drivers which won't load at all? I know there are many ways video bugs can happen, and I do wonder if the suggestions from the release notes would apply to my circumstances.

---

### Post by frappe1 on 2010-05-03
Just an update for anyone else who is having this problem - the instructions in the release notes were of no help in resolving the problem.

---

### Post by pricorp on 2010-05-04
> **frappe1 said:**
> Just an update for anyone else who is having this problem - the instructions in the release notes were of no help in resolving the problem.

@frappe1: Please update if you find a solution. I am having the same issue on one of my computer after upgrading to 10.04.

---

### Post by whatwoob on 2010-05-05
> **frappe1 said:**
> Okay so I'm running a fresh install of Lucid x64 on an Intel i7 with a NVIDIA GT260 and two monitors. Every few hours, the displays will completely freeze, with the exception of the cursor which stays active. The problem seems to be biased towards when user interaction is actually happening. I can leave it alone and it will run for many hours fine, but use seems to set it off, with aggressive clicking and moving being a real problem.

The system is not frozen because I can ssh in and everything is running normally. The problem only affects the actual X session. I also can't break out to a terminal and issue any commands.....its like all input except for the cursor is being trapped and discarded.

The system is using the default noveau driver because the NVIDIA specific driver available in hardware drivers won't load, and neither will the driver package supplied by NVIDIA. Both of them when activated fail on bootup and go to the dialog asking about graphics errors at which I have to revert to last configuration and reboot.

What logs should I be looking in for documentation of the crash so I can help the developers with a well formatted and complete bug report? I want to help fix this issue but I don't know where to look and what information I need to have ready so the developers can know what is going on.

I have a similar problem with my laptop: ATI video card, core 2 duo P8400 cpu, hp 6730s. I never had this problem with 9.04 which I used before upgrading to 10.04. I'm using the 32bit x86 version.

---

