---
title: "Logging in takes me right back to the login screen"
date: 2010-04-20
forum: General Help
---

### Post by Redsandro on 2010-04-20
Hi,

All of the sudden, I cannot log into my mc account anymore, which I use on a daily basis for watching television. (Ubuntu 9.10)

The mc account has no root privileges and I didn't do anything out of the ordinary.

My other (sudoer) account has no problem. Through that account, I can see **/home/mc/.xsession-errors**:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-2pVAhF/socket
SSH_AUTH_SOCK=/tmp/keyring-2pVAhF/socket.ssh

(gnome-settings-daemon:4423): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:4423): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: Failed to read saved session file /home/mc/.config/metacity/sessions/10f74b5290b046c812127178928619199300000043440026.ms: Failed to open file '/home/mc/.config/metacity/sessions/10f74b5290b046c812127178928619199300000043440026.ms': No such file or directory
Unable to find a synaptics device.
Cannot open display: 
Run 'bluetooth-applet --help' to see a full list of available command line options.

(polkit-gnome-authentication-agent-1:4470): Gtk-WARNING **: cannot open display: :1.0

(xdg-user-dirs-gtk-update:4480): Gtk-WARNING **: cannot open display: :1.0
Option parsing failed: Cannot open display: 
Cannot open display: 
Run 'vino-server --help' to see a full list of available command line options

** (gnome-volume-control-applet:4483): WARNING **: Cannot open display: 
Failed to init the UI: Cannot open display: 

** (gnome-screensaver:4468): WARNING **: Cannot open display: 

(nm-applet:4474): Gtk-WARNING **: cannot open display: :1.0

(gnome-power-manager:4469): Gtk-WARNING **: cannot open display: :1.0

GduNotification-ERROR **: Cannot open display: 
aborting...
gnome-session: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
Window manager warning: Fatal IO error 104 (Connection reset by peer) on display ':1.0'.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1.0"
      after 14 requests (11 known processed) with 0 events remaining.
gnome-settings-daemon: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
nautilus: Fatal IO error 104 (Connection reset by peer) on X server :1.0.

** (gnome-panel:4452): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_Panel_TrashApplet:
System exception: IDL:omg.org/CORBA/COMM_FAILURE:1.0
gnome-panel: ../../src/xcb_io.c:378: _XAllocID: Assertion `ret != inval_id' failed.
fixme:heap:HeapSetInformation 0x110000 0 0x47ae3c 4
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:ole:apartment_createwindowifneeded CreateWindow failed with error 1114
fixme:heap:HeapSetInformation 0x5d0000 0 0x47ae3c 4

(evolution-alarm-notify:4472): Gtk-WARNING **: cannot open display: :1.0
```

I am not sure if this is any help, because the user I am currently logged on with also has a neat list of xsession errors yet here I am typing in Gnome.

Xsession-errors on current user (that has no problems) for comparison
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-4gSBsD/socket
SSH_AUTH_SOCK=/tmp/keyring-4gSBsD/socket.ssh

(gnome-settings-daemon:3986): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3986): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Unable to find a synaptics device.
Window manager warning: Failed to read saved session file /home/sander/.config/metacity/sessions/10828dfc6db4a02767127178890397568400000039090025.ms: Failed to open file '/home/sander/.config/metacity/sessions/10828dfc6db4a02767127178890397568400000039090025.ms': No such file or directory

(nautilus:4019): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(polkit-gnome-authentication-agent-1:4036): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:4036): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3
Starting Dropbox...** (gnome-panel:4018): DEBUG: Adding applet 0.
** (gnome-panel:4018): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:4018): DEBUG: Adding applet 1.
** (gnome-panel:4018): DEBUG: Adding applet 2.
** (gnome-panel:4018): DEBUG: Adding applet 3.
** (gnome-panel:4018): DEBUG: Adding applet 4.
** (gnome-panel:4018): DEBUG: Adding applet 5.
** (gnome-panel:4018): DEBUG: Adding applet 6.
** (gnome-panel:4018): DEBUG: Adding applet 7.

** (nautilus:4019): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4019): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4019): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-dropbox 0.6.1
20/04/2010 08:41:51 PM Autoprobing TCP port in (all) network interface
20/04/2010 08:41:51 PM Listening IPv{4,6}://*:5900
20/04/2010 08:41:51 PM Autoprobing selected port 5900
20/04/2010 08:41:51 PM Advertising security type: 'TLS' (18)
20/04/2010 08:41:51 PM Advertising authentication type: 'VNC Authentication' (2)
20/04/2010 08:41:51 PM Advertising security type: 'VNC Authentication' (2)
Initializing nautilus-image-converter extension
Initializing nautilus-gdu extension
Done!
** (gnome-panel:4018): DEBUG: Adding applet 8.
** (gnome-panel:4018): DEBUG: Adding applet 9.
** (gnome-panel:4018): DEBUG: Adding applet 10.
** (gnome-panel:4018): DEBUG: Adding applet 11.
evolution-alarm-notify-Message: Setting timeout for 19064 1271808000 1271788936
evolution-alarm-notify-Message:  Wed Apr 21 02:00:00 2010

evolution-alarm-notify-Message:  Tue Apr 20 20:42:16 2010


(gnome-screensaver:4066): Gdk-CRITICAL **: gdk_drawable_get_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed

(gnome-screensaver:4066): Gdk-CRITICAL **: gdk_colormap_alloc_colors: assertion `GDK_IS_COLORMAP (colormap)' failed

(gnome-screensaver:4066): Gdk-CRITICAL **: gdk_drawable_get_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed

(gnome-screensaver:4066): Gdk-CRITICAL **: gdk_window_set_background: assertion `GDK_IS_WINDOW (window)' failed

(gnome-screensaver:4066): Gdk-CRITICAL **: gdk_window_clear: assertion `GDK_IS_WINDOW (window)' failed

(gnome-screensaver:4066): Gdk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window

(gnome-screensaver:4066): Gdk-CRITICAL **: gdk_drawable_get_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed

(gnome-screensaver:4066): Gdk-CRITICAL **: gdk_colormap_alloc_colors: assertion `GDK_IS_COLORMAP (colormap)' failed

(gnome-screensaver:4066): Gdk-CRITICAL **: gdk_drawable_get_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed

(gnome-screensaver:4066): Gdk-CRITICAL **: gdk_window_set_background: assertion `GDK_IS_WINDOW (window)' failed

(gnome-screensaver:4066): Gdk-CRITICAL **: gdk_window_clear: assertion `GDK_IS_WINDOW (window)' failed

(gnome-screensaver:4066): Gdk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x189 specified for 0x4200003 (Password).

(nautilus:4721): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
```

I have no idea what the problem is. Every disk has at least 10% free. Can someone point me to the problem or other files that show me where to look?

---

### Post by gzarkadas on 2010-04-20
Maybe is that you did set a password expiry date for your user account and that time has elapsed? what is the output of `chage --list <login>'? (put in <login> the login name of the account that has trouble).

---

### Post by Redsandro on 2010-04-20
Yeah I just had some fun with that because I thought you said **chase** :P but now that I finally got it, it's not the password.

```
$ sudo chage —list mc
Last password change : Dec 30, 2009
Password expires : never
Password inactive : never
Account expires : never
Minimum number of days between password change : 0
Maximum number of days between password change : 99999
Number of days of warning before password expires : 7
```

---

### Post by gzarkadas on 2010-04-20
Ok, I 'm not an X specialist and I don't know how much I will be able to help, but I'll give it a try. Maybe in the process someone more knowledgable can give a hand of assistance :).

Your logs imply that the main reason for your mc account to not succeed in login, is the inability to open an X display. This can be as simple as a deleted or altered /home/mc/.Xauthority file or something more complex. Some googling comes up with mainly remote X logins having that kind of error. How do you login to X? locally or remotely? (if you use another account to watch tv because you must access some remote box this could imply a remote X login).

---

### Post by Redsandro on 2010-04-20
Sounds like it could make sense. However, I log in locally.
Only thing I use is Synergy+ to share keyboard and mouse from the computer right next to it. But it's the same for the other account and that one is fine.

I'm gonna touch forcefsck on all drives since I don't have any other ideas at the moment. Maybe disconnect all internal hardware afterwards? I didn't add anything new but I had crazy problems with an ethernet card before. Not like this, but still. Lack of ideas. :)

---

### Post by gzarkadas on 2010-04-21
It may be synergy that's giving the issues, because if I read well the logs it is the second display that X can't open (that is the remote one) or perhaps your network setup. 

For example I found this with a little googling: [https://bugs.launchpad.net/ubuntu/+source/synergy/+bug/385529](https://bugs.launchpad.net/ubuntu/+source/synergy/+bug/385529)

Do you use ssh tunneling to communicate with the other machine? if yes, are ssh settings ok? 

Does the mc account has the right to communicate through networks? I remember after a kernel upgrade those rights to be added and by default be non-set for non-admin users; check the rights of the account from the `System|Users and Groups' app.

In addition, does any other of your logs (syslog particularly) shows something failing when trying to login?

---

### Post by Redsandro on 2010-04-21
Yes I do use the Synergy+ fork, which is updated in 2009. It does not create a remote X though. It is a com in your active local logon to share keyboard and mouse control.

**!!!**

I *just* rebooted my machine in order to check out the syslog. Last thing I did, yesterday, was force a fscheck and disconnect any USB devices. (I was gonna disconnect everything.) And now it just does that auto-login into the MC account! Whaat?

I really really appreciate your help. I don't understand what happened. But ehh.. it works again? I thought filesystem check cleaned up the mess, not repair corrupted data? I didn't even think I had any?

And the USB stuff, I hardly think a mouse/mic/hub prevents a login. I can logout and login fine now that everything is attached again.

So yeah, apart from my :confused: annoyance, I'm happy it works again.

Sorry for the disappointing end of this story!

---

### Post by gzarkadas on 2010-04-21
Well, it's not dissapointing; things finally work :) 

Regarding the ultimate cause of this: it may be that the specific blend of your devices caused some of them not being detected correctly during bootup; if you want to post-investigate it, you can browse your logs for the boot process messages before and after the fixup to come up with a clue.

Enjoy your working-again system!:guitar::guitar::guitar:

---

### Post by Redsandro on 2010-04-21
Yeah!

Looks like I've got many many megabytes of syslog just from the last few days. It's been flooded with Synergy+ messages that say failed to connect, but the cause is simply a change of server IP which I didn't fix yet, and s+ polls every 2 seconds with an error message.

Is there a way to block certain apps (synergy+) from writing in syslog? If this ever happens again I will immediately make a copy of the logfiles, preferably without all the bogus s+ messages.

---

### Post by gzarkadas on 2010-04-21
I don't know; /etc/syslog.conf provide a way to customize logging by facility (see `man syslog' and `man syslog.conf') but not by specific app - unless I overlooked something. Maybe the specific application's configuration files provide an option for the verbosity of logging.

But you needn't be worried; log rotation will take care of not filling up your logs (AFAIK it is enabled by default).

---

### Post by Redsandro on 2010-04-22
Oh no it did it again! I unplugged everything USB related and rebooted, still no ball!

Synergy was connected so no bogus messages this time. This is the syslog from boot to idle, I retried 10 minutes later, that's how I know this is everything from boot to auto-login to fail to login screen again.

On first glance I don't see what could be the culprit, but it's a lot of information.

Here is the syslog:
[[SIZE="3"]http://pastebin.com/5fU5XWgm[/SIZE]]("http://pastebin.com/5fU5XWgm")

Can anyone take a look?

---

### Post by gzarkadas on 2010-04-23
I can't connect to the URL you showed; why not attach a bzip2'ed copy of your syslog here? (with the current forum limit, you could fit several MB if compressed).

---

### Post by Redsandro on 2010-04-23
You can't? That's strange. It works here. Are you in China, Australia or England?

[http://pastebin.com/download.php?i=5fU5XWgm](http://pastebin.com/download.php?i=5fU5XWgm) for the textfile.

I don't have the log anymore because I need to login to my other account for my work so it's probably a lot of megabytes away, but I can upload the file from pastebin here.

With synergy away and only one boot logged, the file is only maybe 80 kilobytes but that's also too much to write in a forum post. :)

(see attachment)

---

### Post by gzarkadas on 2010-04-23
Got it from the download link. I spotted those lines:

> 
Apr 22 18:41:03 RedServ kernel: [   34.748144]    groups: 0-1 (__cpu_power = 2048 ) 
[COLOR=Red]Apr 22 18:41:10 RedServ gnome-session[1872]: WARNING: Could not launch application 'xbmc.desktop': **Unable to start application: Failed to execute child process "wait" (No such file or directory) **
[/COLOR]Apr 22 18:41:11 RedServ Synergy+ 1.3.4: 2010-04-22T18:41:11 FATAL: X display has unexpectedly disconnected#012#011/home/nick/Projects/synergy-plus/lib/platform/CXWindowsScreen.cpp,1631 
My guess: the application pointed out by xbmc.desktop (I assume the xbmc player) is either missing itself or misses some necessary files (or if it is a remote link there is some network problem - note the 7 seconds delay from the previous message); this causes the X display to disconnect and throw you back to login. You will have to find what is missing (or what is the network problem - is port 24800 blocked?) or just re-install the whole thing.

---

### Post by Redsandro on 2010-04-23
Oh yeah, that entry. Thanks for looking into it. That is not the problem. It's a left-over from a long time ago, and apart from the notice in syslog, it is not a problem.

I had the mc account autostart xbmc, but it would minimize if it was loaded too soon, so I tried starting it by the following bash command:

```
wait 10; xbmc
```

However, such code does not work in autostart entries, so it writes an error to syslog about this wait command and doesn't run the rest.

The weird thing is: Those autostarted apps launch when the desktop is shown. But I never even see the desktop. Just that Ubuntu progress bar, screen black, progress bar again and the login screen.

Something extremely annoying: I accidentally logged in to that account today, and it worked. I was like: WHOA! See if it works after a reboot and then it didn't again. :(

BTW as a sidenote: Pastebin now doesn't work here either: It sais cannot connect to MySQL. :P

Just for the heck of it, I can remove that startup entry through the root account.


Synergy is also not honest about my problem. It connects, then it loses X (post login is somehow a new X) and post-login scripts kill Synergy just to launch it again for the new X, you can see it connect again later.

That said, it appears there's no clear event logged that makes mc logout again. I will have to look elsewhere, I think.

---

### Post by Redsandro on 2010-04-23
Hmm, this is interesting maybe. If I compare .xsession-errors from the failing account with the working account and I remove the part at the start that is identical (thus not the problem), I am left with this:

```
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"

      after 14 requests (11 known processed) with 0 events remaining.

Option parsing failed: Cannot open display: 

** (gnome-screensaver:3100): WARNING **: Cannot open display: 

(gnome-power-manager:3101): Gtk-WARNING **: cannot open display: :0.0

(xdg-user-dirs-gtk-update:3110): Gtk-WARNING **: cannot open display: :0.0

** (gnome-volume-control-applet:3111): WARNING **: Cannot open display: 
Cannot open display: 
Run 'vino-server --help' to see a full list of available command line options

GduNotification-ERROR **: Cannot open display: 
aborting...
Failed to init the UI: Cannot open display: 
Cannot open display: 
Run 'bluetooth-applet --help' to see a full list of available command line options.

(polkit-gnome-authentication-agent-1:3102): Gtk-WARNING **: cannot open display: :0.0

(nm-applet:3106): Gtk-WARNING **: cannot open display: :0.0
gnome-settings-daemon: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-session: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
Window manager warning: Fatal IO error 104 (Connection reset by peer) on display ':0.0'.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

** (gnome-panel:3080): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_ShowDesktopApplet:
System exception: IDL:omg.org/CORBA/COMM_FAILURE:1.0
nautilus: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-panel: ../../src/xcb_io.c:378: _XAllocID: Assertion `ret != inval_id' failed.
No protocol specified
fixme:heap:HeapSetInformation 0x110000 0 0x47ae3c 4
No protocol specified
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:ole:apartment_createwindowifneeded CreateWindow failed with error 1114
fixme:heap:HeapSetInformation 0x5d0000 0 0x47ae3c 4
No protocol specified

(evolution-alarm-notify:3104): Gtk-WARNING **: cannot open display: :0.0
```

Too bad it does not at all point to the cause of the fatal IO error.

---

### Post by Redsandro on 2010-04-23
Whhaaat? I removed another autostart entry that does executes **xrandr** to lower the screen resolution. And now I log in fine again.

I've learned that I need to wait a day and see if it sticks, but if that's the case, I am stunned.

I've always had xrandr as autostart app, for years in my other machine Xubuntu that was my media center before I used this one.

Ubuntu is a true puzzlebox.

---

### Post by gzarkadas on 2010-04-24
Maybe there has been an update to the driver for your graphics card and the lower mode that you set with xrandr does not work any more.  

Or just that your previous xorg.conf clashes somehow with the (updated I assume) version of xrandr (check [this link]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")).

This [link]("http://www.phoronix.com/scan.php?page=article&item=927&num=1") may also be helpful if you intend to play with xrandr to find an appropriate lower resolution mode.

Also, does your **auth** log shows any suspicious entry, such as a login that fails?

---

### Post by Redsandro on 2010-04-24
Here's the auth log from April 22nd, you can see the first autologin attempt at 18:40 - 18:41 that corresponds with the above syslog. Nothing out of the ordinary though.

```
Apr 22 18:40:54 RedServ sshd[1593]: Server listening on 0.0.0.0 port 22.
Apr 22 18:40:54 RedServ sshd[1593]: Server listening on :: port 22.
Apr 22 18:40:55 RedServ gdm-session-worker[1726]: pam_unix(gdm-autologin:session): session opened for user mc by (uid=0)
Apr 22 18:40:55 RedServ gdm-session-worker[1726]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Apr 22 18:41:06 RedServ seahorse-daemon[2338]: init gpgme version 1.1.8
Apr 22 18:51:22 RedServ gdm-session-worker[2763]: pam_unix(gdm:session): session opened for user mc by (uid=0)
Apr 22 18:51:22 RedServ gdm-session-worker[2763]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 22 18:51:24 RedServ seahorse-daemon[3373]: init gpgme version 1.1.8
Apr 22 18:51:26 RedServ getty[2747]: tty1: read: Inappropriate ioctl for device
Apr 22 18:53:13 RedServ sshd[1597]: Server listening on 0.0.0.0 port 22.
Apr 22 18:53:13 RedServ sshd[1597]: Server listening on :: port 22.
Apr 22 18:53:16 RedServ gdm-session-worker[1724]: pam_unix(gdm-autologin:session): session opened for user mc by (uid=0)
Apr 22 18:53:16 RedServ gdm-session-worker[1724]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Apr 22 18:53:28 RedServ seahorse-daemon[2374]: init gpgme version 1.1.8
Apr 22 18:54:00 RedServ gdm-session-worker[2789]: pam_unix(gdm:session): session opened for user mc by (uid=0)
Apr 22 18:54:00 RedServ gdm-session-worker[2789]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 22 18:54:03 RedServ seahorse-daemon[2931]: init gpgme version 1.1.8
Apr 22 18:54:06 RedServ getty[2729]: tty1: read: Inappropriate ioctl for device
Apr 22 18:54:37 RedServ gdm-session-worker[3089]: pam_unix(gdm:session): session opened for user sander by (uid=0)
Apr 22 18:54:38 RedServ gdm-session-worker[3089]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 22 18:54:40 RedServ seahorse-daemon[3217]: init gpgme version 1.1.8
Apr 22 18:58:26 RedServ sudo:     root : TTY=unknown ; PWD=/ ; USER=sander ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Apr 22 18:58:26 RedServ sudo:     root : TTY=unknown ; PWD=/ ; USER=sander ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Apr 22 18:58:26 RedServ sudo:     root : TTY=unknown ; PWD=/ ; USER=sander ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
```

---

### Post by gzarkadas on 2010-04-26
I see the error 'Inappropriate ioctl for device' in your mc user log sequences (which the sander user does not have). May be is this the cause of the erratic behaviour?

I googled this link, which states that a tty requiring command when a script is not connected to a tty may cause this script to fail (your autologin script in your case): 
[http://www.unix.com/shell-programming-scripting/20812-inappropriate-ioctl-device.html](http://www.unix.com/shell-programming-scripting/20812-inappropriate-ioctl-device.html)

---

### Post by Redsandro on 2010-04-26
Good catch!

The problem remains shrouded in confusion though. Since I removed the **xrandr -s**, there are no problems. And that command doesn't require tty. When I reintroduce it, the problem occurs *sometimes*.

So I have my workaround, it's just that I'm usually not satisfied unless I pinpoint the exact reason. But I don't see that happen because of the random nature and meager logs.

In a few weeks I will probably throw a clean Ubuntu 10.04 in the mix anyway which will replace my current problems with brand new and exciting ones. ;)

Thanks for looking into it.

---

