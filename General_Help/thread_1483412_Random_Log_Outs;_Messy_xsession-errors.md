---
title: "Random Log Outs; Messy xsession-errors"
date: 2010-05-14
forum: General Help
---

### Post by jam_ on 2010-05-14
I've returned to my computer several times to find that I've been logged out. Based on my ~/.xsession-errors, I believe that my desktop is crashing (but it has never happened when I was sitting at the computer). There are no errors that I can find in dmesg, kern, or X.org or other relevant system log files.

Regarding the "Messy xsession-errors", I'm getting hundreds of thousands of lines of output from kmail (specifically kio_imap4) and amarok (QVariant calls, among others), plus excessive output from gmplayer, and ALL of my global shortcut key presses are being logged (e.g. alt-tab). I've trimmed the output to only display the crash and last few lines of normal output, but certainly all of this writing to disk and mucking up the log file with useless messages should not be happening, right?

I think the key line in the error is: ```
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 394169 requests (394168 known processed) with 3 events  remaining.
```I just don't know what is causing it or how to diagnose what is causing it. 

System details:
64bit Kubuntu 10.04, upgraded from 9.10. file system ext4 (upgraded from ext3)

```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300

``````

kio_imap4(6295)/kio_imap IMAP4Protocol::parseURL: IMAP4::parseURL - namespace= "INBOX."
kio_imap4(6295)/kio_imap IMAP4Protocol::parseURL: IMAP4::parseURL - delimiter= "."
kio_imap4(6295)/kio_imap IMAP4Protocol::parseURL: IMAP4::parseURL - box= "INBOX.Classes"
kio_imap4(6295)/kio_imap IMAP4Protocol::parseURL: IMAP4::parseURL - return 2
kio_imap4(6295)/kio_imap IMAP4Protocol::assureBox: IMAP4Protocol::assureBox - reusing box
kio_imap4(6295)/kio_imap IMAP4Protocol::get: IMAP4::get -  finished
kio_imap4(6295)/kio_imap IMAP4Protocol::dispatch: IMAP4::dispatch - command= 80
kio_imap4(6295)/kio_imap IMAP4Protocol::dispatch: IMAP4::dispatch - command= 77
kio_imap4(6295)/kio_imap IMAP4Protocol::special: IMAP4Protocol::special
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 394169 requests (394168 known processed) with 3 events remaining.
kxkb: Fatal IO error: client killed
kded4: Fatal IO error: client killed
kdeinit4: Fatal IO error: client killed
kdeinit4: sending SIGHUP to children.
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Mute" for "kmix" : "mute"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Down" for "kmix" : "decrease_volume"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Up" for "kmix" : "increase_volume"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+K" for "kwin" : "Window One Desktop Up"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+J" for "kwin" : "Window One Desktop Down"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+L" for "kwin" : "Window One Desktop to the Right"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+L" for "kwin" : "Switch One Desktop to the Right"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Space" for "kwin" : "Window Operations Menu"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+H" for "kwin" : "Switch One Desktop to the Left"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Right" for "kwin" : "Switch Window Right"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Left" for "kwin" : "Switch Window Left"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+H" for "kwin" : "Window One Desktop to the Left"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+J" for "kwin" : "Switch One Desktop Down"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+K" for "kwin" : "Switch One Desktop Up"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Shift+Del" for "krunner" : "Log Out Without Confirmation"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Esc" for "krunner" : "Show System Activity"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F2" for "krunner" : "Run Command"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Shift+PgDown" for "krunner" : "Halt Without Confirmation"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Shift+PgUp" for "krunner" : "Reboot Without Confirmation"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+L" for "krunner" : "Lock Session"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Del" for "krunner" : "Log Out"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F2" for "krunner" : "Run Command on clipboard contents"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Ins" for "krunner" : "Switch User"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+D" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F1" for "plasma-desktop" : "activate widget 20"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Print" for "khotkeys" : "{755e1ffd-b21f-404b-a618-7407a08a9969}"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Search" for "khotkeys" : "{d03619b6-9b3c-48cc-9d9c-a2aadb485550}"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta++" for "amarok" : "increaseVolume"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+M" for "amarok" : "mute"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift++" for "amarok" : "seek_forward"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+N" for "amarok" : "next"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+B" for "amarok" : "prev"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+V" for "amarok" : "stop"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+1" for "amarok" : "rate1"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+2" for "amarok" : "rate2"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+3" for "amarok" : "rate3"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+4" for "amarok" : "rate4"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+5" for "amarok" : "rate5"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+A" for "amarok" : "playlist_add"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+S" for "amarok" : "skipTrack"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+V" for "amarok" : "stop_after_current"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+-" for "amarok" : "seek_backward"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+P" for "amarok" : "play_pause"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Shift+I" for "kopete" : "ReadMessage"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Shift+S" for "kopete" : "ShowContactList"
kglobalaccel(1508) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Shift+W" for "kopete" : "Set_Away_Back"
klauncher: Exiting on signal 1
klauncher(1412)/kio (KLauncher): SlavePool: No communication with slave.

kdeinit4: sending SIGTERM to children.
kdeinit4: Exit.
*** KMail got signal 15 (Exiting)
KCrash: Application 'ksmserver' crashing...
Warning: connect() failed: : No such file or directory
KCrash cannot reach kdeinit, launching directly.
Unexpected response from KInit (response = 0).
ksmserver: Fatal IO error: client killed
startkde: Could not start ksmserver. Check your installation.
*** KMail got signal 11 (Crashing)
ICE default IO error handler doing an exit(), pid = 1514, errno = 11
[/usr/bin/akonadi_ical_resource] ICE default IO error handler doing an exit(), pid = 4406, errno = 11
[/usr/bin/akonadi_ical_resource] ICE default IO error handler doing an exit(), pid = 4407, errno = 11
[/usr/bin/akonadi_maildispatcher_agent] ICE default IO error handler doing an exit(), pid = 4409, errno = 11
[/usr/bin/akonadi_vcard_resource] ICE default IO error handler doing an exit(), pid = 4411, errno = 11
[/usr/bin/akonadi_vcard_resource] ICE default IO error handler doing an exit(), pid = 4412, errno = 11
[/usr/bin/akonadi_birthdays_resource] ICE default IO error handler doing an exit(), pid = 4405, errno = 11
[/usr/bin/akonadi_maildir_resource] ICE default IO error handler doing an exit(), pid = 4408, errno = 11
[/usr/bin/akonadi_nepomuk_contact_feeder] ICE default IO error handler doing an exit(), pid = 4410, errno = 11
QSocketNotifier: Invalid socket 9 and type 'Read', disabling...
QSocketNotifier: Invalid socket 21 and type 'Read', disabling...
kontact: Fatal IO error: client killed
ProcessControl: Application '/usr/bin/akonadi_birthdays_resource' returned with exit code 1 (Unknown error)
ProcessControl: Application '/usr/bin/akonadi_maildir_resource' returned with exit code 1 (Unknown error)
ProcessControl: Application '/usr/bin/akonadi_nepomuk_contact_feeder' returned with exit code 1 (Unknown error)
ProcessControl: Application '/usr/bin/akonadi_maildispatcher_agent' returned with exit code 1 (Unknown error)
kglobalaccel: Fatal IO error: client killed
kscreenlocker: Fatal IO error: client killed
kdeinit4: Fatal IO error: client killed
kdeinit4: sending SIGHUP to children.
ProcessControl: Application '/usr/bin/akonadi_vcard_resource' returned with exit code 1 (Unknown error)
ProcessControl: Application '/usr/bin/akonadi_vcard_resource' returned with exit code 1 (Unknown error)
ProcessControl: Application '/usr/bin/akonadi_ical_resource' returned with exit code 1 (Unknown error)
ProcessControl: Application '/usr/bin/akonadi_ical_resource' returned with exit code 1 (Unknown error)
D-Bus session bus went down - quitting
drkonqi: cannot connect to X server :0.0
kdeinit4: sending SIGTERM to children.
kdeinit4: Exit.
[/usr/bin/akonadi_nepomuk_contact_feeder] No protocol specified
[/usr/bin/akonadi_nepomuk_contact_feeder] akonadi_nepomuk_contact_feeder: cannot connect to X server :0.0
ProcessControl: Application '/usr/bin/akonadi_nepomuk_contact_feeder' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_maildispatcher_agent] akonadi_maildispatcher_agent: cannot connect to X server :0.0
ProcessControl: Application '/usr/bin/akonadi_maildispatcher_agent' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_ical_resource] No protocol specified
[/usr/bin/akonadi_ical_resource] akonadi_ical_resource: cannot connect to X server :0.0
ProcessControl: Application '/usr/bin/akonadi_ical_resource' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_maildir_resource] akonadi_maildir_resource: cannot connect to X server :0.0
ProcessControl: Application '/usr/bin/akonadi_maildir_resource' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_ical_resource] No protocol specified
[/usr/bin/akonadi_ical_resource] akonadi_ical_resource: cannot connect to X server :0.0
ProcessControl: Application '/usr/bin/akonadi_ical_resource' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_vcard_resource] No protocol specified
[/usr/bin/akonadi_vcard_resource] akonadi_vcard_resource: cannot connect to X server :0.0
ProcessControl: Application '/usr/bin/akonadi_vcard_resource' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_vcard_resource] No protocol specified
[/usr/bin/akonadi_vcard_resource] akonadi_vcard_resource: cannot connect to X server :0.0
ProcessControl: Application '/usr/bin/akonadi_vcard_resource' returned with exit code 1 (Unknown error)
[/usr/bin/akonadi_birthdays_resource] No protocol specified
[/usr/bin/akonadi_birthdays_resource] akonadi_birthdays_resource: cannot connect to X server :0.0
ProcessControl: Application '/usr/bin/akonadi_birthdays_resource' returned with exit code 1 (Unknown error)
[akonadiserver] D-Bus session bus went down - quitting
[akonadiserver] terminating service threads
[akonadiserver] terminating connection threads
[akonadiserver] stopping db process
Application 'akonadiserver' exited normally...

```

---

### Post by Zorael on 2010-05-17
If Xorg.0.log doesn't mention any errors, does **kdm.log**? (I know you said no relevant system logs did, but kdm.log is where they should be.)

As for .xsession-errors being verbose, try starting '**kdebugdialog**' and check Disable all debug output. If that doesn't help, you can still save your harddisk the extra write activity by making a startup script that deletes the file and replaces it with a symbolic link pointing it to **/dev/null**.

```
#!/bin/bash

rm ~/.xsession-errors
ln -s /dev/null ~/.xsession-errors
```
Save it in **~/.kde/env/** with a **.sh** extension, and set it executable.

---

### Post by jam_ on 2010-05-17
kdebugdialog is definitely a new one for me. I've clicked, we'll see how that works out. Thanks for the heads up. Could link it to /dev/null, maybe, but I do want it around, especially with these random crashes occuring.

As for kdm.log . . . I totally forgot to check that one. And it has a long list of complaints indeed. See below. Looks like a problem in the intel driver, right? Not sure that it is a known error or not (Googling literally gives zero results for even relatively truncated versions of those errors). I do see that it cannot find zenity, not sure what it is wanting to prompt me to do with that, but I've installed it so that I can find out next time. I should probably file a bug that the error dialog for kdm depends on something that it doesn't automatically pull in.

```

I830PMEvent: Capability change
../../intel/intel_bufmgr_gem.c:876: Error mapping buffer 36316 (binding_table): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 925 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:876: Error mapping buffer 36316 (binding_table): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 925 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:876: Error mapping buffer 36316 (binding_table): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 925 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 36312 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 36312 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 36306 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 36306 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:876: Error mapping buffer 36317 (surface_state): Cannot allocate memory .
<snip out about 8000 lines of that>
Fatal server error:
Failed to map batchbuffer: Cannot allocate memory


Please consult the The X.Org Foundation support
     at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux sen 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=886a3a9d-4d2f-466a-8255-c399006915cb ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May 14 13:31:40 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/1044635418/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address.
IBusInputContext::createInputContext: no connection to ibus-daemon
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/1831751730/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address.
IBusInputContext::createInputContext: no connection to ibus-daemon
kdmgreet: Fatal IO error: client killed
 ddxSigGiveUp: Closing log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux sen 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=886a3a9d-4d2f-466a-8255-c399006915cb ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May 14 13:54:45 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
 ddxSigGiveUp: Closing log
md5sum: /etc/X11/xorg.conf: No such file or directory
/etc/gdm/failsafeXServer: line 141: /var/log/gdm/failsafe.log: No such file or directory
Warning:  Cannot write to /var/log/gdm/failsafe.log
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X  -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux sen 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=886a3a9d-4d2f-466a-8255-c399006915cb ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Fri May 14 13:54:51 2010
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
<snip about 200 lines of that>
/etc/gdm/failsafeXinit: line 184: zenity: command not found
/etc/gdm/failsafeXinit: line 47: zenity: command not found

waiting for X server to shut down
Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a3248]
1: /usr/bin/X (0x400000+0x655ad) [0x4655ad]
2: /lib/libpthread.so.0 (0x7f0788e3b000+0xf8f0) [0x7f0788e4a8f0]
3: /usr/bin/X (DamageUnregister+0x53) [0x4d72f3]
4: /usr/lib/xorg/modules/libshadow.so (shadowRemove+0x33) [0x7f078576b3c3]
5: /usr/lib/xorg/modules/libshadow.so (0x7f078576a000+0x1884) [0x7f078576b884]
6: /usr/bin/X (0x400000+0xa77d9) [0x4a77d9]
7: /usr/bin/X (0x400000+0x16852c) [0x56852c]
8: /usr/bin/X (0x400000+0x2624c) [0x42624c]
9: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f0787b33c4d]
10: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Segmentation fault at address (nil)

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support
     at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.

 ddxSigGiveUp: Closing log



X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux sen 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=886a3a9d-4d2f-466a-8255-c399006915cb ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May 14 13:55:06 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/1567252080/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address.
IBusInputContext::createInputContext: no connection to ibus-daemon

```

---

### Post by Zorael on 2010-05-18
Where are these two snippets from? (Which file? Both kdm.log?) Are they from the same crash?
```
I830PMEvent: Capability change
../../intel/intel_bufmgr_gem.c:876: Error mapping buffer 36316 (binding_table): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 925 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:876: Error mapping buffer 36316 (binding_table): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 925 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:876: Error mapping buffer 36316 (binding_table): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 925 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 36312 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 36312 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 36306 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:957: Error mapping buffer 36306 (pixmap): Cannot allocate memory .
../../intel/intel_bufmgr_gem.c:876: Error mapping buffer 36317 (surface_state): Cannot allocate memory .
<snip out about 8000 lines of that>
Fatal server error:
Failed to map batchbuffer: Cannot allocate memory
```
This one might make sense to the right mind.

```
Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a3248]
1: /usr/bin/X (0x400000+0x655ad) [0x4655ad]
2: /lib/libpthread.so.0 (0x7f0788e3b000+0xf8f0) [0x7f0788e4a8f0]
3: /usr/bin/X (DamageUnregister+0x53) [0x4d72f3]
4: /usr/lib/xorg/modules/libshadow.so (shadowRemove+0x33) [0x7f078576b3c3]
5: /usr/lib/xorg/modules/libshadow.so (0x7f078576a000+0x1884) [0x7f078576b884]
6: /usr/bin/X (0x400000+0xa77d9) [0x4a77d9]
7: /usr/bin/X (0x400000+0x16852c) [0x56852c]
8: /usr/bin/X (0x400000+0x2624c) [0x42624c]
9: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f0787b33c4d]
10: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Segmentation fault at address (nil)
```
This here shows the crash as it happened, but you're missing the debugging symbols so only the memory addresses are shown.
```
$ sudo aptitude install xserver-xorg-core-dbg libc6-dbg   # may be huge
```
I'd recommend you install those and then try to catch the logs of the next crash. Perhaps the backtrace will then show names of functions you can google. And in any case, you'll have much better basis for a bug report.

---

### Post by jam_ on 2010-05-19
Yes, those both came from a kdm.log file, the same file, I suspect different crashes though. There appears to be multiple X starts there, and FWIW, I'm pretty sure that the backtrace follows a failed server restart and not the initial crash (not that that isn't necessarily relevant, but also not obviously the root of the problem). I say that because it follows the zenity not found message, which ends up being a dialog that gets brought up, I think post-restart, complaining about going into low graphics mode. The dialog was basically non-reactive though. I asked it to automatically reconfigure, it didn't seem to actually do anything (maybe that was just backgrounded), then restarted the X server and all was dandy (until the next crash, which did not prompt the low graphics mode zenity dialog).

I've installed the debug symbols. Some of the crashes leave backtraces, some don't. Hopefully, the next crash will produce something useful.

---

