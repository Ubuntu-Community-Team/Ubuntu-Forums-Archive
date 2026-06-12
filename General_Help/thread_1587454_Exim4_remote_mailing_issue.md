---
title: "Exim4 remote mailing issue"
date: 2010-10-03
forum: General Help
---

### Post by JackintheMox on 2010-10-03
I'm having issues with getting remote mailing to work w/ exim4.  I tried checking old searches for solutions to no avail.  Basically, I installed LFD and CSF and am trying to use exim to remotely forward alerts to my personal email.  I set-up exim4 in hopes of sending the alerts but have run into an issue.  I also turned off CSF to ensure that traffic could successfully get out although my configuration should be fine to let outbound 110 traffic go.

Anyway, here's the issue:

tail -10 /var/log/exim4/mainlog:
2010-10-03 15:16:34 1P2THR-0003kV-Of == <personal_email_address@yahoo.com> R=dnslookup_relay_to_domains T=remote_smtp defer (-53): retry time not reached for any host
...

I've tried sending messages via command line to no avail.  It appears there's a problem with DNS lookups for yahoo.com but I can nslookup/dig with no problem.  Exim is set-up for remote forwarding.

Here are my settings:
dpkg-reconfigure exim4-config

internet site; mail is sent and received directly using SMTP
system mail name: <my_domain>
Exim SMTP incoming IP: <my_public_IP>; ::1
Recipient domains for final dest: <my_domain>
Recipient domains for relay: yahoo.com; gmail.com
Smarthost unconditional relay: ""
Dial-on-demand: no
location of incoming mail/config should be irrelevant
root and postmaster mail receipt: ""

If I'm missing something obvious or if anyone has experience with this, I'd appreciate it.  Never set-up a mail MTA before.

Thanks!

---

### Post by btindie on 2010-10-03
Ok, so you're trying to send your email directly to the destination without using a smtp relay/smarthost? I assume you're running this from home??
 
First thing install ngrep ```
sudo apt-get install ngrep
```
Then open another terminal and run ```
sudo ngrep -d wlan0 -qttl -W byline port 25
```
changing *wlan0* to your interface name.
 
Then try sending a test email again from the terminal and watch the ngrep output.
 
I think you may get something like
> 553 Mail from 81.129.??.?? not allowed - 5.7.1 [BL21] Connections not accepted from IP addresses on Spamhaus PBL; see [http://postmaster.yahoo.com/errors/550-bl21.html](http://postmaster.yahoo.com/errors/550-bl21.html) [550]
 
Which basically means they don't allow direct connections from clients, those which are on dynamic IP addresses. This is one measure to reduce spam.
 
To get around that you need to configure exim to use an smtp relay or smarthost, this would be your ISP's smtp server. Exim would then send all outbound email to your ISP's smtp server which would then deliver it to it's destination.

---

