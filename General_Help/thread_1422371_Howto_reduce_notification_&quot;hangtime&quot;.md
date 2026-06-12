---
title: "Howto reduce notification &quot;hangtime&quot;?"
date: 2010-03-05
forum: General Help
---

### Post by sgage on 2010-03-05
Is there an easy way to reduce the length of time that notifications appear? The 10-second default seems over long, especially since there's no way to dismiss the notification.

TIA

---

### Post by sgage on 2010-03-05
Surely there is a way to do this, yes?

---

### Post by falconindy on 2010-03-05
Just dealt with this recently. There is **no way** short of patching notify-osd to accomplish this. The specification defines that it will not honor the -t flag of notify-send. Canonical considers this a feature, not a bug.

[This](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/390508) is one such bug report.

And more...
[https://bugs.launchpad.net/notify-osd/+bug/490065](https://bugs.launchpad.net/notify-osd/+bug/490065)
[https://bugs.launchpad.net/debian/+bug/423314](https://bugs.launchpad.net/debian/+bug/423314)

---

### Post by sgage on 2010-03-05
Thanks falconindy.

I can't believe it. I find the notifications hanging there for 10 seconds to be rather distracting. I'd be happy with 4 seconds. Oh well, too bad for me!

---

### Post by i_am_nitrogen on 2010-03-10
Try using service-discovery-applet.  If any host on the network is rebooted, it delivers an individual notification for each service running on that host.  Better yet, try changing the hostname a couple of times within 10 seconds.  You'll be getting spammed with notifications for the next 5 minutes.  Clicking, hovering, and psychotic mouse wiggling just make the notification stay longer.  Why won't they just let us dismiss a notification?

---

