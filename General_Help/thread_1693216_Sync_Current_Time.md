---
title: "Sync Current Time"
date: 2011-02-22
forum: General Help
---

### Post by Flyers2391 on 2011-02-22
My laptop's time has been off a few minutes recently and I've found that I could go into the terminal and run ntpdate ntp.ubuntu.com, which I've done, but shouldn't there be a way to do this in the GUI, as there apparently used to be?  It appears that the instructions from here: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime) are outdated.  

Attached is what I get with 9.10, I'll check with 10.04 LTS on my desktop when I'm on that to see if it is different.  In the mean time, I was hoping someone might know if it was a removed feature or what the deal is.

---

### Post by wt8008 on 2011-02-26
Follow Steps 1 through 5 in the wiki to allow the system to automatically install the package for automatic ntp syncing.

[https://help.ubuntu.com/community/UbuntuTime#Time%20Synchronization%20using%20NTP](https://help.ubuntu.com/community/UbuntuTime#Time%20Synchronization%20using%20NTP)

After you install it you should see a file `ntp' located in the /etc/cron.daily/ folder, so it should automatically update once a day.

---

### Post by Flyers2391 on 2011-03-01
Thanks for the reply, however, at Step 2, there is no "Synchronize Now" button.  I was hoping there was a way in the GUI so I can help other ubuntu users I know and not scare them with a terminal window.

---

