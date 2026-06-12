---
title: "Syslog Facility Control"
date: 2012-05-11
forum: General Help
---

### Post by mehetmet on 2012-05-11
Hello, 

I am currently running Ubuntu 12.04 on a server I am using to collect all of our syslog data.  Currently we are using SNARE to forward data from our Windows Servers, and our Linux Servers (RHEL v6.1 and Fedora 16) are just sending the logs across the network using the syslog remote configuration.

Now, when setting up SNARE, I was able to select what Facility the messages were sent as, i.e. I selected say, Local2 for our development servers and Local5 for our production.  This is to log all of our servers in a central location but keep our prod and dev servers separate.

My problem comes in when sending the logs from the other 2 Linux machines.  The logs get sent and received fine, but only come into the /var/log/syslog and /var/log/messages files.  Is there a way to set the messages from the Linux machines (either when sent or when received) to have a different Facility then whatever their default is?

---

