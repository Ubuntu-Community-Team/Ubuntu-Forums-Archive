---
title: "Installing senao 2511cd"
date: 2006-03-21
forum: General Help
---

### Post by h3llfyr3 on 2006-03-21
Hi All,
I've never installed hardware under Ubuntu before...
I've got a pcmcia senao 2511cd card (prism 2.5 chipset I think) and have installed the wlan-ng package using apt-get.

ANy Ideas on getting it working?

root@Ar35:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by srf21c on 2006-10-16
I was eventually able to get my Senao 2511CD working on Xubuntu dapper 6.06 with the autodeteced orinoco_cs module driver.  The card was not detected during the installation process however, and at first I could only get the card working when booting to the Xubuntu live CD.   

Further investigation led me to copy the /etc/pcmcia/config.opts settings file from the live CD system to my hard drive installation of Xubuntu.  The necessary lines in config.opts are listed below.

```
# System resources available for PCMCIA cards
include port 0x100-0x3af
include memory 0xc0000-0xfffff

```

---

### Post by oregonvet on 2008-02-12
So is it that easy? I have the same problem. The Senao card worked fine doing an online installation (which I assume is like a live cd) and when I rebooted into xubuntu I couldn't get online. The card would not light up but when removed and reinserted it did but still would not let me online. 

So finding that file and copying it as you have is what I'll try next.

---

