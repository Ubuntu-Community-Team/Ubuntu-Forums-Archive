---
title: "Seamless RDP off kilter when maximized"
date: 2011-07-18
forum: General Help
---

### Post by embolalia1187 on 2011-07-18
I'm going to jump right in here and assume you know about [SeamlessRDP]("http://www.cendio.com/seamlessrdp/"). I have the server plugin installed, and am using ```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\seamlessrdp\runp21.bat" -u DOMAIN\\User -p - 192.168.1.20
```to open a session. runp21.bat is a Windows batch file that says:
```
c:
cd \Program Files (x86)\Activant\Prophet 21 12.1\
pxxi.exe
logoff
```The net effect here is to run Prophet 21, a proprietary Windows-only ERP solution, over RDP, and logout when it closes. (This was recommended to me by a few sites, as rdesktop apparently doesn't handle logouts properly when it terminates.) Worth noting here, Epicor's support site has nary a mention of Linux, and their Mac support solution mainly says "we don't support Mac, but here's some general info to get you started." You don't really need to know the details of P21 except to know that, in operating it efficiently, one must frequently place the cursor over the farthest left edge of the screen.

When first opening the program, it takes up the vast majority of the screen, but is not maximized. There is apparently enough edge there that it won't recognize the edge of the monitor as the edge of its window. So, obviously, you maximize it. (Is there any way to tell a window to maximize in a batch file?)

When the window is maximized, Windows recognizes the mouse as being about half an inch lower than where the mouse shows up. See:
[IMG]http://img194.imageshack.us/img194/7556/screenshotuq.png[/IMG]
Additionally, the window refuses to recognize the lower gnome-panel, so the lower edge of the window is hidden by it.

rdesktop is compiled from latest release from rdesktop.org. Terminal output is:```
Autoselected keyboard map en-us
WARNING: Broken Window Manager: Timeout while waiting for ConfigureNotify
WARNING: Broken Window Manager: doesn't handle restack (window was moved to bottom)
WARNING: Remote desktop does not support colour depth 24; falling back to 16
WARNING: Broken Window Manager: Timeout while waiting for ConfigureNotify
WARNING: Broken Window Manager: Timeout while waiting for ConfigureNotify
WARNING: Broken Window Manager: Timeout while waiting for ConfigureNotify
WARNING: Broken Window Manager: Timeout while waiting for ConfigureNotify
WARNING: Broken Window Manager: Timeout while waiting for ConfigureNotify

```Using 10.04 (Lucid) with Gnome 2. Windows is Server 2008, and the whole thing is basically fresh out of the box. Right now, I'm the only one with a Linux client (that being my personal laptop) but we'd like to start moving over some of our XP boxes.

---

