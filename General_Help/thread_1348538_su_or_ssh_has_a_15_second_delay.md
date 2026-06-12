---
title: "su or ssh has a 15 second delay"
date: 2009-12-07
forum: General Help
---

### Post by allankelly on 2009-12-07
Hi, I have a stable long-term ubuntu server 'rss_rand'. However I have a consistent and lengthy delay (around 15 seconds) when doing 'ssh rss_rand' or when on the rss_rand command line 'su - akelly'. As a number of our development scripts run remote commands via ssh, this is a real pain.

Using the -vvv flag to ssh shows the delay at 'debug1: Entering interactive session.', following fast publickey authentication.

Just in case, I tried the /etc/ssh/ssh_config setting 'GSSAPIAuthentication no' on client and server as documented in various places, also /etc/nsswitch.conf 'hosts: files dns' on the server but this hasn't helped.

There's no indication of a delay or timeout in /var/log/auth.log

Is there a way to debug the login process to see what the delay is?

Cheers, al.

---

