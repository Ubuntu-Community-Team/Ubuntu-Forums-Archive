---
title: "Recent update deleted my mails!"
date: 2010-03-19
forum: General Help
---

### Post by lian1238 on 2010-03-19
Hi, there was an update today, and I think that was what caused some of my mails to go missing. In my Thunderbird inbox, my "latest" mails were received in December 2009. All my mail from then up to now are missing. It also only has my first account. My second mail which I added later is also missing. (Saved passwords seem to be missing too. I got a prompt for my password)

Is there anyway the recent update caused this? And how do I 'recover' my mails?

My themes and icons are not applied until I run gnome-settings-daemon.

Thanks for any advice.

---

### Post by GandG on 2010-03-19
The update caused me similar problems too - had been running Thunderbird 3. The Gui was unresponsive and E-mails, Accounts etc were missing. 

Uninstalled T3 and re-installed T2.0.0.24 and found nothing changed. Uninstalled T20024, manually deleted any residual 'found' Thunderbird bin files then re-installed T20024. Copied profile and ini files from .thunderbird to the new .mozilla-thunderbird folder  which the latest install created and everything came back OK.

Think I'll leave T3 until next month :)

---

### Post by lian1238 on 2010-03-20
I just remembered that I manually installed Thunderbird 3. It was in /opt/thunderbird/thunderbird

The update somehow overwrote my symlink at /usr/bin/thunderbird and reverted the target to the old thunderbird. I changed the symlink and it's working once again. :D

---

### Post by bayvista on 2010-08-31
Had the same problem. Spent many frustrating hours trying to find all my Inbox stuff. Turned out to be something simple. The update had changed my View/Threads to 'Unread'. Once I switched back to 'All', my Inbox was restored.

As I can't afford to spend hours fixing bugs in flaky software, I have now switched to Gmail, which seems much more stable.

---

