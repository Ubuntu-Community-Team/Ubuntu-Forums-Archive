---
title: "Why does my pidgin/yahoo keeps on disconnecting."
date: 2010-01-12
forum: General Help
---

### Post by Inhumanity on 2010-01-12
Damn, I'm getting frustrated with ubuntu. First my ubuntu randomly log out to GDM, second my pidgin(yahoo) keeps on exiting.

any input guys?

---

### Post by Inhumanity on 2010-01-12
bump

---

### Post by amsterdamharu on 2010-01-12
What does the debug window say?

Help => debug window

---

### Post by Inhumanity on 2010-01-12
```
(18:35:19) prefs: /pidgin/debug/width changed, scheduling save.
(18:35:24) util: Writing file prefs.xml to directory /home/francis/.purple
(18:35:24) util: Writing file /home/francis/.purple/prefs.xml
(18:35:33) prefs: /pidgin/debug/filterlevel changed, scheduling save.
(18:35:34) prefs: /pidgin/debug/filterlevel changed, scheduling save.
(18:35:36) prefs: /pidgin/debug/filterlevel changed, scheduling save.
(18:35:38) util: Writing file prefs.xml to directory /home/francis/.purple
(18:35:38) util: Writing file /home/francis/.purple/prefs.xml
(18:36:19) yahoo: 129 bytes to read, rxlen is 149
(18:36:19) yahoo: Yahoo Service: 0xc6 Status: 1
(18:36:19) yahoo: Unknown status key 187
(18:36:19) yahoo: Unknown status key 317
(18:36:19) blist: Updating buddy status for queenbee_bkchiq (Yahoo)
(18:36:19) yahoo: 129 bytes to read, rxlen is 149
(18:36:19) yahoo: Yahoo Service: 0xc6 Status: 1
(18:36:19) yahoo: Unknown status key 187
(18:36:19) yahoo: Unknown status key 317
(18:36:19) blist: Updating buddy status for queenbee_bkchiq (Yahoo)
(18:36:34) yahoo: 163 bytes to read, rxlen is 183
(18:36:34) yahoo: Yahoo Service: 0xf0 Status: 1
(18:36:34) yahoo: Unknown status key 302
(18:36:34) yahoo: Unknown status key 300
(18:36:34) yahoo: Unknown status key 198
(18:36:34) yahoo: Unknown status key 213
(18:36:34) yahoo: Unknown status key 283
(18:36:34) yahoo: Unknown status key 317
(18:36:34) yahoo: Unknown status key 300
(18:36:34) yahoo: Unknown status key 440
(18:36:34) yahoo: Unknown status key 301
(18:36:34) yahoo: Unknown status key 301
(18:36:34) yahoo: Unknown status key 303
(18:36:34) blist: Updating buddy status for reekolagrimas (Yahoo)
(18:36:34) nautilus: saved blist online
(18:36:34) pidgin-libnotify: notify(), new: title: 'Reeko Lagrimas', body: 'is online', buddy: 'Reeko Lagrimas'
(18:36:34) pidgin-libnotify: notify(), has a prpl icon.
(18:36:34) cap: Executing: insert into cap_status (buddy, account, protocol, status, event_time) values(reekolagrimas, aprikanongputi, prpl-yahoo, available, now());
(18:36:35) yahoo: 45 bytes to read, rxlen is 65
(18:36:35) yahoo: Yahoo Service: 0xbe Status: 1
(18:36:38) yahoo: 149 bytes to read, rxlen is 169
(18:36:38) yahoo: Yahoo Service: 0xeb Status: 1
(18:36:38) yahoo: Unhandled service 0xeb
(18:36:39) util: Writing file blist.xml to directory /home/francis/.purple
(18:36:39) util: Writing file /home/francis/.purple/blist.xml
(18:36:43) yahoo: 154 bytes to read, rxlen is 174
(18:36:43) yahoo: Yahoo Service: 0xbe Status: 1
(18:36:43) yahoo: 102 bytes to read, rxlen is 122
(18:36:43) yahoo: Yahoo Service: 0x4f Status: 1
(18:36:43) yahoo: Got P2P service packet (from server): who = reekolagrimas, ip = 3795372912
(18:36:43) yahoo: IP : 255.255.255.127
(18:36:43) dns: DNS query for '255.255.255.127' queued
(18:36:43) dnsquery: IP resolved for 255.255.255.127
(18:36:43) proxy: Attempting connection to 255.255.255.127
(18:36:43) proxy: Connecting to 255.255.255.127:5101 with no proxy
(18:36:43) proxy: Connection in progress
(18:36:44) yahoo: 63 bytes to read, rxlen is 83
(18:36:44) yahoo: Yahoo Service: 0x4b Status: 1
(18:36:44) psychic: no previous conversation exists
(18:36:44) evolution: Error retrieving addressbook: EBookStatus returned 8
(18:36:44) evolution: Error retrieving addressbook: EBookStatus returned 8
(18:36:44) evolution: Error retrieving addressbook: EBookStatus returned 8
(18:36:44) evolution: Error retrieving addressbook: EBookStatus returned 8
(18:36:44) prefs: /pidgin/conversations/toolbar/wide changed, scheduling save.
(18:36:44) prefs: purple_prefs_get_bool: Unknown pref /plugins/core/psychic/raise_conv
```

---

### Post by amsterdamharu on 2010-01-12
I remember having some problems with Pidgin and needed to get the latest version from pidgin (not ubuntu)
Can you try getting the latest version?:

[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

---

### Post by pricetech on 2010-01-12
Just follow the instructions on the Pidgin website to add them to your list of sources and the updates should occur automatically.

This may not be your problem, but it fixed mine and has fixed others plus it's easy to implement.

---

