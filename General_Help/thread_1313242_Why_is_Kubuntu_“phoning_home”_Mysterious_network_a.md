---
title: "Why is Kubuntu “phoning home”? Mysterious network activity!"
date: 2009-11-03
forum: General Help
---

### Post by viking_maniac on 2009-11-03
I installed the Gnome system monitor into Kubuntu since I think it's much greater than the one that comes with Kubuntu. Not long after, I suddenly discovered a lot of &#8220;bumps&#8221; in the network activity towards Internet at the network activity graph in Gnome system monitor. When my computer communicates pretty active with &#8220;something&#8221; on the Internet without me or any applications are doing anything, like when the OS is completely idle, and even when automatic updates and notifications are turned off, it sure raises some red flags in my security book!

So out of high curiosity, I installed Wireshark to see what is going trough my network.

To my huge surprise, after an hour or so and Kubuntu standing completely idle, a couple of megabytes have been transmitted:

A lot of requests have been sent from my local IP to: 224.0.0.251 port 5353 protocol MDNS. Though, no replies back, only from my IP to the IP mentioned.
Another thing that worried me was that my computer suddenly sent, out of the blue, a DNS request and started communicating with this address: 91.189.90.132 TCP/HTTP port 80. This address belongs to Canonical Ltd Admin, and Wireshark states this: Standard query, changelogs.ubuntu.com.

So my network card is suddenly pretty active after I got Kubuntu 9.10 and a lot of things going on (behind my back, apparently) which I actually don't like. As been written, I've disabled automatic updates and checks for updates, even notifications of updates. My computer is idle and this test was done right after login; I just left it idle with nothing happening on it. Well, something is happening!

I'm really curious about what this is and if this can be disabled. When I had Ubuntu 9.04, this didn't happen and my network card was totally quiet unless I started browsing or doing stuff on the net. Therefore I hope someone can share some light on this issue!

Thanks in advance!

---

### Post by Giblet5 on 2009-11-03
Open a terminal window and plug in ```
while true
do
    clear
    netstat -apn | grep ESTABLISHED
    sleep 3
done
```

That will show you each established connection and the application who owns that socket.

It's OK to ignore connections from/to 127.0.0.1...

---

### Post by StuartN on 2009-11-03
> **viking_maniac said:**
> A lot of requests have been sent from my local IP to: 224.0.0.251 port 5353 protocol MDNS.

mDNS is Multicast DNS and IP addresses in the range 224.0.0.0 - 239.255.255.255 are special purpose IP addresses for mDNS. This is normal behaviour in a local network and is not accessing a remote site. A few megabytes per hour seems normal enough, and much more if there is a music server or similar active.

> **viking_maniac said:**
> This address belongs to Canonical Ltd Admin, and Wireshark states this: Standard query, changelogs.ubuntu.com.

I guess that is how your Linux lets you know that updates are available.

You will also get some external requests for the weather applet and time server. They are also normal behaviour.

---

### Post by viking_maniac on 2009-11-05
This problem is so solved! :D

For those of you who are interested:

_**AVAHI-DAEMON**_
*This is the sinner regarding outgoing MDNS-spam!*
In terminal:
$ kdesudo kate /etc/avahi/avahi-daemon.conf
Edit:
deny-interfaces=<your network device> *(of course without <>)*

_**AVAHI-DAEMON**_
*This is for disabling an idiotic DNS request at startup; only spamming the DNS-servers!*
In terminal:
kdesudo kate /usr/lib/avahi/avahi-daemon-check-dns.sh
Edit:
AVAHI_DAEMON_DETECT_LOCAL=0

_**NTP (INTERNET AUTOMATIC TIME ADJUSTMENT/SYNC AT BOOT)**_
*This happens at every boot, but can be disabled!*
In terminal:
kdesudo kate /etc/default/ntpdate
Edit:
## NTPDATE_USE_NTP_CONF=yes
## NTPSERVERS="ntp.ubuntu.com"
## NTPOPTIONS=""
(Add ## to see which you edited in case you want to revert later.)

Make a copy of this guide in case you want to revert later. Nothing permanent is done here since you're not uninstalling anything, hence it's easy to revert.

After I did this, my network was completely quiet and didn't do anything over an idle period of several hours. :)

---

### Post by ibutho on 2009-11-05
Another option would have been to use update-rc.d to disable avahi and ntpd from automatically starting at boot time.

---

### Post by viking_maniac on 2009-11-05
> **ibutho said:**
> Another option would have been to use update-rc.d to disable avahi and ntpd from automatically starting at boot time.

I'd be happy to learn how to do this! :)

---

### Post by StuartN on 2009-11-09
For most people, most of the time, these are safe default actions with a low overhead. Enabling DNS and network discovery is a complex task, so to have it set up for people who wish to use it (anyone using automatic IP address, hostnames via their router, or with Mac and Windows shares) is a blessing. These messages are internal, local network messages.

Likewise the time-check is easy to disable and difficult to set up.

---

