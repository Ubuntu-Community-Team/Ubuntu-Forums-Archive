---
title: "WICD is being naughty lately."
date: 2010-05-24
forum: General Help
---

### Post by HotForLinux on 2010-05-24
A laptop with ubuntu hardy has been using the WICD (Wired and Wireless Network Connection Manager) program to view, select and connect to wireless networks; but lately, the moment the X session starts WICD promts asking for a password to access the network card. I don't know whose passwd (it doesn't say), what for and why... becuase the unit has already auto connected to the network (since boot time) with the wireless card. After giving to WICD an admin password or root's password, the deamon (WICD's deamon) doesn't start.

If I try to start it, it fails:

```

$ invoke-rc.d wicd start
 * Starting Network connection manager wicd                                                      [fail] 
```This is the output of dmesg, but all the lines, except for the last one were already written when the X environment started.



```
[   30.093811] eth1: no IPv6 routers present
[   30.154633] sky2 eth0: disabling interface
[   30.273020] apm: BIOS not found.
[   30.404157] sky2 eth0: enabling interface
[   30.408048] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   62.698752] Marking TSC unstable due to: cpufreq changes.
[   32.903813] [drm] Initialized drm 1.1.0 20060810
[   49.454544] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   49.454557] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   49.454649] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   48.402740] ACPI: EC: non-query interrupt received, switching to interrupt mode

```If I try to execute WICD client from the terminal. The same window saying "WICD needs a password to acces your netwok cards" and asking for a password appears.
The output in the terminal goes llike this:



```
$ wicd-client
Has notifications support True
rename failed
Loading...
Connecting to daemon...
Can't connect to the daemon, trying to start it automatically...
rename failed
Connected.
ERROR:dbus.proxies:Introspect error on :1.51:/org/wicd/daemon: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
warning: ignoring exception org.freedesktop.DBus.Error.ServiceUnknown: The name :1.51 was not provided by any .service files
warning: ignoring exception org.freedesktop.DBus.Error.ServiceUnknown: The name :1.51 was not provided by any .service files

```

Any ideas about what is going on?
I think that playing with gome's network configuration )network-admin) caused the problem. But how to solve it?


WICD's log:

```
2010/05/25 01:35:42 :: ---------------------------
2010/05/25 01:35:42 :: wicd initializing...
2010/05/25 01:35:42 :: ---------------------------
2010/05/25 01:35:42 :: wicd is version 1.6.2.2 463
2010/05/25 01:35:42 :: Traceback (most recent call last):
2010/05/25 01:35:42 ::   File "/usr/share/wicd/wicd-daemon.py", line 1750, in <module>
2010/05/25 01:35:42 ::     main(sys.argv)
2010/05/25 01:35:42 ::   File "/usr/share/wicd/wicd-daemon.py", line 1714, in main
2010/05/25 01:35:42 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/05/25 01:35:42 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/05/25 01:35:42 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/05/25 01:35:42 ::   File "/usr/share/wicd/wicd-daemon.py", line 1330, in __init__
2010/05/25 01:35:42 ::     debug=debug)
2010/05/25 01:35:42 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/05/25 01:35:42 ::     self.read(path)
2010/05/25 01:35:42 ::   File "/usr/lib/python2.5/ConfigParser.py", line 267, in read
2010/05/25 01:35:42 ::     self._read(fp, filename)
2010/05/25 01:35:42 ::   File "/usr/lib/python2.5/ConfigParser.py", line 490, in _read
2010/05/25 01:35:42 ::     raise e
2010/05/25 01:35:42 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/05/25 01:35:42 ::     [line  4]: '[]\n'

```the contents of the file "/etc/wicd/wired-settings.conf"  is:
```
[DEFAULT]
lastused = True

[]

```

---

### Post by HotForLinux on 2010-05-24
OK.

I just deleted that sh** at the end of the "/etc/wicd/wired-settings.conf"  file 
     
     > [DEFAULT]
lastused = True
[COLOR=Red]
**[]**[/COLOR] 

and now the demon started ok; then the cllient started ok with its tray icon and all. So I think it is solved.

---

### Post by TyeS on 2012-01-02
I am very new to Ubuntu and I haven't had problems with my internet connection via wireless until I plugged my friend's wired internet into the computer. I was connected for a while and then when I rebooted the computer I was asked to type in a password which has never been needed to start the computer. When I went to open the wicd network it asked for a password also/ sometimes now it will just show the icon in the dock as if it's opening then disappear.


the message I get is: [COLOR="Red"]Could not connect to wicd's D-Bus interface. Check the wicd log for error messages.[/COLOR]

I looked up how to check the wicd log but when I got to the [COLOR="red"]var/log/wicd[/COLOR] the folder icon had an "x" on it and the folder is empty.

I also read a forum where they said to check the [COLOR="red"]etc/init.d/wicd[/COLOR]

and the forum had the proper scripts to replace it with. However when I tried to put the correct scripts in I got this message:

[COLOR="red"]Could not save the file /etc/init.d/wicd. You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.[/COLOR]

I also tried going to the [COLOR="red"]"/etc/wicd/wired-settings.conf"[/COLOR] but when I do the [COLOR="red"]manager-settings.conf[/COLOR] has an "x", [COLOR="red"]wired-settings.conf [/COLOR]has an "x" and the [COLOR="red"]wireless-settings.conf[/COLOR] has an "x" on them and cannot be opened. 

Does anyone know how to fix this problem? I am extremely new to Ubuntu and very confused.

Thanks.

---

