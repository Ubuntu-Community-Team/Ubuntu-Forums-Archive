---
title: "Gnome Nanny breaks Internet Connection when uninstalled"
date: 2012-07-28
forum: General Help
---

### Post by ctsdownloads on 2012-07-28
Just as the title says, Gnome Nanny immediately breaks my Internet connection with any browser when uninstalled. I am 98% sure it's doing some blocking, when uninstalled, but I am unsure how to prevent this. Have tried purging, reinstalling, etc.

I am moving things to OpenDNS web filtering (or will be, eventually).

All I want is the ability to remove Gnome Nanny without losing my web connectivity to websites. On a side note, apt still works even after Gnome Nanny is removed.

 Help

---

### Post by ctsdownloads on 2012-07-28
(bump) Anyone, really, anyone? Bueller? Anyone? :)  (bump)

---

### Post by dcstar on 2012-07-29
> **ctsdownloads said:**
> Just as the title says, Gnome Nanny immediately breaks my Internet connection with any browser when uninstalled. I am 98% sure it's doing some blocking, when uninstalled, but I am unsure how to prevent this. Have tried purging, reinstalling, etc.

I am moving things to OpenDNS web filtering (or will be, eventually).

All I want is the ability to remove Gnome Nanny without losing my web connectivity to websites. On a side note, apt still works even after Gnome Nanny is removed.

 Help

Remove the Proxy settings in the browser.

---

### Post by ctsdownloads on 2012-07-29
> **dcstar said:**
> Remove the Proxy settings in the browser.

Don't believe Gnome Nanny has anything to do with browser specific proxy settings. Just in case, I checked and no proxy settings are being used in Firefox. The issue is system-wide, not limited to just my browser.

Hopefully someone has additional thoughts? To reiterate, with Gnome Nanny installed, accessing the Internet is possible. Uninstalled, it's completely down without any clear resolution to fixing the problem.

Help

---

### Post by Cheesehead on 2012-07-29
Are you asking how to trooubleshoot Nanny to file a bug report?
Or are you asking how to fix your network connection?

---

### Post by ctsdownloads on 2012-07-29
> **Cheesehead said:**
> Are you asking how to trooubleshoot Nanny to file a bug report?
Or are you asking how to fix your network connection?

Well, neither actually. I may not have been clear earlier -- let me try one more time.

1) Working Ubuntu 12.04 install, everything is great, I can connect to the Web via any browser, FTP, etc.

2) Foolishly installed [Gnome Nanny]("http://projects.gnome.org/nanny/"). Installed, everything in #1 worked, however Gnome Nanny, wasn't really what I was looking for.

3) Uninstalled via apt, immediately all connectivity to the Internet is broken. Software updates, ability to surf the web via any browser, etc.

Clearly, there is still some filtering rules that go ballistic, when the software is uninstalled. I imagine it's blocking something, somewhere.

This isn't a problem with my network connection, this is a problem with uninstalling Gnome Nanny and having it break/block my ability to connect to the Internet.

Hopefully this is more clear.

Thanks

---

### Post by Cheesehead on 2012-07-29
Did nanny install/uninstall cleanly? Were there any error messages?
Did anything get added/removed in addition to nanny?

Aside from the web browser, do other network-using applications like e-mail work?

Nanny, if I recall correctly, does work by creating a proxy. That's where the filter resides. But removing nanny cleans up and removes the proxy. A failure to clean up and remove the proxy (located at /usr/share/pyshared/nanny/daemon/proxy/ ) certainly causes at least one error message. Does that directory still exist on your system?

---

### Post by ctsdownloads on 2012-07-30
> **Cheesehead said:**
> Did nanny install/uninstall cleanly? Were there any error messages?
Did anything get added/removed in addition to nanny?

Aside from the web browser, do other network-using applications like e-mail work?

Nanny, if I recall correctly, does work by creating a proxy. That's where the filter resides. But removing nanny cleans up and removes the proxy. A failure to clean up and remove the proxy (located at /usr/share/pyshared/nanny/daemon/proxy/ ) certainly causes at least one error message. Does that directory still exist on your system?


Thanks. After uninstalling with apt, zero errors and the above directory is removed. I removed the software using --purge as well. As soon as it's done, all internet access is dead. Oddly, I can ping websites though. So clearly, I'm being blocked/firewalled off somewhere.

Reinstalling via apt, the only error I can generate is:

update-rc.d: warning: /etc/init.d/nanny missing LSB information


Also, both installed and uninstalled, Ubuntu network proxy settings are empty and not in use. This doesn't feel like a proxy problem at this stage, it feels like a firewall issue. I've triple checked to see if my network settings change, nothing there. IP and subnet, unchanged in all instances. With my wired connection, I even tried deleting the connection and redoing it. No dice.

Anyway to see if I am somehow firewalled off? This is a vanilla Gnome Nanny install, nothing more. Thanks

---

### Post by ctsdownloads on 2012-07-30
Okay, finally have an interesting discovery. Running a traceroute without Nanny installed, the traceroute stalls at XX-XX-XXX-X.evrt.wa.frontiernet.net when running it against Google.com.

If however, Nanny installed, the traceroute runs past XX-XX-XXX-X.evrt.wa.frontiernet.net all the way to Google without missing a beat.

Netstat and Ping, are working/correct no matter if Nanny is installed or not. Also changed the logs, nothing there indicating what is going on there either. Luckily I have a dedicated home directory and my apps backed up -- about ready to say forget it and do a clean install. This is getting to be silly. :)

If anything above gives you additional thoughts, please feel free to share them.

---

### Post by ctsdownloads on 2012-07-30
One last attempt? Anyone (see most recent post above please for details).

Thanks

---

