---
title: "after resume &quot;Disconnected - you are now offline&quot; notification doesn't disappear"
date: 2011-08-28
forum: General Help
---

### Post by Bazon on 2011-08-28
When I resume from standby, the "Disconnected - you are now offline" notification(*) *(which probably appeared when standby was started)* stays on the screen and doesn't go away until I close it manually. 
Network works, so in fact I'm online and the notification is false.

So how do I prevent that false notification from 
(a) appearing or
(b) not disappearing?

Notifications are set to disappear after 4 seconds, which the do, except this naughty one...

(*)
for me: "Verbindung getrennt - Sie sind nun offline"

---

### Post by jerrrys on 2011-08-28
one possibility

[http://ubuntuforums.org/showthread.php?t=1408202](http://ubuntuforums.org/showthread.php?t=1408202)

some other hits here

[http://ubuntuforums.org/showthread.php?t=1408202](http://ubuntuforums.org/showthread.php?t=1408202)

in the pass i have lived with this, but in the pass it was a clickable balloon.  not in 11o4, would like to know how remove it too, but got too many other things going on right now.  so maybe you can tell me what works...

---

### Post by Bazon on 2011-08-29
Thanks for the links, same problem indeed:

> **warp99 said:**
> Short answer, most likely no. But you can turn off the notifications for nm-applet by using the gconf-editor and under apps > nm-applet tick the box "disable-disconnected-notifications".

Setting /apps/nm-applet/disable-disconnected-notifications = TRUE didn't help either, even after a restart to be sure settings are effective. 
Maybe because Xubuntu uses not the gnome network manager?
Or settings made in gconf-tool aren't effective in xubuntu?

---

### Post by Bazon on 2011-08-30
up

are the xubuntu settings elsewhere then in gconf-tool?
the network-manager is clearly used...
(....but compiz in xubuntu has its own settings, too, e.g.)

---

### Post by Da_Coynul on 2011-10-27
One way to solve this problem would be to build network-manager-gnome (nm-applet) from source _without_ these two Ubuntu patches:

lp341684_device_sensitive_disconnect_notify.patch
lp358526_generic_disconnected_notification_icon.patch

Easy instructions for building Ubuntu packages from source can be found [**here**]("http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/").

BTW I am surprised more people have not complained about this bug.  I guess not many people use Xubuntu and those who do don't have the time or interest to look for bug fixes :confused:

Bug report here: [https://bugs.launchpad.net/ubuntu/+source/xfce4-notifyd/+bug/835972](https://bugs.launchpad.net/ubuntu/+source/xfce4-notifyd/+bug/835972)

---

