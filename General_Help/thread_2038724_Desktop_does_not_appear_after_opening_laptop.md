---
title: "Desktop does not appear after opening laptop"
date: 2012-08-07
forum: General Help
---

### Post by Kalanac on 2012-08-07
Hello,

The title of the thread is likely a bit vague so I'll try to explain this as clearly as possible.  Here is what I expect to happen:

Boot laptop > Use laptop > Close lid > Open lid > Enter password > Continue using laptop.

However, what is happening is I open the lid and get the desktop wallpaper, but nothing else.  No password dialog appears and I need to reset the laptop.  This doesn't always happen.  I'm not certain why it happens some times and not others.  I've tried to close the lid and open again but that doesn't have any effect.  

I'm able to reboot using the "magic key" (ctrl+alt+sysreq+reisub) sequence so the computer itself is still responsive.  My feeling is that the password dialogue is either not being summoned or is appearing in such a position that I can't see it (thinking on it, I'll try typing blind next time it happens to see if that works).  I've tried switching desktops (ctrl+alt+cursor) to see if that works with no effect.

So then gurus any ideas where to begin with this one?  I'm using a fully updated version of Precise Pangolin but I've had the issue since Oneric, today I was just vexed enough to report it :)  Oh if it makes any difference I have to use the linux_ocpi option in grub to get around the fact my laptop backlight doesn't come on by itself.

---

### Post by Kalanac on 2012-08-10
Bump and a bit of an update:

I tried blind typing, no luck.  I was able to drop to the tty terminals though, so I can get some stuff from terminal and interact with the system if anyone has suggestions or needs error logs or something.

I ended up rebooting, but I'll try restarting the x session next time.

---

### Post by 2F4U on 2012-08-10
You should look into the system log file and also in the file /var/log/pm-suspend.log. Instead of closing the lid, have you tried to suspend from the menu?

---

### Post by Kalanac on 2012-08-10
OK, that file has 2330 lines of logular gubbins.  Is there anything specific I should be searching for?  I can attach a file if needed.

Suspend from the menu works as per the lid.  It woke up normally and presented the password dialogue as it should, but that sometimes happens with the lid too.  I can't consistently get the error to occur, it just happens from time to time (maybe 2-3 times a day depending on usage)

---

