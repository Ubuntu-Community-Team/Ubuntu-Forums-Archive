---
title: "Can't set wireless cards into Master mode (airsnarf)"
date: 2011-04-24
forum: General Help
---

### Post by LawlCakes on 2011-04-24
[FONT="Arial Black"]I'm running Blackbuntu 10.10 with the 2 wireless cards RTL8187L and a RT2870/3070. Both cards have the correct drivers. But I noticed when I was trying to start Airsnarf it failed at the creating the AP. Here is my output.[/FONT]

```

Airsnarf - A rogue AP setup utility.
0.2
The Shmoo Group
------------------------------------
Creating dhcpd.conf...Done.
Building the captive portal...chmod: cannot access `/var/www/cgi-bin/*': Not a directory
Done.
Setting the wireless parameters...Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Invalid argument.
Done.
Setting the ip address and default route...SIOCADDRT: File exists
Done.
 * Stopping DHCP server dhcpd3                                           [fail]
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]
 * Restarting Mail Transport Agent (MTA) sendmail                        [ OK ]
Setting up firewall to redirect DNS...Done.
Starting local DNS resolver...
 
Creating TCP socket 0#53 - done.
Creating UDP socket 0#53 - done.
Waiting for connections...
Waiting for connections...

```

[FONT="Arial Black"]I've tried getting it into Master mode in Terminal but still has the same error...I've even tried both cards. In Airsnarf and in Terminal. Both say the same thing. I'm out of ideas.:confused:[/FONT]

---

