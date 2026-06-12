---
title: "Firestarter, now no network connection"
date: 2012-08-05
forum: General Help
---

### Post by MotherMayI on 2012-08-05
Hi all, any assistance on my situation would be much appreciated -

In the process of trying to get my Ubuntu machine to share its Wifi connection with a Playstation 3 via crossover I followed the advice from various posts and tried setting it up via 'firestarter'.

Although the attempt was unsuccessful, my internet connection on the PC did still initially work. Then it stopped. Disabling the firewall did nothing, so I tried to remove it:

```

sudo apt-get purge -y firestarter

```

Still no internet connection. Restarted, still no internet connection. Tried:

```

sudo iptables -F

```

And I still have no internet connection.

ifconfig is showing my wlan0 IP address as 10.42.0.1, which is very strange - it is normally 192.168.1.141. I also cannot ping 10.42.0.1 from other computers on the router. Equally, the computer in question cannot ping other computers (either on the network or on the internet) and just errors - 'connect: Network is unreachable'.

Any help would be much appreciated.

Thank you.

---

### Post by colin.p on 2012-08-05
I am quite sure that someone will be able to soon help you, however, Firestarter is no longer updated and generally not recommended. The last time I used it was in Redhat 9 and I had a similar issue as you. I was trying to set up an ICS for dialup and eventually had to re-install as nothing I could find would fix it. If memory serves me, it was a DNS issue, so if you can't ping then it would be a different problem.

Of course, help forums like this one were virtually nonexistent at that time.

---

