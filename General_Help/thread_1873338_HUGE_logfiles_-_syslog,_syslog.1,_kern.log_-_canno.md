---
title: "HUGE logfiles - syslog, syslog.1, kern.log - cannot log in to desktop"
date: 2011-11-01
forum: General Help
---

### Post by Closrapexa on 2011-11-01
Sometimes, not always, after reboot I cannot log in to the desktop and all I get is a blank screen that says, among other things "sane disabled." I previously had a problem with logfiles syslog, syslog.1 and kern.log inflating to horribles sizes, 3 or 4 gigs. 

When this happens, I need to remove all three files, and then I can reboot and log in normally. logrotate is installed by default, but I guess it's not doing what it is supposed to. I didn't see anything special when I looked in the logfiles, no reason for them to grow that big. 

Does anyone know what is happening

---

### Post by 2F4U on 2011-11-01
Since logrotate is supposed to clean up things on a regular basis, my guess would be that something is causing that increase within a very short time. Did you look into the log files to determine what exactly was logged there? Extensive logging usually points to a more serious problem.

---

### Post by JoeDesertrat on 2011-11-01
I am having the same issue. The syslog and kern.log are filling up to GB's in size repeating with thousands of: 
[drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times

Logrotate is working, I end up with massive files for each day. I have to delete several days worth as my hard drive fills up.

---

### Post by Closrapexa on 2011-11-01
I don't see even that recurring line, just lots and lots and LOTS of everything. I never had this problem with any other version (I've used only Ubuntu), only since installing Xubuntu a week ago.

---

### Post by 2F4U on 2011-11-01
Logrotate, in its default configuration on my machine, only rotates the log files weekly and keeps 4 weeks worth of backlogs. If your logs are filling up so quickly, you should probably adjust these settings in 

/etc/logrotate.conf

There is also an option to compress log files, which is deactivated per default.

---

### Post by Closrapexa on 2011-11-04
I didn't quit know what to change in the logrotate file except to enable the compression, which seems to have solved the problem. thanks!

---

### Post by SparTacux on 2011-11-04
You've not got GUFW enabled with full logging set by any chance? That would write **** loads of data to those files if you use your browser a lot.

---

### Post by Closrapexa on 2011-11-04
A firewall? No I don't have that. In the logrotate file, where it says "weekly" can I change it do daily so it'll rotate them every day? Is that how it works?

---

### Post by gsmanners on 2011-11-04
Sounds familiar... Maybe it's something like this: [http://ubuntuforums.org/showthread.php?t=1864914](http://ubuntuforums.org/showthread.php?t=1864914)

---

