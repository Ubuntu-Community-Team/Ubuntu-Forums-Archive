---
title: "Network Change"
date: 2012-02-29
forum: General Help
---

### Post by OldManRiver on 2012-02-29
All,

I closed my thread at: 

[http://ubuntuforums.org/showthread.php?t=1804424](http://ubuntuforums.org/showthread.php?t=1804424)

Where I outlined and my network and worked to solve it's unique problems.  I finally won and now have the Clear Box so have added it to the diagram here:
```
_____________                                    ______________
|             |                                  |              |
|             |__/|                          |\__|              |
|    MAIN     |  \|    WIFI W/HGain Ants     |/  |    REMOTE    |
|   WHOUSE    |                                  |    WHOUSE    |
|             |                                  |              |
|_____________|                                  |______________|
                                                         |
                                                         |  wlan0    _______
       _______     _______     _______    ______     ____|___       |       | 
      |       |   |       |   |       |  |      |   |        |      | Clear |
      | W-Box |   | Svr1  |   | Svr2  |  | Svr3 |   |  UBox  |______|  Box  |
      |_______|   |_______|   |_______|  |______|   |________| eth2 |_______|
          |           |           |         |            | 
          |___________|___________|_________|____________|  eth0
                         Local Remote Network R-LAN
```
So now wlan0, formerly the primary internet connection is now a secondary connection and eth2, the Clear Box become the primary.

I attempted the changes to the network config files and put them on a PasteBin at:

[http://pastebin.com/bZx25w8B](http://pastebin.com/bZx25w8B)

From what I see in the files 2 things jump out at me are:
[LIST=1]
[*]resolv.conf - the default nameserver was 192.168.3.1 (wlan0 now missing) and the new nameserver for eth2 is the one shown,
[*]iptables - is blank and should contain the info from the last 2 lines of the script wifi-start.sh, which is to bridge the internet connections to the LAN on eth0.  Also I need to add the "load balancing" and other capabilities available for multiple and shared internet connections.

Some good URLs will suffice at this point, I think.  Oh if you know how to get Network Manager to be able to only "READ" the resolv.conf file I would love that too.

Thanks!

OMR
[/LIST]

---

### Post by OldManRiver on 2012-03-14
All,

Can I get some help here?

OMR

---

### Post by OldManRiver on 2012-04-02
All,

Marked this "SOLVED" as I found another way around this!

Cheers!

OMR

---

