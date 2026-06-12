---
title: "rc.local and backlight acer"
date: 2012-08-17
forum: General Help
---

### Post by duncanmaybury on 2012-08-17
Hello,
I have an acer aspire and recently updated 12.04. No Back light.
I have followed the steps here: [http://ubuntuforums.org/showthread.php?p=12174465#post12174465](http://ubuntuforums.org/showthread.php?p=12174465#post12174465) I added to he discussion, sorry if that was wrong, so I have started this thread.
With an external monitor plugged in I can see, so can execute :
sudo setpci -s 00:02.0 F4.B=00This allows me to see on the lapop screen.
When I modify the rc.local file as described, set it as executable and reboot I have no backlight, any ideas why the rc.local file is not doing its job?

---

