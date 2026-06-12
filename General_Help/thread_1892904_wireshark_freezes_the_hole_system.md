---
title: "wireshark freezes the hole system"
date: 2011-12-09
forum: General Help
---

### Post by hg088 on 2011-12-09
im running oneiric

when i run wireshark with gksu and then try to start capturing on wlan0, the hole system would freeze immediately

has this happened to anyone else?

any fix?

---

### Post by Synoc on 2011-12-09
I think last time I tried wireshark on my system (which I'll never do again BTW) I jsut used a "sudo wireshark" but I recommend using a distro called "BackTrack Linux" direct from the livedvd it's safer than allowing wireshark to run on your PC/Server.

---

### Post by josephmills on 2011-12-09
> **hg088 said:**
> im running oneiric

when i run wireshark with gksu and then try to start capturing on wlan0, the hole system would freeze immediately

has this happened to anyone else?

any fix?

alt+f2 
then 
gksudo wireshark 


works for me what version do you have ?
also how are you trying to capture? 
could we also see a 
```
lspci -nn | grep Wireless 
```

---

### Post by hg088 on 2011-12-09
> **josephmills said:**
> alt+f2 
then 
gksudo wireshark 


works for me what version do you have ?
also how are you trying to capture? 
could we also see a 
```
lspci -nn | grep Wireless 
```

thanks for answering guys, and sorry for taking so long to answer u back.
im trying to capture traffic on wlan0 which is usb (dont know if thats implied)

when i run wireshark as root, a message window appears saying: Lua: Error during loading:
 [string "/usr/share/wireshark/init.lua"]:45: dofile has been disabled

and as soon as i click on the wlan0 entry to start capturing, the hole system just freezes
and raising skinny elephants doesnt work

im runnng oneiric amd64 and installed wireshark from the software center

---

### Post by hg088 on 2011-12-10
jmm, weird, i unchecked "capture in promiscuous mode" in the nic options and now it appears to work fine

im actually kind off a noob so i was hoping some could tell me what does that promiscuous mode thing mean

---

