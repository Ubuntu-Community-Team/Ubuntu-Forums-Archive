---
title: "Login Window Problem"
date: 2006-06-06
forum: General Help
---

### Post by Blarion on 2006-06-06
Whenever I go into Login Window setup in my system preferences, the window stays open for a second and then shuts. What do I do. I think it might have something to do with me installing XGL/Compiz yesterday. Not really sure.

---

### Post by Blarion on 2006-06-06
Got rid of XGL and Compiz, the problem is still there.

---

### Post by mlind on 2006-06-06
Do you mean gdmsetup dialog?

try launching
```

gksu gdmsetup

```
from terminal, and post any errors it prints out.

---

### Post by Blarion on 2006-06-06
No errors... didn't print anything at all.

---

### Post by marks_linux on 2006-06-13
Same here but I get:

sudo gksu gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.


any way round it?

---

### Post by mlind on 2006-06-13
[QUOTE=marks_linux]Same here but I get:

sudo gksu gdmsetup

any way round it?[/QUOTE]

use only either sudo or gksu, but not both. gksu basically just offers GUI for
sudo password prompt. You can troubleshoot this using ltrace or strace.

try

```

sudo ltrace gdmsetup.

```

Output is probably very long and maybe too verbose, but can give a hint
about what's wrong here.

---

### Post by arpels on 2006-10-09
Hi Mark, 

Did you maneged to solve this problem ? 

I'm getting exactly the same at the moment. it started to happend after i put KDE on top of ubuntu. 


> **marks_linux said:**
> Same here but I get:

sudo gksu gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.


any way round it?

---

### Post by kanna1620 on 2007-01-13
> **mlind said:**
> Do you mean gdmsetup dialog?

try launching
```

gksu gdmsetup

```
from terminal, and post any errors it prints out.

I tried what you said but it is saying that
could not acces GDM configuration file.
The same errors occured when i type gksu gdmsetup as above.
Plz some one help me

---

### Post by mnhercules84 on 2007-01-30
> **arpels said:**
> Hi Mark, 

Did you maneged to solve this problem ? 

I'm getting exactly the same at the moment. it started to happend after i put KDE on top of ubuntu.
I have the same problem :(

---

### Post by salocinbake on 2007-02-01
Ever since I installed Kde desktop, I have the same problem. Try to acces under Gnome and KDE   same result:

misterx-desktop:~$ gksu gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

Looking forward to solve this.

Thanks

---

### Post by RuarriS on 2007-02-13
I also have the same problem with the login window manager not opening. It seemed to only happen after I tried kde for a bit and then removed it.

---

### Post by beams on 2007-02-15
I had the same problem and tried all the possible solutions on the forums but no luck.

I have just resolved however by removing ALL packages with kdm in the name (lots), and installing  all packages with gdm in the name (only a few, some already installed, some only themes).

Probably overkill on my part but I now have a system with gdm login screen, and ability to run gdmsetup gui i.e. System->Administration->Login Window

Hope that helps someone.

---

### Post by mohasr on 2007-02-22
I had the same problem as well. I fixed it by reinstalling gdm from synaptic

it maybe just a missing file or so.

---

### Post by mohasr on 2007-02-23
err...

sorry to report that the problem reappeared once I rebooted...

still looking for a fix

---

### Post by 16777216 on 2007-02-25
Mine is doing it too. I was thinking about switching to KDM but it looks that might make things worse.

---

### Post by 16777216 on 2007-02-25
I did a > sudo ltrace gdmsetup and have attached the output below.

Sorry about the archive but that was the only way to post the output.

---

### Post by Iceni on 2007-02-26
Anyone found a solution to this? I have the same problem, running Edgy with Beryl.

---

### Post by mlind on 2007-02-26
does /var/log/gdm/:0.log, /var/log/syslog or ~/.xsession-errors contain any details why it's failing?

---

### Post by Iceni on 2007-02-26
Unless this is related:

Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.

there is nothing regarding this problem.

---

### Post by Iceni on 2007-02-26
I found something I belive can be related:
Could not access GDM configuration file.
(synaptic:1127): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
X connection to :0.0 broken (explicit kill or server shutdown).

Looks like it might be connected to the flash player somehow, but that seems really really weird. Any suggestions?

---

### Post by 16777216 on 2007-02-27
/var/log/gdm/0.log

```
_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/AMD-64-MAIN-LINUX:0
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux AMD-64-MAIN-LINUX 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686
Build Date: 07 July 2006
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 26 23:07:41 2007
(==) Using config file: "/etc/X11/xorg.conf"
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us" };
    xkb_geometry             { include "pc(pc105)" };
```The lines that pertain to GDM in ~/.xsession-errors

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "paul"
/etc/gdm/Xsession: Beginning session setup...
```

---

### Post by Iceni on 2007-02-28
I'm posting the files here, if anyone could look at them that would be fantastic:

**0.log**
> 
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux moridin 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 28 16:54:55 2007
(==) Using config file: "/etc/X11/xorg.conf"
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+no" };
    xkb_geometry             { include "pc(pc105)" };
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!


**Xsession-errors**
> Feb 28 17:00:48 moridin syslogd 1.4.1#18ubuntu6: restart.
Feb 28 17:00:48 moridin anacron[4398]: Job `cron.daily' terminated
Feb 28 17:00:48 moridin anacron[4398]: Normal exit (1 job run)
Feb 28 17:15:52 moridin gconfd (root-5896): starting (version 2.16.0), pid 5896 user 'root'
Feb 28 17:15:53 moridin gconfd (root-5896): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb 28 17:15:53 moridin gconfd (root-5896): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Feb 28 17:15:53 moridin gconfd (root-5896): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb 28 17:15:53 moridin gconfd (root-5896): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb 28 17:15:53 moridin gconfd (root-5896): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Feb 28 17:16:23 moridin gconfd (root-5896): GConf server is not in use, shutting down.
Feb 28 17:16:23 moridin gconfd (root-5896): Exiting
Feb 28 17:17:01 moridin /USR/SBIN/CRON[5933]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb 28 17:17:08 moridin gconfd (root-5939): starting (version 2.16.0), pid 5939 user 'root'
Feb 28 17:17:08 moridin gconfd (root-5939): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb 28 17:17:08 moridin gconfd (root-5939): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Feb 28 17:17:08 moridin gconfd (root-5939): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb 28 17:17:08 moridin gconfd (root-5939): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb 28 17:17:08 moridin gconfd (root-5939): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4


Thanks in advance!

---

### Post by BMWolfgang on 2007-03-04
hi, don't know if this might help you

[http://www.ubuntuforums.org/showthread.php?p=2248101#post2248101](http://www.ubuntuforums.org/showthread.php?p=2248101#post2248101)

---

### Post by virtualXTC on 2007-03-05
Worked for me!  Thanks!
Just in case the link every breaks it's a good idea to also copy over the solution.  In this case I will simplify it:

```
$ sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/S21gdm
```

Also note,  this is a init fix and therefore requires a reboot.

---

