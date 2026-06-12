---
title: "Ubuntu 10.04, Exim4, 10 mail limit?"
date: 2010-11-10
forum: General Help
---

### Post by dkirkdrei on 2010-11-10
I am running Exim4 on Ubuntu 10.04, using it for sending emails out from various programs on our LAN. I have program that sends out approx. 60 emails once a month and Exim's default setting of only sending out 10 emails prior to the remaining being queued is causing an inconvenience in this case. In the Exim log files, I receive a notification of: "no immediate delivery: more than 10 messages received in one connection". I have scoured the internet but have not found a fix. I have added this line: smtp_accept_queue_per_connection=100 to /etc/exim4/update-exim4.conf.conf and restarted Exim but this does nothing. I have also tried smtp_accept_queue_per_connection=0 but this does not accomplish anything either. Can anyone shed some light on what setting needs to be changed to allow more than 10 emails to be sent at one time? Thanks.

---

