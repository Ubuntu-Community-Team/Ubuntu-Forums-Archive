---
title: "help ddxSigGiveUp all through kdm log"
date: 2010-02-08
forum: General Help
---

### Post by nerdy_kid on 2010-02-08
having a few too many X crashes lately (from resume), my X log ddxSigGiveUp as the reason for the crashes, so i looked into my kdm log and found all this crap.

```

(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
 ddxSigGiveUp: Closing log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux jesse-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=17fa1623-401f-4614-8239-53163ddf4ecb ro quiet
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  8 11:03:57 2010
(==) Using config file: "/etc/X11/xorg.conf"
 ddxSigGiveUp: Closing log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux jesse-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=17fa1623-401f-4614-8239-53163ddf4ecb ro quiet
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  8 11:08:45 2010
(==) Using config file: "/etc/X11/xorg.conf"
KCrash: Application 'kdmgreet' crashing...
 ddxSigGiveUp: Closing log
drkonqi: cannot connect to X server :0.0

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux jesse-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=17fa1623-401f-4614-8239-53163ddf4ecb ro quiet
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  8 11:13:40 2010
(==) Using config file: "/etc/X11/xorg.conf"
 ddxSigGiveUp: Closing log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux jesse-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=17fa1623-401f-4614-8239-53163ddf4ecb ro quiet
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  8 11:24:45 2010
(==) Using config file: "/etc/X11/xorg.conf"
 ddxSigGiveUp: Closing log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux jesse-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=17fa1623-401f-4614-8239-53163ddf4ecb ro quiet
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  8 11:28:06 2010
(==) Using config file: "/etc/X11/xorg.conf"
KCrash: Application 'kdmgreet' crashing...
QThread::wait: Thread tried to wait on itself
QThread: Destroyed while thread is still running
drkonqi: cannot connect to X server :0.0
 ddxSigGiveUp: Closing log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux jesse-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=17fa1623-401f-4614-8239-53163ddf4ecb ro quiet
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  8 11:31:31 2010
(==) Using config file: "/etc/X11/xorg.conf"
 ddxSigGiveUp: Closing log
KCrash: Application 'kdmgreet' crashing...
drkonqi: cannot connect to X server :0.0

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux jesse-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=17fa1623-401f-4614-8239-53163ddf4ecb ro quiet
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  8 11:51:42 2010
(==) Using config file: "/etc/X11/xorg.conf"
 ddxSigGiveUp: Closing log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux jesse-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=17fa1623-401f-4614-8239-53163ddf4ecb ro quiet
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  8 11:58:58 2010
(==) Using config file: "/etc/X11/xorg.conf"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
---------------------------------------CUT------------
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
--------------------------------CUT--------------------
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xdb6400]
3: /usr/lib/xorg/modules//libwfb.so(wfbCopyNtoN+0x20f) [0x1f97ff]
4: /usr/lib/xorg/modules//libwfb.so(wfbCopyRegion+0x21b) [0x1f857b]
5: /usr/lib/xorg/modules//libwfb.so(wfbDoCopy+0x44d) [0x1f8a9d]
6: /usr/lib/xorg/modules//libwfb.so(wfbCopyArea+0x78) [0x1f8ca8]
7: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x150f4c6]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux jesse-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=17fa1623-401f-4614-8239-53163ddf4ecb ro splash quiet vga=788 quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  8 22:32:19 2010
(==) Using config file: "/etc/X11/xorg.conf"
 ddxSigGiveUp: Closing log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux jesse-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=17fa1623-401f-4614-8239-53163ddf4ecb ro splash quiet vga=788 quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  8 22:39:04 2010
(==) Using config file: "/etc/X11/xorg.conf"

```

PLEASE help me out anyway possible, this is a real pain :S
I am assuming that my gfx card isnt coming out of suspend fast enough so that X or kdm gets tired of waiting and throws a SigGiveUp...any config file i can edit to change the time period or something?  or am i totaly off.....thanks for any help!

---

### Post by nerdy_kid on 2010-02-09
bump....

---

### Post by nerdy_kid on 2010-02-10
sigh bump....

---

### Post by kentaur on 2010-04-12
Hi

I also have random crashes of X. I have no clue why this occurs, but it is terribly frustrating.

This seems to be the essential part:

```

> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xd35400]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11


```

Here is my complete/var/log/kdm.log.1:

```

The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xd35400]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ken-net-kontor 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686
Kernel command line: root=UUID=20f9e3a2-26ea-4225-b8ee-e0c188d58028 ro quiet splash 
Build Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 12 14:36:28 2010
(==) Using config file: "/etc/X11/xorg.conf"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
QFont::fromString: Invalid description 'Serif,20,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,75,0'
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server


```

---

### Post by margemoosh on 2010-05-23
same problem:(

---

