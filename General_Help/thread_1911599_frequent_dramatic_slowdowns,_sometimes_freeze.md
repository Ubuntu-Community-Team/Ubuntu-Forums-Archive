---
title: "frequent dramatic slowdowns, sometimes freeze"
date: 2012-01-19
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-01-19
I'm having very frequent (maybe 4 or 5 times an hour) dramatic slowdowns that last typically a minute or so, sometimes 5 minutes or more. Not all applications are affected equally. Typically nautilus or firefox will freeze meaning there is no change in what they show, even the little whirly dodads on an opening firefox tab quit whirling. Many windows will be featureless grey below the title bar. Sometimes the taskbar is affected, sometimes not. Usually I can still steer the pointer around the screen with the trackball, but not always.  Often, although still steerable the pointer form (i.e., arrow or I or hand, etc.) will remain unchanged no matter what I put in over. In that event clicking either button doesn't do anything not does the scroll wheel. Sometimes if the pointer form is responsive to what it is over clicking still works. Occasionally it will freeze for a looooooooong time, like more than 20 minutes, sometimes with the pointer still steerable, sometimes not. When it freezes like that the only thing I've been able to do was cold reboot. I haven't tried leaving it on overnight. It didn't respond to any of the hot keys I knew to bring up a terminal or clicking on a terminal launcher or cntrl-alt-del or cntrl-z or cntrl-c (desperate dos man here, lol) or anything. I've learned a few more magic key sequences, including the _Alt+PrintScreen_+R+E+I+S+U+B to try since the last time it froze totally (hasn't done it today). I'll write them down shortly and give them a try next time it freezes. I read where some people with similar problems got rid of them by updating the graphics driver to a more recent propietary one than the latest proprietary one in the repository. So I added the [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) maverick repository and now I'm using the nvidia 290.10-0ubuntu1~maverick~xup1 driver. It didn't seem to make any difference. In response to another story I installed the CompizConfig Settings Manager but I've looked at the options and I can't see anything obvious to try changing. The last seven times this has happened I copied the .xsession-errors log and they all look fairly similar. To my uneducated eye the thing that stands out is they all have either:

```
(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400084 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** (update-notifier:1764): DEBUG: aptdaemon on bus: 0
** (update-notifier:1764): DEBUG: Skipping reboot required
Tab close- xul:tab
Tab close- tab
Tab close- tab
```or this very similar sequence:

```
(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (update-notifier:1772): DEBUG: aptdaemon on bus: 0
** (update-notifier:1772): DEBUG: Skipping reboot required
NOTE: child process received `Goodbye', closing down

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
```and then go on through other nasty sounding error messages, very frequently, but not always including a whole lot of "(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead".

It didn't use to do this. I can't think of anything I installed or uninstalled that could have broke it, but I can't absolutely say that's impossible. The first problem I had was an inability to write good CDs from iso files which I assumed meant I need a new burner.  I'm still assuming that is unrelated but correct me if you suspect a connection. I also see a lot of very high cpu usage in system monitor at times,  frequently associated with a radical slowdown, usually just in one core  of my pentium d. But usually I have to be lucky and have system monitor up to see this because the slowdowns prevent system monitor from coming up now. OK, one more thing, maybe unrelated. Frequently I can't get firefox to start with an error message saying it is already running but not responding and indeed firefox-bin appears as a process in system monitor. So I made a launcher to "killall firefox-bin" which is adequate to deal with it. I only mention it in case it is a clue for someone. The slowing/freezing  seems to have gotten progressively worse which to me suggest a hardware fault. I've run memory checkers frequently but I can do it again if that is indicated. I'm about ready to just start upgrading one component at a time until I replace the one at fault if I can't come up with some better way of diagnosing the problem. As a temporary measure I was thinking of uninstalling nautilus and using thunar. Any suggestions? If nothing else, any ideas on how I might get a handle on what hardware, if any, is more likely to be the culprit?  TIA for any suggestions.

Here are complete copies of .xsession-errors logs if anyone wants to look at them further:
```

1
---------------------------
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-NFLPgt
GNOME_KEYRING_CONTROL=/tmp/keyring-NFLPgt
GNOME_KEYRING_CONTROL=/tmp/keyring-NFLPgt
SSH_AUTH_SOCK=/tmp/keyring-NFLPgt/ssh

(gnome-power-manager:1586): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
gnome-session[1537]: WARNING: Could not launch application 'evolution-alarm-notify.desktop': Unable to start application: Failed to execute child process "/usr/lib/evolution/2.30/evolution-alarm-notify" (No such file or directory)

(polkit-gnome-authentication-agent-1:1617): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1617): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
** (nm-applet:1613): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
** Message: applet now embedded in the notification area
Initializing nautilus-clamscan extension
Initializing nautilus-bitdefender extension
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (update-notifier:1772): DEBUG: aptdaemon on bus: 0
** (update-notifier:1772): DEBUG: Skipping reboot required
NOTE: child process received `Goodbye', closing down

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab

----------------------------
2
-------
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-NFLPgt
GNOME_KEYRING_CONTROL=/tmp/keyring-NFLPgt
GNOME_KEYRING_CONTROL=/tmp/keyring-NFLPgt
SSH_AUTH_SOCK=/tmp/keyring-NFLPgt/ssh

(gnome-power-manager:1586): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
gnome-session[1537]: WARNING: Could not launch application 'evolution-alarm-notify.desktop': Unable to start application: Failed to execute child process "/usr/lib/evolution/2.30/evolution-alarm-notify" (No such file or directory)

(polkit-gnome-authentication-agent-1:1617): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1617): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
** (nm-applet:1613): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
** Message: applet now embedded in the notification area
Initializing nautilus-clamscan extension
Initializing nautilus-bitdefender extension
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (update-notifier:1772): DEBUG: aptdaemon on bus: 0
** (update-notifier:1772): DEBUG: Skipping reboot required
NOTE: child process received `Goodbye', closing down

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2200003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2200003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied

---------
3
-----------
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-NFLPgt
GNOME_KEYRING_CONTROL=/tmp/keyring-NFLPgt
GNOME_KEYRING_CONTROL=/tmp/keyring-NFLPgt
SSH_AUTH_SOCK=/tmp/keyring-NFLPgt/ssh

(gnome-power-manager:1586): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
gnome-session[1537]: WARNING: Could not launch application 'evolution-alarm-notify.desktop': Unable to start application: Failed to execute child process "/usr/lib/evolution/2.30/evolution-alarm-notify" (No such file or directory)

(polkit-gnome-authentication-agent-1:1617): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1617): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
** (nm-applet:1613): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
** Message: applet now embedded in the notification area
Initializing nautilus-clamscan extension
Initializing nautilus-bitdefender extension
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (update-notifier:1772): DEBUG: aptdaemon on bus: 0
** (update-notifier:1772): DEBUG: Skipping reboot required
NOTE: child process received `Goodbye', closing down

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1610): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2005): Gdk-WARNING **: XID collision, trouble ahead
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2200003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2200003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
[ConvConfHandler] isPreferred contentType: application/x-apple-diskimage
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab

--------
4
--------------
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-exREKc
GNOME_KEYRING_CONTROL=/tmp/keyring-exREKc
GNOME_KEYRING_CONTROL=/tmp/keyring-exREKc
SSH_AUTH_SOCK=/tmp/keyring-exREKc/ssh

(gnome-power-manager:1576): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
gnome-session[1527]: WARNING: Could not launch application 'evolution-alarm-notify.desktop': Unable to start application: Failed to execute child process "/usr/lib/evolution/2.30/evolution-alarm-notify" (No such file or directory)

(polkit-gnome-authentication-agent-1:1607): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1607): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
** (nm-applet:1603): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
** Message: applet now embedded in the notification area
Initializing nautilus-clamscan extension
Initializing nautilus-bitdefender extension
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400084 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** (update-notifier:1764): DEBUG: aptdaemon on bus: 0
** (update-notifier:1764): DEBUG: Skipping reboot required
Tab close- xul:tab
Tab close- tab
Tab close- tab

---------
5
----------
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-exREKc
GNOME_KEYRING_CONTROL=/tmp/keyring-exREKc
GNOME_KEYRING_CONTROL=/tmp/keyring-exREKc
SSH_AUTH_SOCK=/tmp/keyring-exREKc/ssh

(gnome-power-manager:1576): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
gnome-session[1527]: WARNING: Could not launch application 'evolution-alarm-notify.desktop': Unable to start application: Failed to execute child process "/usr/lib/evolution/2.30/evolution-alarm-notify" (No such file or directory)

(polkit-gnome-authentication-agent-1:1607): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1607): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
** (nm-applet:1603): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
** Message: applet now embedded in the notification area
Initializing nautilus-clamscan extension
Initializing nautilus-bitdefender extension
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400084 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** (update-notifier:1764): DEBUG: aptdaemon on bus: 0
** (update-notifier:1764): DEBUG: Skipping reboot required
Tab close- xul:tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
sys:1: GtkWarning: IA__gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Tab close- tab
Tab close- tab
Tab close- tab

---------
6
----------
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-exREKc
GNOME_KEYRING_CONTROL=/tmp/keyring-exREKc
GNOME_KEYRING_CONTROL=/tmp/keyring-exREKc
SSH_AUTH_SOCK=/tmp/keyring-exREKc/ssh

(gnome-power-manager:1576): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
gnome-session[1527]: WARNING: Could not launch application 'evolution-alarm-notify.desktop': Unable to start application: Failed to execute child process "/usr/lib/evolution/2.30/evolution-alarm-notify" (No such file or directory)

(polkit-gnome-authentication-agent-1:1607): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1607): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
** (nm-applet:1603): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
** Message: applet now embedded in the notification area
Initializing nautilus-clamscan extension
Initializing nautilus-bitdefender extension
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400084 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** (update-notifier:1764): DEBUG: aptdaemon on bus: 0
** (update-notifier:1764): DEBUG: Skipping reboot required
Tab close- xul:tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
sys:1: GtkWarning: IA__gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab


(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
/usr/lib/pymodules/python2.6/mirage.py:32: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import tempfile, socket, md5, threading


(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed



Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3e00084 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
NOTE: child process received `Goodbye', closing down
WARNING: waitpid failed pid:1753 errno:10: file ./src/base/process_util_posix.cc, line 233
WARNING: waitpid failed pid:1753 errno:10: file ./src/base/process_util_posix.cc, line 233
WARNING: Failed to deliver SIGKILL to 1753!(3).: file ./src/chrome/common/process_watcher_posix_sigchld.cc, line 162
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x340008c (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400084 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(gnome-screenshot:3177): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
NOTE: child process received `Goodbye', closing down
Window manager warning: GtkMenu failed to grab the pointer

** (gnome-panel:1598): WARNING **: Pointer grab failed


(firefox:3189): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
/usr/lib/pymodules/python2.6/mirage.py:32: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import tempfile, socket, md5, threading
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3c00084 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Tab close- tab

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
sys:1: Warning: g_utf8_collate: assertion `str1 != NULL' failed

/usr/lib/pymodules/python2.6/mirage.py:32: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import tempfile, socket, md5, threading
Tab close- tab
Tab close- tab

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

------------
7
----------
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-exREKc
GNOME_KEYRING_CONTROL=/tmp/keyring-exREKc
GNOME_KEYRING_CONTROL=/tmp/keyring-exREKc
SSH_AUTH_SOCK=/tmp/keyring-exREKc/ssh

(gnome-power-manager:1576): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
gnome-session[1527]: WARNING: Could not launch application 'evolution-alarm-notify.desktop': Unable to start application: Failed to execute child process "/usr/lib/evolution/2.30/evolution-alarm-notify" (No such file or directory)

(polkit-gnome-authentication-agent-1:1607): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1607): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
** (nm-applet:1603): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
** Message: applet now embedded in the notification area
Initializing nautilus-clamscan extension
Initializing nautilus-bitdefender extension
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400084 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** (update-notifier:1764): DEBUG: aptdaemon on bus: 0
** (update-notifier:1764): DEBUG: Skipping reboot required
Tab close- xul:tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
sys:1: GtkWarning: IA__gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/firefox %u.desktop for panel launcher: No such file or directory
Unable to open desktop file /home/f/Desktop/passwords.desktop for panel launcher: No such file or directory
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab


(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
/usr/lib/pymodules/python2.6/mirage.py:32: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import tempfile, socket, md5, threading


(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed



Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3e00084 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
NOTE: child process received `Goodbye', closing down
WARNING: waitpid failed pid:1753 errno:10: file ./src/base/process_util_posix.cc, line 233
WARNING: waitpid failed pid:1753 errno:10: file ./src/base/process_util_posix.cc, line 233
WARNING: Failed to deliver SIGKILL to 1753!(3).: file ./src/chrome/common/process_watcher_posix_sigchld.cc, line 162
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x340008c (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400084 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(gnome-screenshot:3177): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
NOTE: child process received `Goodbye', closing down
Window manager warning: GtkMenu failed to grab the pointer

** (gnome-panel:1598): WARNING **: Pointer grab failed


(firefox:3189): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(firefox:3189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
/usr/lib/pymodules/python2.6/mirage.py:32: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import tempfile, socket, md5, threading
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3c00084 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Tab close- tab

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
Tab close- tab
sys:1: Warning: g_utf8_collate: assertion `str1 != NULL' failed

/usr/lib/pymodules/python2.6/mirage.py:32: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import tempfile, socket, md5, threading
Tab close- tab
Tab close- tab

(nautilus:1600): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
```Thanks, oldos2er, for showing how to make this neater with the code tags.

---

### Post by Dreamer Fithp Apprentice on 2012-01-19
ignore this second post. I edited it into the first one and can't figure out how to delete this one.

---

### Post by schveiguy on 2012-01-19
My thought is your system is thrashing (meaning it's continually swapping memory to/from disk).  Watch the memory usage and see how much physical memory you are using.

I had the same problem after an upgrade to 11.10, and when I updated the memory to 2GB from 1GB, the problem went away.  Unity is definitely a memory hog.

---

### Post by Colonel_Ingus on 2012-01-19
Do you have a HDD light anywhere? If so look at it, if that HDD light is on the whole time its slow, then it's possible you don't have enough memory and having to use the swap. I had to buy more memory recently because of this. 

More memory is cheap and a fast way to speed it up. 

Once I encountered random slow downs like that and it was bad sectors on the HDD too, that's another possibility. 

Hope you get it fixed soon, best of luck.

---

### Post by Dreamer Fithp Apprentice on 2012-01-19
Thanks, guys. I'm trying to make it slowdown or crash at the moment and of course it won't. I have literally a couple of hundred (well, I didn't count, but I had a bunch open when I opened 138 more from a folder of bookmarks, so that is probably about right) open in firefox 3.6.24 (the latest in the standard Maverick repo); VLC playing one movie; SM playing another movie; two instances of Nautilus, one with 3 tabs and the other with 5 tabs, plus Systerm Monitor.  It took all  of that to boost my memory usage up to 80%  = 1.6 gb out of 2 gb installed and swap hasn't been touched. CPU usage is high and variable on both cores but I have had only momentary slowdowns, I think maybe when one of the cpu cores goes to near 100%, and no hangs. 

From this I suspect:

1- that memory availability and swap usage are unlikely to be the issue but this is hardly a confident conclusion since I can't crash it at the moment.

2-that it is probably either:
    a-an intermittent hardware fault
or
    b-some program that occasionally kicks in and uses up my cpu

Do those log messages mean anything to anybody?

---

### Post by Dreamer Fithp Apprentice on 2012-02-16
Still having this problem but it is less severe. I've started leaving System Monitor open and switching to it in the task bar (i'm still using 10.10 until and unless I can get Mate to work well in my Oneiric alternate bootable partition)  to try to diagnose causes.  Often I can get it to show although I can't always get it to switch between its tabs when the system slows. Still looks like something is using a LOT of cpu, maxing out one or both cores, when the slowdowns happen. Leaving System Monitor on the processes tab sorted on the %cpu column usually shows "plugin-container" topping the list. Right now it is running over 90% and both cores are in heavy use. The process ID says 1858. I could almost swear that earlier the ID number was 7265 but maybe I misread it. Whatever that process is, it is also using a lot of memory, almost half a gig.  Am I right to suspect something is amiss with this process? How to I go about finding out exactly where it is coming from? I would think System Monitor would have some way to query properties of a process to see where it comes from but I can't find anything like that.

I'm suspecting this may be a situation where several things were contributing to the problem. It seemed to get a lot less severe when I replaced my CD/DVD drive. Although I didn't have to be doing anything that USED the CD/DVD drive before for the problem to occur. I've had poisonous hard drives (D**n Seagates) before that caused crashes merely by being connected so I suspect something of the sort was going on with the CD/DVD drive I replaced. Possibly it was sucking too much power and made the voltage go down. 

If anyone has thoughts in reaction to reading this I'd be interested and appreciative to read them.

---

### Post by JRV on 2012-02-16
Open a terminal and enter the command:```
top
```


This will show you if a program is hogging the processor/memory.

---

### Post by Dreamer Fithp Apprentice on 2012-02-18
Thanks, JRV. Top is certainly a better way of doing it as System Monitor is a bit of a resource hog itself. I knew about top but was still in the lazy gui habit of using System Monitor. Shame on me. Top is light enough I can keep it running all the time. Much better.:D

---

### Post by CatKiller on 2012-02-18
Plugin-container is probably Flash. It uses a lot of resources because Flash is rubbish.

I suspect hard drive. I had similar problems with a broken ribbon cable that would short sometimes, but faulty hard drive would do it too. Especially if you get clicking noises before or during the freeze.

You've stress-tested the machine for normal use and the problem is intermittent which sounds like classic hardware fault to me. Hard drives are the most likely hardware to fail and would cause these symptoms through blocking I/O.

You can probably get a testing utility from the manufacturer's website to run some tests. Back up your data in the meantime.

You might also want to keep an eye on your temperatures too as another line of enquiry.

---

### Post by Dreamer Fithp Apprentice on 2012-02-18
Thanks, Catkiller. That all sounds like sage advice. I'll order a new hard drive today as I'm running out of space to back up. I'll back it up before I run the diagnostics as those are probably stressful in themselves. And thanks for the Flash tip. That is pretty easily testable if I understand it correctly. The problem shouldn't occur as long as I block flash. I'll report back when I've followed all this up and have achieved insights someone else may benefit from or sufficient to generate more questions.

---

