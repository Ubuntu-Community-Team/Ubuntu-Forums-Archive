---
title: "Conky network speeds with wireless"
date: 2010-07-31
forum: General Help
---

### Post by turvyc on 2010-07-31
Hi all,

So I've got my Conky tweaked to exactly how I want it, with one small issue that I'm hoping y'all can help me with. I have a section called "network activity" that monitors the up/download speeds of my internet connection. This works perfectly if I have a wired connection, but if I have a wireless connection, both up and down read 0. I've looked at the Conky variables, but the wireless variables only have to do with connection strength/type etc. Here's the relevant part of my ~/.conkyrc ...
```
# Network Information
${font TlwgTypewriter:bold:size=10}${color1}${alignr}network activity 
$font${color2}Up: ${upspeed}${alignr}Down: ${downspeed} 
```
It's pretty simple, but it just doesn't work for the wireless situation. Anybody have any ideas?

---

### Post by Old_Grey_Wolf on 2010-07-31
Change 

$font${color2}Up: ${upspeed}${alignr}Down: ${downspeed} to
$font${color2}Up: ${upspeed eth0}${alignr}Down: ${downspeed eth0}

You may need to use eth1 instead of eth0.

---

### Post by AlphaLexman on 2010-07-31
> **Old_Gray_Wolf said:**
> You may need to use eth1 instead of eth0.
You may need to use wlan0 instead of eth1.

---

### Post by turvyc on 2010-07-31
Ah of course, I forgot about that parameter. I want it to show my up/down speeds whether I'm connected by wired or wireless, so I used the handy ${if_up} and ${else} tags:
```

${if_up wlan0}Up: ${upspeed wlan0}${alignr}Down: ${downspeed wlan0}${else}Up: ${upspeed eth0}${alignr}Down: ${downspeed eth0}${endif}
```
The only problem is that if I go from a wireless to a wired connection, I have to manually switch off the wireless switch on my laptop in order for wlan0 to go down. I guess that's good practice anyways, but interestingly if I turn it back on (while still connected to the wired network), wlan0 stays down, and only comes back up if I reconnect to a wireless network.

Anyways, thanks for the help folks!

---

### Post by lambchops468 on 2010-10-18
> **turvyc said:**
> Ah of course, I forgot about that parameter. I want it to show my up/down speeds whether I'm connected by wired or wireless, so I used the handy ${if_up} and ${else} tags:
```

${if_up wlan0}Up: ${upspeed wlan0}${alignr}Down: ${downspeed wlan0}${else}Up: ${upspeed eth0}${alignr}Down: ${downspeed eth0}${endif}
```
The only problem is that if I go from a wireless to a wired connection, I have to manually switch off the wireless switch on my laptop in order for wlan0 to go down. I guess that's good practice anyways, but interestingly if I turn it back on (while still connected to the wired network), wlan0 stays down, and only comes back up if I reconnect to a wireless network.

Anyways, thanks for the help folks!

Hi, I know I'm dragging up an old thread but since I got here using google, I figured it might be good to post the solution
Conky has a configration value called if_up_strictness with values {up,link,address}.
using
```

....config stuff....
if_up_strictness address
.....some more config..
TEXT
...your text

```
will make if_up test for the presence of an IP address instead of the interface being up.

---

