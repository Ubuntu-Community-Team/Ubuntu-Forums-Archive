---
title: "Gmail in evolution/thunderbird broken"
date: 2009-10-17
forum: General Help
---

### Post by skawt on 2009-10-17
Hi Guys,

i've had evolution set up for Gmail for awhile now, and its worked just fine.  after my cable connection went down for a couple days, i have been unable to connect to gmail with evolution or thunderbird, it only works thru webpage.  i've removed each program and reinstalled a few times, (separately) no luck.  anything in particular i should be looking for?  account settings are correct for both. checked and rechecked.   i'm a little lost with this...:confused:

---

### Post by mac666 on 2009-10-17
I guess you use the proper setup with connecting to their servers?
[http://mail.google.com/support/bin/answer.py?hl=en&answer=13287](http://mail.google.com/support/bin/answer.py?hl=en&answer=13287)

And, my firewall / VPN blocks the custom ports gmail uses, so i have to turn the VPN off everytime i use evolution...
Check those stuff

---

### Post by skawt on 2009-10-17
hmm.  thanks for the quick reply.  it seems all the ports, settings, servers, etc are correct.  as for VPN, i don't know, i don't have anything listed under connections.  this problem occurs with or without firewall.  basically, the only thing that changed was my internet connection went down for two days.  when it came back, everything but evolution/thunderbird worked as normal.  its weird, it just keeps checking for mail until connection times out.

---

### Post by rampageoberon on 2009-10-17
Just to confirm, are you using POP3 or IMAP to access Gmail?

Also it might be good to try the whole setup on a new profile (thunderbird, never used evolution)

the below code will effectively backup the existing profile. When you start thunderbird again it will create a new profile.
```
mv .mozilla-thunderbird .mozilla-thunderbird-backup
```

The below code will restore the profile you backed up.
```
rm -r .mozilla-thunderbird
mv .mozilla-thunderbird-backup .mozilla-thunderbird
```

Hope this helps.

---

### Post by MarkEoz on 2009-10-21
Hi,
 
I've got a familiar problem..
 
Since today I can't download new emails to my evolution client, I can send emails but it won't show new emails. I can read them in gmail so there is no big problem but it's really weird since i havn't changed any preferences..
 
Help would be gladly appriciated!
 
Greetz,

---

### Post by skawt on 2009-10-24
all right.  this is getting weird.  i did a complete reinstall and the problem persists, tho it seems to have spread.  now the only things that can connect to the net are firefox, update manager, and boinc.  evolution, transmission, etc. are not connecting.  i don't get it.  no firewall running.  default settings all around.:mad:

---

### Post by skawt on 2009-10-24
okay.  here's how this got fixed.  i reset my Modem.  with the little pinhole reset button.  apparently i had jacked up a setting or two (probably ports) when i was screwing around with it.  let that be a lesson to you all  :P

---

