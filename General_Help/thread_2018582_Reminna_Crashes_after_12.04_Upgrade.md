---
title: "Reminna Crashes after 12.04 Upgrade"
date: 2012-07-06
forum: General Help
---

### Post by Iggy64 on 2012-07-06
Have been running 11.10 with LXDE desktop for many months, using Reminna to remote connect to Win XP machine (music server).  Upgraded Ubuntu to 12.04.  Now get occasional crashes of Reminna.  I'll have to write down the error message next time; but it says something like "Ubuntu 12.04 internal error."  Then it closes Reminna.  Is there a fix?

If this has been asked and answered, please forgive and point me to the thread.  I did not find it.

---

### Post by QIII on 2012-07-06
The actual error would be helpful.  If you launch Reminna from the terminal, you might get a pretty detailed message that you can cut and paste.  If not, we can have a look at the logs.

At this point we could all speculate on any of a hundred things that might be going on.

(By the way, I use Reminna to RDP into an XP box all the time.  So it does (generally?) work.)

---

### Post by Iggy64 on 2012-07-06
Thanks for the response, QIII.  As a relative Linux newbie, I guess I'm not being very helpful.  Here are the contents of syslog:

Jul  6 14:02:50 Laptop-61SXY91 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="584" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jul  6 14:02:59 Laptop-61SXY91 wpa_supplicant[809]: WPA: Group rekeying completed with 4c:e6:76:f9:68:34 [GTK=TKIP]
Jul  6 14:03:24 Laptop-61SXY91 anacron[908]: Job `cron.daily' terminated
Jul  6 14:03:24 Laptop-61SXY91 anacron[908]: Normal exit (1 job run)
Jul  6 14:17:01 Laptop-61SXY91 CRON[2854]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  6 14:39:49 Laptop-61SXY91 kernel: [ 3724.856518] show_signal_msg: 48 callbacks suppressed
Jul  6 14:39:49 Laptop-61SXY91 kernel: [ 3724.856529] remmina[1748]: segfault at 0 ip 05a01580 sp b59fdc40 error 4 in libfreerdp-gdi.so.1.0.1[59f5000+14000]
Jul  6 15:02:59 Laptop-61SXY91 wpa_supplicant[809]: WPA: Group rekeying completed with 4c:e6:76:f9:68:34 [GTK=TKIP]
Jul  6 15:11:11 Laptop-61SXY91 kernel: [ 5607.397500] remmina[2974]: segfault at 0 ip 080cf580 sp b61fec40 error 4 in libfreerdp-gdi.so.1.0.1[80c3000+14000]
Jul  6 15:17:01 Laptop-61SXY91 CRON[3784]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  6 15:49:11 Laptop-61SXY91 kernel: [ 7886.813417] remmina[3731]: segfault at 0 ip 04d4c580 sp b58fdc40 error 4 in libfreerdp-gdi.so.1.0.1[4d40000+14000]
Jul  6 16:02:59 Laptop-61SXY91 wpa_supplicant[809]: WPA: Group rekeying completed with 4c:e6:76:f9:68:34 [GTK=TKIP]
Jul  6 16:17:01 Laptop-61SXY91 CRON[4054]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

There are a couple of mentions of reminna in here, but I don't know enough to interpret this.  Maybe this is not even any help to someone like you.  If Reminna closes again, I'll try to catch the exact error message.

I might also try simply re-installing Reminna.

---

### Post by QIII on 2012-07-06
If reinstalling Reminna pulls in libfreerdp-plugins-standard 1.0.1, reinstalling Reminna might work.

The problem appears to be in the plug-in, which is being called by Reminna.  There may be nothing wrong with Reminna proper.

Try reinstalling it, which would do no harm.  But if you get the same segfault, I think we'll have to look at that plug-in.

---

### Post by dcstar on 2012-07-07
> **QIII said:**
> If reinstalling Reminna pulls in libfreerdp-plugins-standard 1.0.1, reinstalling Reminna might work.

The problem appears to be in the plug-in, which is being called by Reminna.  There may be nothing wrong with Reminna proper.
.........

The old Reminna and all of its components probably need to be totally removed and then the current Reminna reinstalled to ensure that it uses the new components.

---

### Post by Iggy64 on 2012-07-12
Thanks to both QIII and dcstar for your support.  I have been traveling for several days and have not had a chance to try the uninstall/re-install of Reminna.  Will do as soon as I get home.  

You advice is much appreciated.  I'm a Linux noob, but the community support is great.

---

