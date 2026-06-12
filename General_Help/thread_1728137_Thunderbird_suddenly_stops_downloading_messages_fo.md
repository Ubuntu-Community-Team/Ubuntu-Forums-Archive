---
title: "Thunderbird suddenly stops downloading messages for an account"
date: 2011-04-13
forum: General Help
---

### Post by Zorrothustra on 2011-04-13
(Ubuntu LTS 10.4) I have multiple mail accounts on Thunderbird (TB). All worked fine with no issues whatsoever. A few months ago it suddenly started giving me this alert message related to my yahoo.fr pop3 account

> The POP3 mail server (pop.mail.yahoo.fr) does not support UIDL or XTND XLST, which are required to implement the ``Leave on Server'', ``Maximum Message Size'' or ``Fetch Headers Only'' options. To download your mail, turn off these options in the Server Settings for your mail server in the Account Settings window.

Obviously I checked if these settings were somehow changed. They weren't. It should leave messages on the server indeed, but I don't use no max message size or fetch headers only options. The original settings are what they used to be and how they have always worked. 

The thing is: everything works normal if I start up TB. It downloads the messages, puts them in the folders where I want them to come etc... The problem seems to appear after a while (mostly a few hours, or overnight). It just stops downloading the messages from my yahoo.fr account. When I click the Get Mail for my yahoo account the above alert message pops up. 

There is only one solution really. Close TB and restart it after which all works fine again. 

It might be that the problem is related to another issue reported as [bug # 689453 in launchpad]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/689453") that started around the same time (a few months ago). That bug forces me to have to end the process through the System Monitor where Thunderbird-bin uses almost 100% of the CPU and doesn't shut down.

Obviously it doesn't avoid me from using TB, but it starts to work on my nerves to have to close down TB (sometimes through the End Process in system monitor) and then restart it so frequently.

---

### Post by SeijiSensei on 2011-04-13
Try turning off "leave mail on server" and see if that helps.  If IMAP is an option, I'd choose that over POP all that time.

You may see a flood of old mail the first time you connect after turning this off.  You might want to create a local folder in TBird and move the contents of your inbox there before connecting.

---

### Post by Zorrothustra on 2011-05-31
Thanks for the suggestion. However, with the slow connection I have (max 30Kb) imap is not an option. And I'dd really prefer keeping my messages on the server and deleting them manually. 

So I lived with the problem and sort of started to get used to it, even thought it still bothers me. 

Just did a fresh install last week of 11.04, but the issue is still there... Obviously, the settings from the old installation are imported through the backup from the /.thunderbird folder. 

Damn, I had somehow hoped Natty could help me out...

---

### Post by alxobr on 2012-05-04
Hi all,

Some fresh news about this strange bug.

Two yahoo.fr POP3 accounts are configured on my TB 12.01  X11, and one of them has stopped downloading mail a few days ago giving  the above mentioned message. The other yahoo.fr POP3 account (which has  less volume I must say) still works normally on TB. The messages on the  first account however can be seen using web mail and can even be  downloaded using Opera mail, so I begin to suspect this might be a TB  issue. I use "Leave messages on server" on both accounts and both  clients.

Cheers,

Alexandre

---

### Post by Zorrothustra on 2012-05-04
I won't cry it out too loud (afraid I might wake up the bug), but so far everything seems to be working fine with TB in Ubuntu 12.04 (clean install).
I had occasional problems in Ubuntu 11.10 where TB sometimes repeatedly downloaded same message over and over again from that yahoo account, that problem is described here: [http://kb.mozillazine.org/Duplicate_messages_received](http://kb.mozillazine.org/Duplicate_messages_received).

---

### Post by alxobr on 2012-05-08
> **Zorrothustra said:**
> I won't cry it out too loud (afraid I might wake up the bug), but so far everything seems to be working fine with TB in Ubuntu 12.04 (clean install).

This is just to whisper that today all messages are getting downloaded normally again ;-). 

Cheers,

Alexandre

---

