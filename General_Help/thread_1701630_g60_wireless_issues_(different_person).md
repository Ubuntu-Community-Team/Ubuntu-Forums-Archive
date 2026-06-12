---
title: "g60 wireless issues (different person)"
date: 2011-03-06
forum: General Help
---

### Post by Seiroku on 2011-03-06
I'm new to all of this so please take it easy on me. I'm having similar issues to the last HP g60 user.  I tried all of what was in the help there and nothing seemed to work.  these are the stats i was given when i checked after i messed around with the system.  I am completely confused on how to fix this, please help!!!!  any other information, please let me know how to access it.
vanilla Maverick 10.10,

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          
ppp0      no wireless extensions.

$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by bkratz on 2011-03-06
Well first check the wireless switch, it usually generates the hard block. If ok try

sudo rfkill unblock all

and see if that gets you going

---

### Post by Seiroku on 2011-03-06
the switch is just an LED button by the power button.  it's orange when the wireless is disabled and blue when it's enabled.  i press the button and it stays orange.  i'm not sure how to enable the wireless.  i tried a fix from the other thread and it enabled the wireless but the LED stays orange.  It's frustrating me beyond belief.  >_<

---

### Post by Seiroku on 2011-03-06
oh, and right now the module hp_wmi is NOT loaded.  it was and didn't seem to be doing me any good, so i tried the disable and blacklist and when i rebooted, hp_wmi is gone so i'm not sure how to get that back to test it.

i typed in dmesg | grep -e ath9k -e wlan

and got:

$ dmesg | grep -e ath9k -e wlan
[   15.560289] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.560308] ath9k 0000:02:00.0: setting latency timer to 64
[   15.635931] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   15.636664] Registered led device: ath9k-phy0::radio
[   15.636684] Registered led device: ath9k-phy0::assoc
[   15.636701] Registered led device: ath9k-phy0::tx
[   15.636719] Registered led device: ath9k-phy0::rx
[  606.108148] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

