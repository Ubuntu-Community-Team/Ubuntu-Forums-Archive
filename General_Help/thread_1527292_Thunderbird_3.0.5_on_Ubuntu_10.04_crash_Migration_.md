---
title: "Thunderbird 3.0.5 on Ubuntu 10.04 crash: Migration from Thunderbird to Evolution"
date: 2010-07-09
forum: General Help
---

### Post by roland_j on 2010-07-09
Hi,

my problem is probably not a Ubuntu-problem, but maybe someone share my experience and can help: Recently,I  upgraded my system to Ubuntu 10.04. Thunderbird was also upgraded to 3.0.5. The first time when I started Thunderbird it took some time because of indexing I think (I have 4 GB of mails in my folders). After this it worked fine for two weeks or so, but now it crashes: After start-up Thunderbird comes up with a message "Loading message" in the status bar. Then it "works" for about five minutes (freeze) and crash without a message.

The old version worked fine. I have no ides what they've done to this program. I will now remove Thunderbird from my system now and look for alternatives. Do you have any recommendation? I tried Evolution which seems to work fine. Can I import all my Thunderbird-account in evolution? 
I found the following hint: "Copy everything from ~/.mozilla-thunderbird/xyz.default/Mail into ~/.evolution/mail/local/Inbox.sbd". Is this the only way? How about my accout date (login, server address etc.)?

Regards
Roland

---

### Post by philinux on 2010-07-09
First off lets get TB running. There does seem to be a problem with the upgrade. I think it's affecting people with large email database. 4gig wow.

Anyway open synaptic package manager.

Highlight thunderbird in the list.

Click on the versions tab.

Highlight version 3.0.4 then click Package>Force Version.

That should get thunderbird running.

[TB to Evolution]("http://www.google.com/search?q=linux+migrate+thunderbird+to+evolution&hl=en&tbo=1&output=search&source=lnt&tbs=qdr:y&sa=X&ei=nvA2TLGzDpSy0gTZ47DiAw&ved=0CAgQpwU")

---

### Post by roland_j on 2010-07-09
Hi,

thank you. That solved the problem (at least temporarily), but I still don't understand what is wrong with Thunderbird. I think it may be better to switch to a different mail client.

Regards
Roland

---

