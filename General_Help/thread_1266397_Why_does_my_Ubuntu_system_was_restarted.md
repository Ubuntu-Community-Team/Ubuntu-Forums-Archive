---
title: "Why does my Ubuntu system was restarted?"
date: 2009-09-14
forum: General Help
---

### Post by CrAzYoNi on 2009-09-14
Hello all,
I was working on my Ubuntu Jaunty system (32bit) and playing the "terminal server client" application, it got frozen on full screen mode, so I opened a new tty (Ctrl+Alt+F1), logged in and killed it's two processes, afterwards I did "ps -u username | more" and after I passed some lines with the "Enter" button my system was restarted, on "/var/log/messages" file I can see the (might) related lines:
Sep 14 21:59:18 Server exiting on signal 15
Sep 14 22:00:16 Server syslogd 1.5.0#5ubuntu3: restart.

Do you have an idea about how can I check\know\notice what made the system restart?

Thanks in advance.

Yours,
CrAzYoNi

---

### Post by aesis05401 on 2009-09-14
Can you post the output of: ```

uname -r

```

---

### Post by CrAzYoNi on 2009-09-14
uname -a output:
Linux Server 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

---

### Post by NoaHall on 2009-09-14
I think that kernel's a old version - try updating.

---

### Post by CrAzYoNi on 2009-09-14
I'll try to update it in a few hours, would just finish to learn some code perl before...
Though if it's an old kernel or not... how can I know why my system had a restart?

---

### Post by scrooge_74 on 2009-09-14
did you check the other logs to see what happened?

---

### Post by CrAzYoNi on 2009-09-14
I'm learning about being system administrator... so I guess this is why i'm asking here my question;
I've checked the /var/log/messages & /var/log/kern.

Though else of the 2 lines above that I posted I didn't found anything that seem related to the restart.

---

### Post by scrooge_74 on 2009-09-14
did you check in /var/log/syslog and in /var/log/dmesg   ?

---

### Post by aesis05401 on 2009-09-14
Launchpad had a number of issues reported that resulted in this behavior, but they were filed against an earlier kernel version.  I don't have any other insight, sorry.

---

### Post by CrAzYoNi on 2009-09-15
Under /var/log/syslog file I found:
> 
Sep 14 21:58:59 Server console-kit-daemon[3302]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep 14 21:58:59 Server console-kit-daemon[3302]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep 14 21:58:59 Server gnome-session[3862]: WARNING: Unable to stop system: Not privileged for action: org.freedesktop.consolekit.system.stop no 
Sep 14 21:59:01 Server console-kit-daemon[3302]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep 14 21:59:01 Server console-kit-daemon[3302]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep 14 21:59:01 Server gnome-session[3862]: WARNING: Unable to stop system: Not privileged for action: org.freedesktop.consolekit.system.stop no 
Sep 14 21:59:01 Server console-kit-daemon[3302]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep 14 21:59:01 Server console-kit-daemon[3302]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep 14 21:59:01 Server gnome-session[3862]: WARNING: Unable to stop system: Not privileged for action: org.freedesktop.consolekit.system.stop no 
Sep 14 21:59:01 Server console-kit-daemon[3302]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep 14 21:59:01 Server console-kit-daemon[3302]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep 14 21:59:01 Server gnome-session[3862]: WARNING: Unable to stop system: Not privileged for action: org.freedesktop.consolekit.system.stop no 
Sep 14 21:59:01 Server console-kit-daemon[3302]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep 14 21:59:01 Server console-kit-daemon[3302]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep 14 21:59:01 Server gnome-session[3862]: WARNING: Unable to stop system: Not privileged for action: org.freedesktop.consolekit.system.stop no 
Sep 14 21:59:05 Server NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Sep 14 21:59:05 Server NetworkManager: <info>  (wlan0): deactivating device (reason: 38). 
Sep 14 21:59:05 Server console-kit-daemon[3302]: WARNING: Unable to activate console: No such device or address 
Sep 14 21:59:05 Server NetworkManager: <info>  Clearing nscd hosts cache. 
Sep 14 21:59:05 Server kernel: [169799.869769] wlan0: disassociating by local choice (reason=3)
Sep 14 21:59:05 Server init: tty4 main process (2269) killed by TERM signal
Sep 14 21:59:05 Server init: tty5 main process (2270) killed by TERM signal
Sep 14 21:59:05 Server init: tty2 main process (2277) killed by TERM signal
Sep 14 21:59:05 Server init: tty3 main process (2278) killed by TERM signal
Sep 14 21:59:05 Server init: tty6 main process (2279) killed by TERM signal
Sep 14 21:59:05 Server init: tty1 main process (3819) killed by TERM signal


After those lines I notice that daemons begin to exit\end...
> 
Sep 14 21:59:10 Server postfix/master[8821]: terminating on signal 15
Sep 14 21:59:14 Server mysqld_safe[30120]: ended
Sep 14 21:59:18 Server exiting on signal 15



Does any of those lines can describe why the restart has been occurred?

The file /var/log/dmesg does not contain any understandable time-stamp, at-least not understandable for me; So I didn't knew what\Where exactly to search.

Thanks in advance for trying to help me.

Yours,
CrAzYoNi.

---

### Post by aesis05401 on 2009-09-17
Hello, 

Can you post a bit of log from before the part you already gave us?  Are there any ACPI temp events?  Has this happened again since the first time?

---

