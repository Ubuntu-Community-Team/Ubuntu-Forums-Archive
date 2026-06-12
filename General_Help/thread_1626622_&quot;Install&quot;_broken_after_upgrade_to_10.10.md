---
title: "&quot;Install&quot; broken after upgrade to 10.10"
date: 2010-11-20
forum: General Help
---

### Post by phubert28 on 2010-11-20
64 bit Ubuntu 10.04 _upgraded to_ 10.10 on Dell Optiplex 360 w. 4GB RAM, Nvidia card, dual monitors, 320 & 160GB HDs.

When my WinXP hung irretrievably, I took the 64 bit Ubuntu 10.04 CD I'd burned and LET it install to the 2nd hard drive I'd purchased for that very purpose. Everything was FINE. Learning curve, of course, but forums and guys at varlinux.org were VERY helpful.

However, when 10.10 became available, I opted to upgrade.

I probably should have asked some advice before the FIRST install since I ALLOWED the install to do its own partitioning.

Anyway, after the upgrade the following do not function:

Update Manager's "Install" - does nothing - no error message
Computer Janitor - does nothing - no error message
and
PlayOnLinux update does not function.

Does anyone have some thoughts about where I might look to FIX the problems?

I've already REMOVED / installed Update Manager - no help.

I'd LIKE to be able to clean up old revs. of the OS and I'd like 10.10 to work as well as 10.04 did!

---

### Post by cariboo on 2010-11-20
Could you open an Applications->Accessories->Terminal and type:

```
update-manager
```

at the prompt, and post anything that is printed out in the terminal so that we can see what is happening when you run the command.

Just select the text in the terminal with your mouse, then right-click and select copy, before closing the terminal paste the text in to your next post. Please enclose the output in code tags eg:

[noparse]```

```[/noparse]

or just click the # sign in the advanced editor window.

---

### Post by phubert28 on 2010-11-20
> **cariboo907 said:**
> Could you open an Applications->Accessories->Terminal and type:

```
update-manager
```at the prompt, and post anything that is printed out in the terminal so that we can see what is happening when you run the command.

Just select the text in the terminal with your mouse, then right-click and select copy, before closing the terminal paste the text in to your next post. Please enclose the output in code tags eg:

[noparse]```

```[/noparse]

or just click the # sign in the advanced editor window.

With no updates to install just now, entering update-manager via terminal opens the GUI, but no messages.

No difference if I run with sudo.

Computer Janitor, OTOH, when I select "Do selected tasks" pops up the message (I lied, apparently) 

"System clean up could not complete. Be sure no other package manager such as Synaptic or Update Manager is running."

Would update-notifier qualify?? Killing notifier doesn't help, anyway.

I get the impression some switch is hard-set where it should not be.

**

When there ARE updates and I select Install, the timer circle runs for a bit & stops without anything taking place.

---

### Post by phubert28 on 2010-11-20
> **cariboo907 said:**
> Could you open an Applications->Accessories->Terminal and type:

```
update-manager
```at the prompt, and post anything that is printed out in the terminal so that we can see what is happening when you run the command.

Just select the text in the terminal with your mouse, then right-click and select copy, before closing the terminal paste the text in to your next post. Please enclose the output in code tags eg:

[noparse]```

```[/noparse]

or just click the # sign in the advanced editor window.

When I run "computer-janitor clean --all", however, I get the following:

ERROR:dbus.proxies:Introspect error on :1.52:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.58" (uid=1000 pid=9547 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.52" (uid=0 pid=9127 comm="/usr/bin/python))
ERROR:dbus.connection:Unable to set arguments (set([dbus.String(u'deb:googleearth-data'), dbus.String(u'deb:apport-hooks-medibuntu'), dbus.String(u'deb:google-chrome-beta'), dbus.String(u'deb:ubuntu-tweak'), dbus.String(u'deb:medibuntu-keyring'), dbus.String(u'deb:linux-image-2.6.32-25-generic'), dbus.String(u'file:/etc/grub.d/00_header.dpkg-old'), dbus.String(u'deb:googleearth')]),) according to signature None: <type 'exceptions.TypeError'>: Don't know how which D-Bus type to use to encode type "set"
Traceback (most recent call last):
  File "/usr/sbin/computer-janitor", line 35, in <module>
    main()
  File "/usr/share/computerjanitor/computerjanitorapp/cli/main.py", line 312, in main
    options.arguments.func(options.arguments)
  File "/usr/share/computerjanitor/computerjanitorapp/cli/main.py", line 293, in clean
    timeout=3600)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 132, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 556, in call_async
    message.append(signature=signature, *args)
TypeError: Don't know how which D-Bus type to use to encode type "set"
paul@Aragorn:~$

---

