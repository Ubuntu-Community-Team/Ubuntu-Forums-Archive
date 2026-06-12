---
title: "No Signal Detected"
date: 2011-11-24
forum: General Help
---

### Post by Richiegs on 2011-11-24
I am using Ubuntu 10.04, Sometimes after I chose Ubuntu during startup, the computer would indicate "No signal detected" and the light on my LCD would turn to yellow as if it is in sleep mode. The PC would not respond even after I press any key on the keyboard. Does anyone know what is the cause and know how to fix this problem? Thank you in advance

---

### Post by WasMeHere on 2011-11-24
I run Lucid on a desktop, so I might be able to help you comparing your symptoms with what happens here.

I think *No Signal Detected* is written by the monitor when the computer sends no signal.

- Does it happen very seldom or quite often? Will it be OK after reboot or is power-off necessary?

- When you say 'the PC would not respond even after I press any key' do you mean that you see nothing on the screen or that you hear nothing from the box (noise from the hard drive, beep or whatever)?

It might be a bad connection between the computer and the monitor. It might also be that Lucid is failing or simply shutting down (instead of starting).

---

### Post by sudodus on 2011-11-24
Could it be a failing disk? Is it new enough to have S.M.A.R.T. checking? Try with *palimpsest* alias 'System-Administration-Disk Tool'

---

### Post by Richiegs on 2011-11-24
> **Olle Wiklund said:**
> I run Lucid on a desktop, so I might be able to help you comparing your symptoms with what happens here.

I think *No Signal Detected* is written by the monitor when the computer sends no signal.

- Does it happen very seldom or quite often? - Sometimes
Will it be OK after reboot or is power-off necessary? - It is usually OK after reboot.

- When you say 'the PC would not respond even after I press any key' do you mean that you see nothing on the screen or that you hear nothing from the box (noise from the hard drive, beep or whatever)? - I see nothing on the screen.

It might be a bad connection between the computer and the monitor. It might also be that Lucid is failing or simply shutting down (instead of starting). - A bad connection is unlikely because I have had this new LCD for 3 months and it never happens when I choose to use Windows.

---

### Post by WasMeHere on 2011-11-24
Good, one possibility less. What about noise from the computer ,,, ?

---

### Post by Richiegs on 2011-11-24
> **sudodus said:**
> Could it be a failing disk? Is it new enough to have S.M.A.R.T. checking? Try with *palimpsest* alias 'System-Administration-Disk Tool'

I have no problem when I choose to use Windows.

---

### Post by Richiegs on 2011-11-24
> **Olle Wiklund said:**
> Good, one possibility less. What about noise from the computer ,,, ?

No Noise. It is like the computer goes into the sleep mode.

---

### Post by WasMeHere on 2011-11-24
> **Olle Wiklund said:**
> Good, one possibility less. What about noise from the computer ,,, ?
[s]I guess we have to wait until the next episode to find out about this question.[/s]

It is hard to solve problems that happen sometimes unless you can link it to something else. For example: Can you link it to updating the software or using some particular software or hardware?

---

### Post by Richiegs on 2011-11-24
> **sudodus said:**
> Could it be a failing disk? Is it new enough to have S.M.A.R.T. checking? Try with *palimpsest* alias 'System-Administration-Disk Tool'
I don't find palimpsest/System-Administration-Disk Tool.

---

### Post by dandnsmith on 2011-11-24
As Olle says, the message is usually when the monitor doesn't get a signal from the graphics card/chipset.
I assume that you're talking about having seen the grub menu and selecting Ubuntu - at that point I've never had that message (only when initially booting from cold, or during a restart).
That means that there has been output from the graphics card/chipset, but it has been switched off for some reason. I think that Ub10.04 runs without an xorg.conf by default - which makes that a little odd, unless you've hand-configured the xorg stuff for the old monitor.

I suggest looking to see if there is an xorg.conf (in /etc ?), and removing/renaming if so. If there wasn't one, then you could try reconfiguring the xorg display package to custom build one (I can never remember the command for doing that).

HTH

---

### Post by sudodus on 2011-11-24
```
palimpsest
``` from a terminal window, If you don't find it in the menu.

You can also test if the linux file system is good. ***Run a live session*** and mount ***no*** partitions, for example run from your installation CD or USB drive and from a terminal window, do
```
sudo e2fsck -f /dev/sd[COLOR=Red]xy[/COLOR]
``` where x should be changed to the letter of your system drive and y to the number of the partition, for example /dev/sd[COLOR=Red]a5[/COLOR]. Look for the device mounted to / in the output of ```
df
```

---

### Post by Richiegs on 2011-11-24
> **dandnsmith said:**
> As Olle says, the message is usually when the monitor doesn't get a signal from the graphics card/chipset.
I assume that you're talking about having seen the grub menu and selecting Ubuntu - at that point I've never had that message (only when initially booting from cold, or during a restart).
That means that there has been output from the graphics card/chipset, but it has been switched off for some reason. I think that Ub10.04 runs without an xorg.conf by default - which makes that a little odd, unless you've hand-configured the xorg stuff for the old monitor.

I suggest looking to see if there is an xorg.conf (in /etc ?), and removing/renaming if so. If there wasn't one, then you could try reconfiguring the xorg display package to custom build one (I can never remember the command for doing that).

HTH
There are 4 files inside the xorg.conf.d folder -05-evdev.conf, 10-synaptics.conf, 10-vmmouse.conf and 10-wacom.conf. Should I remove the entire folder?

---

### Post by dandnsmith on 2011-11-24
No - definitely not. It's only xorg.conf we're interested in, which is usually under /etc, but the man page for Xorg lists several places to be tried as possibles.

---

### Post by Richiegs on 2011-11-24
> **dandnsmith said:**
> No - definitely not. It's only xorg.conf we're interested in, which is usually under /etc, but the man page for Xorg lists several places to be tried as possibles.

There is no Xorg file in /etc.

---

### Post by Richiegs on 2011-11-24
There is a file called .xsession-errors. I don't know if it relates to the problem that I experienced.


/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /home/goodboy/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/none.
GNOME_KEYRING_CONTROL=/tmp/keyring-70oJvb
SSH_AUTH_SOCK=/tmp/keyring-70oJvb/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-70oJvb
SSH_AUTH_SOCK=/tmp/keyring-70oJvb/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-70oJvb
SSH_AUTH_SOCK=/tmp/keyring-70oJvb/ssh

(polkit-gnome-authentication-agent-1:1776): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1776): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:1761): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x97f9d00'
Unable to find a synaptics device.
Initializing nautilus-gdu extension
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
I/O warning : failed to load external entity "/home/goodboy/.compiz/session/10ef8f440dc1699324132218136480091400000017000026"
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
gnome-session[1700]: WARNING: Could not launch application 'evolution-alarm-notify.desktop': Unable to start application: Failed to execute child process "/usr/lib/evolution/2.28/evolution-alarm-notify" (No such file or directory)
** (update-notifier:1968): DEBUG: Skipping reboot required

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): Gdk-WARNING **: XID collision, trouble ahead

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(exe:2066): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by WasMeHere on 2011-11-26
There are complaints about graphics (do you use the built-in grahics driver or a proprietary one?) and complaints about a sambashare (is it on an external drive or another computer?)

I think it is hard-ware related since it only happens sometimes (but I am not sure). Could it be a hard drive that is starting slowly, and is not ready when it is supposed to be ready?

Is there a difference if you let the system wait at the grub menu or if you press Enter to get it started at once, or if you move the high-light with an arrow key and wait for a long time (say one minute) before pressing Enter to boot the selected OS?

Or maybe the harddrive has problems as suggested by sudodus?

---

### Post by Richiegs on 2011-12-03
[QUOTE=Olle Wiklund;11490135]There are complaints about graphics (do you use the built-in grahics driver or a proprietary one?)-Built-in graphic driver


I think it is hard-ware related since it only happens sometimes (but I am not sure). Could it be a hard drive that is starting slowly, and is not ready when it is supposed to be ready? - I don't think so because it never happens when I use Windows.

Is there a difference if you let the system wait at the grub menu or if you press Enter to get it started at once, or if you move the high-light with an arrow key and wait for a long time (say one minute) before pressing Enter to boot the selected OS? -
No, I think it was caused by Ubuntu Tweak. Did anyone experience similar thing like this?

---

### Post by WasMeHere on 2011-12-06
> **Richiegs said:**
> [QUOTE=Olle Wiklund;11490135]There are complaints about graphics (do you use the built-in grahics driver or a proprietary one?)
- Built-in graphic driver
>  I think it is hard-ware related since it only happens sometimes (but I am not sure). Could it be a hard drive that is starting slowly, and is not ready when it is supposed to be ready?
- I don't think so because it never happens when I use Windows.
> Is there a difference if you let the system wait at the grub menu or if you press Enter to get it started at once, or if you move the high-light with an arrow key and wait for a long time (say one minute) before pressing Enter to boot the selected OS?

No, I think it was caused by Ubuntu Tweak. Did anyone experience similar thing like this?[/QUOTE]

Well this is hard to solve. You think it was caused by Ubuntu Tweak. Please try to remember, if you have been tweaking Ubuntu (yourself), or if the problem started after a particular update (suggested by the system itself)!

Will it happen if you start a live session with Ubuntu from a CD or USB drive (repeating it several times)?

---

