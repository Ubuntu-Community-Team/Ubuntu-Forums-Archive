---
title: "How to prevent non VPN traffic?"
date: 2012-05-04
forum: General Help
---

### Post by dshuck on 2012-05-04
I have a VPN adapter that is configured as adapter ppp0.  My intention is to ensure that all my traffic goes through that VPN connection.  What I have found is that occassionally, that VPN connection will drop out and traffic will begin routing through wlan0 without being obvious to me.

Could someone point me to how I might best be able to ensure that I have no traffic running across wlan0, other than of course the ability to create the connection to ppp0?

I have seen a recommendation that pointed to this: [http://pastebin.com/qPM84b7z](http://pastebin.com/qPM84b7z), however, I honestly have virtually no idea how to implement it, and am a little worried that I am going to do something that I may have trouble reversing out of.  

Any advice would be appreciated.

---

### Post by dshuck on 2012-05-05
If anyone else comes across this, it was amazingly simple. First I backed up my current good iptables configuration like this:

```
sudo iptables-save > ~/iptables/working.iptables.rules

```

Then I took the sample iptables file that I linked above (putting it below in case it disappears in the future) and saved it as ~/iptables/vpn.iptables.rules

```
# Begin Here
*filter
:OUTPUT DROP [0:0]
:FORWARD ACCEPT [0:0]
:INPUT ACCEPT [0:0]
# Comment

## Wireless Rules 

# DHCP and DNS
-I INPUT -i wlan0 -p udp --dport 67:68 --sport 67:68 -j ACCEPT
-A INPUT -i wlan0 -p udp --sport 53 -j ACCEPT
-A OUTPUT -o wlan0 -p udp --dport 53 -j ACCEPT
# PPTP and GRE for outbound VPN connections
-I OUTPUT -o wlan0 -p tcp --dport 1723 -j ACCEPT
-I OUTPUT -o wlan0 --proto gre -j ACCEPT
# Allow comms with home network
-I OUTPUT -o wlan0 -d 192.168.99.0/24 -j ACCEPT


## VPN Firewall Rules

# Allow anything outbound
-I OUTPUT -o ppp0 -j ACCEPT


## Loopback Firewall Rules

# Allow anything
-I INPUT -i lo -j ACCEPT
-I OUTPUT -o lo -j ACCEPT


COMMIT
```

I then restored iptables using that file like this:
```
sudo iptables-restore < ~/iptables/vpn.iptables.rules
```

And that's it.  When I drop my VPN, I can no longer hit any remote resource.  When I bring it back up, all is well!

---

### Post by strask on 2012-05-05
Thanks for updating your post with this solution! :)

---

### Post by dcstar on 2012-05-05
> **dshuck said:**
> If anyone else comes across this, it was amazingly simple.
.........

Then please **MARK** the thread!

---

