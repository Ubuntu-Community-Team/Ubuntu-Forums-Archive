---
title: "Postfix issue"
date: 2009-07-08
forum: General Help
---

### Post by craigjw on 2009-07-08
I am new to Postfix and trying to get configure the smtpd_recipient_restrictions section of main.cf

If I have:
smtpd_recipient_restrictions = reject_rbl_client = bl.spamcop.net, permit_mynetworks
then I cannot connect to port 25 on the server, i.e. it connects but I do not get the SMTP banner.

If I comment it out it works.

Can someone help me to understand what is going on.

Thanks,
Craig

---

### Post by gareththered on 2009-07-08
Have you set the 'mynetworks' options in main.cf so that it includes your network?

---

### Post by craigjw on 2009-07-08
Hi - yes, its set to:
 
mynetworks = 10.0.0.0/8

which includes my IP of 10.200.5.44

---

### Post by gareththered on 2009-07-08
When you said you commented it out, did you mean the whole line/statement or just the 'permit_mynetworks' statement?

Is there anything in /var/log/mail.log?

---

### Post by craigjw on 2009-07-08
Hi - no, I commented out the:

smtpd_recipient_restrictions = reject_rbl_client = 
bl.spamcop.net, permit_mynetworks

line.

---

### Post by gareththered on 2009-07-08
May I suggest you remove one statement at a time so you know which of the two options is causing the issue?  Also, try changing the order around so that 'permit_mynetworks' comes first.

---

### Post by craigjw on 2009-07-08
I changed it to:
smtpd_recipient_restrictions = permit_mynetworks, reject_rbl_client = bl.spamcop.nets

and it didnt work.

I then changed to:

smtpd_recipient_restrictions = permit_mynetworks

and it didnt work.

I then comment the entire smtpd_recipient_restrictions line out and it works.

---

### Post by craigjw on 2009-07-08
I do see this in the logs:

fatal: parameter "smtpd_recipient_restrictions": specify at least one working instance of: check_relay_domains, reject_unauth_destination, reject, defer or defer_if_permit

---

### Post by gareththered on 2009-07-08
So we've narrowed it down to the 'permit_mynetworks' setting!

Where are you connecting to the server from?  Is that from the IP address you previously posted?  

Try:-
```
grep reject: /var/log/mail.log
```
and see if you can find anything interesting in there about why your connection is being rejected.

Try:-
```
postconf -d | grep "mynetworks ="
```
and make sure the IP address your addresses are OK.  Mine includes the 127.0.0.0/8 and my external IP.

Finally, here's the relevant part of my config:-
```
smtpd_recipient_restrictions = 
   reject_unauth_pipelining,
   reject_non_fqdn_recipient,
   reject_unknown_recipient_domain,
   permit_mynetworks,
   permit_sasl_authenticated,
   reject_unauth_destination,
   check_sender_access
      hash:/etc/postfix/sender_access,
   check_recipient_access
      hash:/etc/postfix/recipient_access,
   reject_rbl_client zen.spamhaus.org
   permit
```
If you decide to try the above config, then don't copy the two 'check_' lines (and their associated 'hash:' lines) otherwise you'll have to create the two hash files for them.

---

### Post by gareththered on 2009-07-08
> **craigjw said:**
> I do see this in the logs:

fatal: parameter "smtpd_recipient_restrictions": specify at least one working instance of: check_relay_domains, reject_unauth_destination, reject, defer or defer_if_permit
That's also in the man page for postconf(5).  Strange that they are not in my config, but that works!  Now I'm starting to worry and wish I hadn't replied to this thread ;-)

---

### Post by craigjw on 2009-07-08
Yes that worked for me.

Next problem though:

the relay_domains field doesnt seem to work!

I have relay_domains = mydomain.com

I can still use the SMTP server to send to other domains.

---

### Post by gareththered on 2009-07-09
I'm afraid I don't have 'relay_domains' in my setup.  I use 'mydestination' which becomes the default value for 'relay_domains' if none is specified.

Sorry for the slow reply, but I was away last night which gave me time to think, and I'm not certain that my setup is working properly.  The last line is 'permit'.  This means that if all other lines have been tried and don't match, then Postfix will allow the email through.  In other words, it will only reject a mail if one of the 'reject_' options is true.

Your config has only two options, so if they fail your mail will be rejected (as you don't have the final 'permit').

In my opinion, neither of our systems has a working 'permit_mynetworks'.  I got away with it due to the final 'permit'. I will need to investigate a little more.....

---

