---
title: "airmon-ng"
date: 2009-11-02
forum: General Help
---

### Post by nicklausmichael on 2009-11-02
Trying to run airmon-ng and running into some problems with it not working... this pops up immediately after entering command....in addition I do have NetworkManager for wireless network unchecked and still get this problem
Any suggestions or advice is greatly appreciated.

```
c0ld@c0ld-laptop:~$ sudo airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
832    avahi-daemon
833    avahi-daemon
1308    NetworkManager
1551    wpa_supplicant
1552    dhclient


Interface    Chipset        Driver

wlan0        Atheros     ath5k - [phy0]
                (monitor mode enabled on mon2)
mon0        Atheros     ath5k - [phy0]
mon1        Atheros     ath5k - [phy0]

```ID LIKE TO ADD EVEN USING JUST A NORMAL SITE SURVEY TOOL LIKE MY CARD IS NOT DISPLAYING ANY WIRLLESS NETWORKS AVAILABLE...In regards Im trying to use airodump-ng to see networks cause the other network survey program ubuntu has isnt working either..


SOLUTION:Wireless button on laptop doesnt change color when wireless card is engaged.. so naturally I assumed it was on and operating cause Ive had the same issue with other linux systems I just pushed it and networks started appearing... so the problem is fixed hope this helps any other ppl with same problem..

---

### Post by klemes on 2009-11-02
I am by no means expert in aircrack-ng but I dont think these will give you any trouble .Go ahead and proceed to the airodump-ng and aircrack-ng commands and see how it goes.

---

### Post by amedac on 2009-11-02
when you are working with aircrack programs, you must turn off network manager, and you must configure everything from terminal, you have a lot of aircrack tutorials on the net, video tutorials on youtube etc

---

