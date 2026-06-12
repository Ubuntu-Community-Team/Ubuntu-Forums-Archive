---
title: "postfix to forward emails"
date: 2010-09-16
forum: General Help
---

### Post by cwscribner on 2010-09-16
Hi all.

I have a 9.04 box doing Nagios monitoring for a client.  They want to forward the notifications from Nagios to their exchange server to avoid accidental spam detections from their IronPort appliance.  How do I tell postfix "send mail to xxx.xxx.xxx.xxx"?

---

### Post by cwscribner on 2010-09-20
Nobody?  I wouldn't think this would be that hard.  I just don't know where to find what I need.  Don't I need to do something with MX records?

---

### Post by cwscribner on 2010-09-23
So I'm thinking maybe postfix doesn't do this, but iptables does?  Can I append a rule that forwards port 25(smtp) to another IP address?

---

