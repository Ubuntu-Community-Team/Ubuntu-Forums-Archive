---
title: "No UPnP message after MySQL update"
date: 2010-07-26
forum: General Help
---

### Post by rafe101 on 2010-07-26
I just ran some system updates today. MySQL was among them. after rebooting. I got a message I haven't seen since I was first installing several months ago. I couldn't connect to the database.

At first, I freaked out because I didn't know what to do. I tried checking my passwords, but I still don't understand all the configuration for MySQL. I tried reconfiguring the myth packages, but couldn't get through the setup. It would just bounce me out after a few attempts because of incorrect password sets.

I finally figured out, from the logs, that MySQL hadn't logged anything since it's 'successful shutdown' after the updates. It hadn't even tried to come on. I started it manually and everything seems to be fine, but how do I get it to start at startup again?

The mythbox is running 10.04.

---

### Post by rafe101 on 2010-07-27
I just tried a suggestion I found to change the start condition in /etc/init/mysql.conf to "start on (net-device-up IFACE=ethX)", in my case, eth0. That didn't help.

---

### Post by rafe101 on 2010-07-27
As per the suggestion on [this thread]("http://ubuntuforums.org/showthread.php?p=9643316#post9643316"), I added the command to start mysql to the rc.local file and it starts now.

What I don't know is if this was caused by an update and it gets corrected will calling the service twice cause problems? I suppose if I do get any I'll have to remember to remove that command.

---

### Post by rafe101 on 2010-08-26
Just adding an update--I had some mysql updates the other day and just commented out the line in the rc.local file and mysql still starts up. So the issue I was having appears to be fixed.

---

