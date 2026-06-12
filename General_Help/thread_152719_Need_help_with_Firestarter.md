---
title: "Need help with Firestarter"
date: 2006-03-30
forum: General Help
---

### Post by LucasLinard on 2006-03-30
I've Installed Firestarted and It is displaying at the events tab a big number of events  from my IP. WHat is this? I'll post one of them here. Can anyone explain me this???

Time: Mar 30 13:00:40 Source: xxx.xx.x.xxx (my IP) Destination: 239.255.255.250 In IF: eth0 Out IF:  Port: 1900 Length: 129 ToS: 0x00 Protocol: UDP Service: SSDP

What does it mean????

Thanks:confused:

---

### Post by chocolatetoothpaste on 2006-03-30
[QUOTE=LucasLinard]I've Installed Firestarted and It is displaying at the events tab a big number of events  from my IP. WHat is this? I'll post one of them here. Can anyone explain me this???
[/QUOTE]
Do you mean under the events tab?  Like when your icon turns into a lightning bolt?

---

### Post by graigsmith on 2006-03-30
It means it blocked a request.  Port 1900 is windows messenger requests.

So if you were on windows without the firewall enabled you would have probably received an advertisement pumped out right on a popup.  this would have been harmless to your system, and it wouldn't have done anything if you had your firewall off.  but the firewall blocked it, so there's nothing to worry about.

---

### Post by LucasLinard on 2006-03-30
[QUOTE=chocolatetoothpaste]Do you mean under the events tab?  Like when your icon turns into a lightning bolt?[/QUOTE]
Yeah
The icon is a blue > . Then just after I minimize it to the tray i becomes a red bolt.
there are a LOT of events under the events tab. Everything (every programs) seems to be ok (with regards to internet conection). But I keep getting a LOT of events like this one under the events tab (blocked connections)
Time: Mar 30 14:00:41 Source: XXX.XX.X.XXX Destination: 239.255.255.250 In IF: eth0 Out IF:  Port: 1900 Length: 129 ToS: 0x00 Protocol: UDP Service: SSDP

Can you explaion me what is this event??

---

### Post by LucasLinard on 2006-03-30
Thanks to you both chocolatetoothpaste and graigsmith.
I was wondering if it was something to worry about!
Thanks a lot.

---

