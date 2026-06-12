---
title: "Share Wi-Fi Connection"
date: 2011-08-25
forum: General Help
---

### Post by 888vvv888 on 2011-08-25
I would like to share my main internet connection[a MAC-blocking WiFi hotspot] with my other devices[2 tablets and a cell phone] by WiFi as well on Ubuntu 10.10. What steps do i need to take?
[Unfortunately the owner has a limited number of MAC slots and these are all filled at the moment]
Thank you

---

### Post by seawolf167 on 2011-08-25
Take a look at [this page ]("https://help.ubuntu.com/community/Internet/ConnectionSharing")for instructions.

---

### Post by 888vvv888 on 2011-08-25
Thank you.
As always, the solution is simpler than you may initially assume. :guitar:

---

### Post by seawolf167 on 2011-08-25
Glad it works for you! If this is all solved, please mark the thread as such under "Thread Tools" -> "Mark as Solved"

---

### Post by 888vvv888 on 2011-08-25
> **seawolf167 said:**
> Glad it works for you! If this is all solved, please mark the thread as such under "Thread Tools" -> "Mark as Solved"

It seems i was overjoyed too early.
The tutorial i followed seems to assume i am receiving the connection through LAN and want to share it through WiFi. I am connected however by WiFi and would like to share through WiFi.
Possible or not?
Thank you once again

---

### Post by seawolf167 on 2011-08-25
As far as I know you cannot share an internet connection on the same device/port that you are receiving an internet connection through, though I could be proven wrong here.

If it is a MAC address *blocking *setup, the owner should only be blocking specific MAC addresses, and you should be able to have the gateway (assuming it is the DHCP server) hand out addresses until it's address range is taken. 

If it is a MAC address *allowing *setup, the owner should only be allowing specific MAC addresses, in this case, can you simply have them add additional devices?

---

