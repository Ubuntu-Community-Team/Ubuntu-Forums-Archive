---
title: "Unknown Program not responding when trying to shutdown"
date: 2009-12-14
forum: General Help
---

### Post by LowSky on 2009-12-14
See picture. It's AWN related, It does not happen when I close it before shutting down. But anyone have any idea if its a applet or AWN itself?

---

### Post by lightstream on 2009-12-14
I had a similar thing happen for a short while.

I found that it wouldn't be a problem if I shut down by pressing the button on the front of the PC; it would only happen if I shut down using the menu option.

In my case it was not AWN as I don't use that.

---

### Post by LowSky on 2009-12-14
I'm wondering if it's Python or mabye Compiz?

---

### Post by lightstream on 2009-12-14
Do you actually get this in Karmic? I haven't seen mine for a couple of months.

Maybe you could try to find what it is by using top, and killing processes until the dialog shows it closes?

There's probably a better way to find out what it is.. although I don't know what!

---

### Post by okhowaboutthisusername on 2009-12-14
2.6.31-16-generic #53-Ubuntu SMP x86_64

I saw this today. In fact, it's the third time in a couple of weeks that i've found my machine still running after walking away. This time, i clicked the monitor back on and noticed the warning. I chose "shut down anyway" and things seemed to be proceeding normally (screen went dark, etc.) but the box remained running.

> I found that it wouldn't be a problem if I shut down by pressing the button on the front of the PC;It would do because that's a hardware switch. The OS cannot override that.

syslog sez:

```
Dec 14 15:14:51 apollo gnome-session[2004]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
Dec 14 15:14:51 apollo gnome-session[2004]: WARNING: Client '(null)' failed to reply before timeout
Dec 14 15:14:51 apollo gnome-session[2004]: CRITICAL: gsm_client_peek_app_id: assertion `GSM_IS_CLIENT (client)' failed
Dec 14 15:14:51 apollo gnome-session[2004]: CRITICAL: gsm_client_get_app_name: assertion `GSM_IS_CLIENT (client)' failed
Dec 14 15:14:51 apollo gnome-session[2004]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
Dec 14 15:17:01 apollo CRON[4213]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```I'm not sure what to make of that.

---

### Post by LowSky on 2009-12-15
I found these
[http://ubuntuforums.org/showthread.php?t=1238393](http://ubuntuforums.org/showthread.php?t=1238393)
[http://www.uluga.ubuntuforums.org/showthread.php?p=7593553](http://www.uluga.ubuntuforums.org/showthread.php?p=7593553)

It appears to be the same issue

Because the error is so vague I think I'm going to try to shut down one process at a time until the error doesn't show up and then report back any findings

---

### Post by lightstream on 2009-12-15
> **okhowaboutthisusername said:**
> 
It would do because that's a hardware switch. The OS cannot override that.


Actually it is the OS that chooses how to respond to the power button on the computer case. If you go to System > Preferences > Power Management you can choose what actions to perform when the power button (or the suspend button) is pressed.

In Windows, shutting down by pressing the power button performs a hard shutdown, where any running processes are killed if they fail to respond to a close signal (the TERM signal), while the soft shutdown will not kill non-responsive programs without user confirmation. In Windows, shutting down by power switch is often quite a bit quicker because of this.

I have no idea if a similar system is found in Linux though.

Anyway I'll be using the menu to shutdown for a bit to see if my issue has really gone away or not.

PS okhowaboutthisusername -> love the user name!!

---

### Post by okhowaboutthisusername on 2009-12-23
> Actually it is the OS that chooses how to respond to the power button on the computer case.

You're right. I wasn't very clear and did not at all take that into account. What I was referring to is that holding down the power button will force the hardware to take action, in spite of a completely unresponsive OS.

This happened to me again yesterday, btw. But there was no alert dialogue--no OS at all--when i turned the monitor back on. It seems as if there are two similar issues here. Sometimes, the OS won't begin the shutdown process due to an unresponsive mystery process and sometimes everything appears to have exited but the box stays powered up. Whether they're related is another thing.

---

