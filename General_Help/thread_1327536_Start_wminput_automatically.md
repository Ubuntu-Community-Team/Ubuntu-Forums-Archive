---
title: "Start wminput automatically"
date: 2009-11-15
forum: General Help
---

### Post by davbeck on 2009-11-15
I am trying to start wminput automatically when the system starts but the problem is that it requires root privileges. How can I either eliminate the need for super user or, automatically start something that requires it?

I read here: [http://antrix.net/journal/techtalk/boxee_wiimote.comments](http://antrix.net/journal/techtalk/boxee_wiimote.comments) to create a udev rule, but following his instructions did not work.

---

### Post by greyfox1 on 2009-12-23
I got this working in Karmic by doing the following after confirming that it worked using gksudo once I had followed [this tutorial]("http://ubuntuforums.org/showthread.php?t=993376&highlight=udev"):

1. I created the file: /etc/udev/rules.d/80-wminput.rules. This file contains only the text:
```
KERNEL=="uinput", MODE="0666"
```

2. At this point, I confirmed that I could get my wiimote working without root privileges by opening a Terminal and issuing the command:

```
wminput -c ir_ptr [wiimote MAC address]
```


3. Once I knew I could get this working without root privileges, I went to System->Preferences->Startup Applications and created a new item with the command I confirmed was working in Terminal in step 2 above. Wminput now starts when I log in, which is perfect since I use XBMC on this particular machine. The only tricky part is you have to press 1+2 on the wiimote at the right time, or else wminput won't grab it.

NOTE: There are various instructions out there, including the one you linked to, that recommend configuring the file in step 1 by user group rather than by mode 0666. I tried and tried but couldn't get it working using the group method. Try this at your own risk as the "mode" method is slightly less secure, but at least it works. HTH!

---

