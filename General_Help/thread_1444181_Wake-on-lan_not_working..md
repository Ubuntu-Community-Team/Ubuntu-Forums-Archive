---
title: "Wake-on-lan not working."
date: 2010-03-31
forum: General Help
---

### Post by robofighter on 2010-03-31
Since installing Ubuntu server on my windows 7 rc machine, WOL is not working anymore.

I have used both wireshark on my computer and TCPdump on the ubuntu server, both them confirm that the WOL command was sent and received correctly.

Mac address are also correct and static private ip address was set to the server.

---

### Post by robofighter on 2010-04-01
still not working

---

### Post by robofighter on 2010-04-01
fyi I am using a magic packet method.

---

### Post by robofighter on 2010-04-02
It is working now.

I used the command ethtool on my ubuntu server, and it shows
supports wol: pumbg
wol: d

The d turns out that it meant disabled
so I used
```
sudo ethtool -s eth0 wol g
```

It enabled the wol, and is now allow the system to wake up through a magic packet.

---

### Post by Kenniej on 2010-04-02
Thnx, worked for me too !

---

