---
title: "PC now starts with server login instead of Unity desktop"
date: 2012-10-08
forum: General Help
---

### Post by clay7 on 2012-10-08
I recently made a few changes to my PC (Ubuntu 12.04 LTS Desktop):

[LIST]
[*]Update and upgrade
[*]Installed openssh-server so I could check on the computer remotely
[*]Installed fail2ban
[/LIST]

Now when I start the computer, I get the server login screen instead of the Unity desktop. If I run **startx** it just locks up the computer.

How can I get the desktop to show up again?

---

### Post by daslinkard on 2012-10-08
What happens when you do the following...
1. log out of your session
2. log back in and select the icon next to your user name.
3. Select unity
4. Log in

This should log you back into Unity.  Try to reboot and see if it remains as your default log in (Unity that is).

---

### Post by clay7 on 2012-10-08
If I log out and log back in, I'm in the same situation.

When my computer turns on, it shows the purple Ubuntu screen and then goes straight to the server-style logon (black screen, white text only, no graphics).

---

### Post by daslinkard on 2012-10-08
So there is no icon next to your username at log in for you to change the theme you are logging into?

---

### Post by clay7 on 2012-10-08
Thanks - no, there are no graphics at all. It looks exactly like the Ubuntu server login screen.

I've tried editing the GRUB file with "nomodeset" instead of "quiet splash" but that didn't work.

My guess is that this is related to the ATI drivers of the graphics card. Google shows several other instances of this problem. Unfortunately, so far I haven't found the solution...

---

### Post by daslinkard on 2012-10-08
What about trying

```
sudo apt-get install gnome
```

Then once this is completed....reboot your system and try the log in again.

---

### Post by clay7 on 2012-10-09
I did

```
sudo apt-get install gnome-panel
```

and rebooted, and it still went back to the server login screen. I tried "startx" and it again locked up the system.

---

### Post by HiImTye on 2012-10-09
try ctrl+alt+f7 to switch to tty7 (if it doesn't say tty7). if that doesn't produce your login screen then I'd check your syslog and kern.log to see what errors it's giving you
```
less /var/log/syslog
less /var/log/kern.log
```

edit: I'd also check to see if you have a login manager running
```
ps -e | grep dm$
```
it should list either lightdm or gdm if you have one up

---

### Post by clay7 on 2012-10-09
```
ps -e | grep dm$
```
returned nothing. Also, tried ctrl+alt+f7 but this just froze the computer.

**/var/log/kern.log** showed some interesting things:

```
fb0: VESA VGA frame buffer device
init: gdm main process (963) killed by TERM signal
fglrx_pci 0000:03:00:0: irq 42 for MSI/MSI-X
[fglrx] Firegl kernel thread PID: 1076
[fglrx] Firegl kernel thread PID: 1077
[fglrx] Firegl kernel thread PID: 1078
[fglrx]IRQ 42 Enabled
[fglrx] Gart USWC size:628 M.
[fglrx] Gart cacheable size:247 M.
[fglrx] Reserved FB block: Shared offset:0, size:1000000
[fglrx] Reserved FB block: Unshared offset:fb07000, size:1f9000
[fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000
[fglrx] IRQ 42 Disabled
init: lightdm main process (964) terminated with status 1
ip_tables: (C) 2000-2006 Netfilter Core Team
init: plymouth-stop pre-start process (1140) terminated with status 1
{some lan settings}
init: failsafe-x main process (1088) terminated with status 1
```

I have both lightdm and gdm installed but it looks like neither is running. I've tried 
```
sudo apt-get -f install
```
and that did nothing either.

Any thoughts?

---

### Post by HiImTye on 2012-10-09
you have both installed simultaneously? I'd try these

```
sudo /etc/init.d/lightdm stop
sudo /etc/init.d/gdm stop
sudo /etc/init.d/lightdm start
```
if that fails then
```
sudo less /var/log/lightdm/lightdm.log
```

---

### Post by clay7 on 2012-10-10
I've stopped each service and tried to start (and restart) only one, but the computer froze each time.

I'll be able to check the lightdm.log when I get home later. Thank you for your help!

---

### Post by Monotoko on 2012-10-10
It sounds like a graphics card issue to me... have you tried plugging your screen into the mainboard rather than the graphics card?

---

### Post by clay7 on 2012-10-10
I tried powering off, switching the monitor cord to the motherboard VGA out, but this did not show anything at all. 

I've removed gdm to avoid any confusion on my part (or the system's). Then I rebooted, and here are the contents of all logs in the **/var/log/lightdm** directory. I agree that this looks like a video card problem but I don't know how to correct this. It's even more confusing since it worked fine for a few weeks, and then after my seemingly innocent changes, I have these problems. Thanks again to all for your help.

**/var/log/lightdm/x-0.log**
```

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
Current Operating System: Linux clay-MS-7223 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=69f865d5-2757-4182-9673-05991ef73e56 ro splash vt.handoff=7
Build Date: 29 August 2012  12:10:05AM
xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 10 21:05:33 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@3:0:1) found
/usr/bin/X: symbol lookup error: /usr/lib/xorg/modules/drivers/fglrx_drv.so: undefined symbol: GlxInitVisuals2D

```

**/var/log/lightdm/lightdm.log**
```

[+0.01s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.01s] DEBUG: Starting Light Display Manager 1.2.1, UID=0 PID=894
[+0.01s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.01s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registered seat module xlocal
[+0.01s] DEBUG: Registered seat module xremote
[+0.01s] DEBUG: Adding default seat
[+0.01s] DEBUG: Starting seat
[+0.01s] DEBUG: Starting new display for greeter
[+0.01s] DEBUG: Starting local X display
[+0.02s] DEBUG: X server :0 will replace Plymouth
[+0.04s] DEBUG: Using VT 7
[+0.04s] DEBUG: Activating VT 7
[+0.04s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.04s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.04s] DEBUG: Launching X Server
[+0.04s] DEBUG: Launching process 971: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.04s] DEBUG: Waiting for ready signal from X server :0
[+0.04s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.05s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+4.21s] DEBUG: Process 971 exited with return value 127
[+4.21s] DEBUG: X server stopped
[+4.21s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+4.21s] DEBUG: Releasing VT 7
[+4.21s] DEBUG: Stopping Plymouth, X server failed to start
[+4.29s] DEBUG: Display server stopped
[+4.29s] DEBUG: Stopping display
[+4.29s] DEBUG: Display stopped
[+4.29s] DEBUG: Stopping X local seat, failed to start a display
[+4.29s] DEBUG: Stopping seat
[+4.29s] DEBUG: Seat stopped
[+4.29s] DEBUG: Required seat has stopped
[+4.29s] DEBUG: Stopping display manager
[+4.30s] DEBUG: Display manager stopped
[+4.30s] DEBUG: Stopping daemon
[+4.30s] DEBUG: Exiting with return value 1

```


**/var/log/lightdm/x-0-greeter.log**
```

Activating service name='org.a11y.atspi.Registry'
[+0.00s] DEBUG: unity-greeter.vala:816: Starting unity-greeter 0.2.8 UID=104 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:819: Setting cursor
Successfully activated service 'org.a11y.atspi.Registry'

** (at-spi2-registryd:1207): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (at-spi2-registryd:1207): WARNING **: Unable to register client with session manager
[+0.02s] DEBUG: unity-greeter.vala:823: Creating background surface
[+0.02s] DEBUG: unity-greeter.vala:826: Loading command line options
[+0.02s] DEBUG: unity-greeter.vala:854: Setting GTK+ settings
[+0.10s] DEBUG: unity-greeter.vala:877: Creating Unity Greeter
[+0.10s] DEBUG: Connecting to display manager...
[+0.10s] DEBUG: Wrote 17 bytes to daemon
[+0.10s] DEBUG: Read 8 bytes from daemon
[+0.10s] DEBUG: Read 120 bytes from daemon
[+0.10s] DEBUG: Connected version=1.2.1 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true
[+0.28s] DEBUG: menubar.vala:318: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.37s] CRITICAL: g_error_free: assertion `error != NULL' failed
[+0.37s] DEBUG: get entries
[+0.37s] DEBUG: menubar.vala:511: Adding indicator object 0x8f1d9c4 at position 0
[+0.38s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.38s] DEBUG: Checking against 2 possible times
[+0.40s] DEBUG: Guessing max time width: 62
[+0.40s] DEBUG: get entries
[+0.40s] DEBUG: menubar.vala:511: Adding indicator object 0x8f7901c at position 1
[+0.41s] WARNING: IndicatorObject class does not have an accessible description.
[+0.42s] WARNING: IndicatorObject class does not have an accessible description.
[+0.42s] DEBUG: get entries
[+0.42s] DEBUG: get entries
[+0.42s] DEBUG: menubar.vala:511: Adding indicator object 0x8e9652c at position 2
[+0.42s] DEBUG: menubar.vala:335: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.44s] DEBUG: Loaded session /usr/share/xsessions/ubuntu-2d.desktop (Ubuntu 2D, This session logs you into Ubuntu 2D Mode)
[+0.44s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+0.44s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.48s] DEBUG: Ignoring session /usr/share/xsessions/gnome-shell.desktop
[+0.48s] DEBUG: session-chooser.vala:42: Adding session ubuntu (Ubuntu)
[+0.49s] DEBUG: session-chooser.vala:42: Adding session ubuntu-2d (Ubuntu 2D)
[+0.89s] DEBUG: Setting keyboard layout to 'us'
[+0.95s] DEBUG: main-window.vala:98: Screen is 1600x900 pixels
[+0.95s] DEBUG: main-window.vala:104: Monitor 0 is 1600x900 pixels at 0,0
[+0.96s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.96s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+1.01s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+1.01s] DEBUG: unity-greeter.vala:327: Adding/updating user clay (clay)
[+1.01s] DEBUG: unity-greeter.vala:184: Adding guest account entry
[+1.13s] DEBUG: Starting authentication for user clay...
[+1.13s] DEBUG: Wrote 20 bytes to daemon
[+1.13s] DEBUG: unity-greeter.vala:880: Showing greeter
[+1.13s] DEBUG: unity-greeter.vala:352: Showing main window
[+1.14s] DEBUG: New style for time label
[+1.14s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+1.14s] DEBUG: Checking against 2 possible times
[+1.14s] DEBUG: Guessing max time width: 62
[+1.16s] DEBUG: background.vala:315: Regenerating backgrounds
[+1.16s] DEBUG: background.vala:67: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1600x900
[+1.16s] DEBUG: New style for time label
[+1.16s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+1.16s] DEBUG: Checking against 2 possible times
[+1.17s] DEBUG: Guessing max time width: 62
[+1.18s] DEBUG: unity-greeter.vala:893: Starting main loop
[+1.19s] DEBUG: Read 8 bytes from daemon
[+1.19s] DEBUG: Read 34 bytes from daemon
[+1.19s] DEBUG: Prompt user with 1 message(s)
[+1.65s] DEBUG: Setting keyboard layout to 'us'
[+1.73s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu
[+1.73s] DEBUG: notify visible signal received
[+1.73s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+1.77s] DEBUG: Num devices: '0'

[+1.77s] MESSAGE: Couldn't find primary device
[+1.77s] DEBUG: Num devices: '0'

[+1.77s] DEBUG: icon_policy is: 0 (present==0, charge==1, never==2)
[+1.77s] DEBUG: count_batteries found 0 batteries (0 are charging/discharging)
[+1.77s] DEBUG: should_be_visible: no
[+1.77s] DEBUG: menubar.vala:519: Removing indicator object 0x8e964d4
[+1.77s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.77s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.77s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.77s] WARNING: menubar.vala:531: Indicator object 0x8e964d4 not in menubar
[+1.77s] DEBUG: New calendar item
[+1.81s] DEBUG: unity-greeter.vala:310: starting system-ready sound
[+2.27s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+2.35s] DEBUG: indicator-sound: new_volume_slider_widget
[+2.36s] DEBUG: indicator-sound: new_voip_slider_widget
[+10.72s] DEBUG: Providing response to display manager
[+10.72s] DEBUG: Wrote 24 bytes to daemon
[+10.86s] DEBUG: Read 8 bytes from daemon
[+10.86s] DEBUG: Read 16 bytes from daemon
[+10.86s] DEBUG: Authentication complete for user clay with return code 0
[+10.86s] DEBUG: Starting session ubuntu
[+10.86s] DEBUG: Wrote 18 bytes to daemon

```

---

