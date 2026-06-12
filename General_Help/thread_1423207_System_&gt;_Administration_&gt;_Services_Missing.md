---
title: "System &gt; Administration &gt; Services Missing"
date: 2010-03-06
forum: General Help
---

### Post by brvaland on 2010-03-06
Hi Experts

I'm newbie to Ubuntu, I have found that under System > Administration > Services options is missing. Also Networking option is missing.

The Ubuntu Version : Ubuntu 9.10  - the Karmic Koala - released in October 2009

Can you please advise, what is missing on my OS Version?

Kind Regards
Bhavesh

---

### Post by fragos on 2010-03-06
Try System-> Preferences-> Startup Applications for Services. For Networking, right click the Network applet icon and select Edit Connections...

---

### Post by brvaland on 2010-03-07
Thanks for your reply.

I don't have "startup application for services", but do have "startup application" unable to locate networking under startup application.

Please advise?

Kind Regards
Bhavesh

---

### Post by fragos on 2010-03-07
For Networking don''t look in Startup Applications as that only loads "Network Manager". To perform "networking" aka network configuration, look in the upper applet bar and find the network manager icon which is a connected symbol for wired or a set of bars for wireless. Hovering over it will tell you what network connection you have. Right clicking it gives a drop down menu which includes a check box for "Enable_networking" and a selection for "edit Configuration".

---

### Post by brvaland on 2010-03-07
Thanks 

I have managed to locate the networking and found "edit configuration" option.

How can I change the host-name of the computer?

Please advise?

Kind Regards
Bhavesh

---

### Post by fragos on 2010-03-07
Your host name is in /etc/hostname which requires admin privileges to edit. Type "Alt-F2" and the "gksudo gedit /etc/hostname" and you can change it.

---

### Post by brvaland on 2010-03-07
Thanks.

Resolved.

---

