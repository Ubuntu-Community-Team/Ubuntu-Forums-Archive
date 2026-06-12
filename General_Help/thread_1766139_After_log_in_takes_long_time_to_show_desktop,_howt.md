---
title: "After log in takes long time to show desktop, howto monitor events at log in time?"
date: 2011-05-24
forum: General Help
---

### Post by jamesjenner on 2011-05-24
G'day all,


It takes me a while to log in the splash screen just sits there for ages before i get to the desktop. Never used to be this slow and I'm not sure why. 

Firstly, I'm running Ubuntu 11.04, standard DE. I do have conky starting up in a script but it has the & at the end of the line so I didn't think this would cause it (or is there some special case for log in time on how & is treated?). However as a test I will comment out the line in the script and see if it is the cause.

However just for general knowledge and in case that isn't the problem, how does one go seeing what is happening during the time from when one log's in and the desktop is displayed? Is there some kind of log that shows the date/time that can be enabled or is there a debug mode that can be enabled somehow via special keys or maybe from grub? 

I'm really curious as to how to debug such a delay without resorting to disabling start up programs for the DE.

Cheers,

James.

---

### Post by jaychandran_s on 2011-05-24
Please post your system specs, i probably think that either of these may be the causes of your problem...(causes are listed by decreasing probability)...
1. The most convincing reason for your problem is that you have too less RAM for ubuntu (more than the minimum, but not optimal for the kinds of softwares you use, might be).
2. Your graphics card is too slow. (in that case, just disable the composting manager, either compiz or metacity)
3. You have a 32-bit machine and you have installed 64-bit ubuntu..

Hope that my reply helps...

---

### Post by jamesjenner on 2011-05-24
> **jaychandran_s said:**
> Please post your system specs, i probably think that either of these may be the causes of your problem...(causes are listed by decreasing probability)...
1. The most convincing reason for your problem is that you have too less RAM for ubuntu (more than the minimum, but not optimal for the kinds of softwares you use, might be).
2. Your graphics card is too slow. (in that case, just disable the composting manager, either compiz or metacity)
3. You have a 32-bit machine and you have installed 64-bit ubuntu..

Hope that my reply helps...

That will be a negative to your points sorry mate. I have a Quad Core system with 4 Gig of RAM and a GPU with 1 Gig dedicated memory. I cannot remember which Intel chip it is or which Graphics Card it is but I can find out tonight. Also the health of all my HD's are fine.

The performance of my system is fine, that is not the issue. The issue is how to determine what is causing a 'pause' during the log in process. I was hoping that there would be some way to log or capture what is happening when (debug it so to speak) so I can see what is taking the most time and find the culprit.

---

### Post by wildmanne39 on 2011-05-24
> **jamesjenner said:**
> That will be a negative to your points sorry mate. I have a Quad Core system with 4 Gig of RAM and a GPU with 1 Gig dedicated memory. I cannot remember which Intel chip it is or which Graphics Card it is but I can find out tonight. Also the health of all my HD's are fine.

The performance of my system is fine, that is not the issue. The issue is how to determine what is causing a 'pause' during the log in process. I was hoping that there would be some way to log or capture what is happening when (debug it so to speak) so I can see what is taking the most time and find the culprit.
Hi, after you boot go into log file viewer and see what the logs say.

---

### Post by jamesjenner on 2011-05-24
> **wildmanne39 said:**
> Hi, after you boot go into log file viewer and see what the logs say.

ahh thanks mate, didn't realise there was such a beast, love unity how I can just search for it and find it :) I was expecting to go to /var/logs or similar to find some file. 

But now I have a question. Which log shows what happens after you select to log in? as in what shows what is loaded for your DE?

I'm looking at the syslog, finding a couple of things like:

```

May 24 19:09:01 james-Ubuntu CRON[1564]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
May 24 19:09:01 james-Ubuntu CRON[1562]: (CRON) error (grandchild #1564 failed with exit status 1)
May 24 19:10:39 james-Ubuntu gdm-session-worker[1405]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May 24 19:10:55 james-Ubuntu gnome-session[1589]: WARNING: Could not launch application 'skype-wrapper.desktop': Unable to start application: Failed to execute child process "skype-wrapper" (No such file or directory)

```

Note sure what the cron job was that failed, appears to be trying to delete something? If so I presume it's some php5 related thing which I'm not concerned about, unless it's causing a delay.

user.log, messages.log and debug.log are empty. I presume I could tell by my auth.log what time I logged on and then compare others to it? But I'm not sure which log would indicate a hold up in the DE being started up. :confused:

---

### Post by jamesjenner on 2011-05-25
Okkkaaayyyy...

No response from anyone but I've figured out that the following is posted in the auth.log at from the time I log in. Not sure if any of the errors would cause the problem i'm experiencing.

```
May 25 17:08:04 james-Ubuntu gdm-session-worker[1412]: pam_unix(gdm:session): session opened for user james by (uid=0)
May 25 17:08:04 james-Ubuntu gdm-session-worker[1412]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
May 25 17:08:10 james-Ubuntu polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.30 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May 25 17:08:29 james-Ubuntu dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.42" (uid=1000 pid=1666 comm="nautilus ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.12" (uid=0 pid=1247 comm="/usr/sbin/console-kit-daemon --no-daemon "))
May 25 17:08:43 james-Ubuntu dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.45" (uid=1000 pid=1940 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.12" (uid=0 pid=1247 comm="/usr/sbin/console-kit-daemon --no-daemon "))

```
The above log entries are interesting as you can see from when i hit enter on my password to when the desktop displayed. I used the clock to determine the system time as soon as it was visible on the DE and it was 5:08:44, so the above log saying the last error was at 08:43 seems like possible causality though correlation doesn't mean causality. 

Any help appreciated.

---

### Post by wildmanne39 on 2011-05-25
> **jamesjenner said:**
> Okkkaaayyyy...

No response from anyone but I've figured out that the following is posted in the auth.log at from the time I log in. Not sure if any of the errors would cause the problem i'm experiencing.

```
May 25 17:08:04 james-Ubuntu gdm-session-worker[1412]: pam_unix(gdm:session): session opened for user james by (uid=0)
May 25 17:08:04 james-Ubuntu gdm-session-worker[1412]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
May 25 17:08:10 james-Ubuntu polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.30 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May 25 17:08:29 james-Ubuntu dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.42" (uid=1000 pid=1666 comm="nautilus ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.12" (uid=0 pid=1247 comm="/usr/sbin/console-kit-daemon --no-daemon "))
May 25 17:08:43 james-Ubuntu dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.45" (uid=1000 pid=1940 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.12" (uid=0 pid=1247 comm="/usr/sbin/console-kit-daemon --no-daemon "))

```
The above log entries are interesting as you can see from when i hit enter on my password to when the desktop displayed. I used the clock to determine the system time as soon as it was visible on the DE and it was 5:08:44, so the above log saying the last error was at 08:43 seems like possible causality though correlation doesn't mean causality. 

Any help appreciated.
Hi, I do not know for sure what is going on there, I posted on here several hours ago to you, I dont know what happened to it, I said to look in the boot,xorg,kernel and system logs.

---

### Post by wildmanne39 on 2011-05-25
> **jamesjenner said:**
> Okkkaaayyyy...

No response from anyone but I've figured out that the following is posted in the auth.log at from the time I log in. Not sure if any of the errors would cause the problem i'm experiencing.

```
May 25 17:08:04 james-Ubuntu gdm-session-worker[1412]: pam_unix(gdm:session): session opened for user james by (uid=0)
May 25 17:08:04 james-Ubuntu gdm-session-worker[1412]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
May 25 17:08:10 james-Ubuntu polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.30 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May 25 17:08:29 james-Ubuntu dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.42" (uid=1000 pid=1666 comm="nautilus ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.12" (uid=0 pid=1247 comm="/usr/sbin/console-kit-daemon --no-daemon "))
May 25 17:08:43 james-Ubuntu dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.45" (uid=1000 pid=1940 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.12" (uid=0 pid=1247 comm="/usr/sbin/console-kit-daemon --no-daemon "))

```
The above log entries are interesting as you can see from when i hit enter on my password to when the desktop displayed. I used the clock to determine the system time as soon as it was visible on the DE and it was 5:08:44, so the above log saying the last error was at 08:43 seems like possible causality though correlation doesn't mean causality. 

Any help appreciated.
Hi, I looked again those logs are pertaining to your password authorizing you to log on.

---

### Post by jamesjenner on 2011-05-25
> **wildmanne39 said:**
> Hi, I looked again those logs are pertaining to your password authorizing you to log on.

Yup, as I said, from the auth.log. But I wanted to know what the two last lines are which appear to be errors, and if the errors could be the cause of the delayed log in time. 

The first one appears to be related to nautilus, the second one appears to be something to do with /usr/lib/indicator-datetime/indicator-datetime-ser which I can only presume is the indicator under Unity to show the time. Buggered if I know why an entry exists for it in auth.log.

---

### Post by sealtrip on 2011-11-19
> **jamesjenner said:**
> 
The first one appears to be related to nautilus, the second one appears to be something to do with /usr/lib/indicator-datetime/indicator-datetime-ser which I can only presume is the indicator under Unity to show the time. Buggered if I know why an entry exists for it in auth.log.

I am facing the exact same issue right now. Did you manage to find a solution?

---

