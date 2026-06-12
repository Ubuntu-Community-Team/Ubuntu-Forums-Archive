---
title: "Detect if TV is currently receiving signal through HDMI"
date: 2012-03-18
forum: General Help
---

### Post by 160R on 2012-03-18
I have a HTPC Zotac HD-ID40, with ubuntu 10.04 installed, running XBMC. I was wondering if it is possible, to get/see on HTPC (ubuntu), if TV(LG) is currently receiving signal from HDMI. Is there any signal sent from TV to HTPC when TV is on and switched to HDMI port(not AV, Antenna,...).

I know that HTPC reads TV EDID(Extended display idnetification data), but EDID is supposed to be static data, and can be read even if the TV is off. Is there any file in ubuntu that would containg info of TV receiving signal?

I don't believe that this can be done but I asked it anyway. 

Thank you all for your answers!

Lp: 160R

---

### Post by papibe on 2012-03-18
Hi 16R. Welcome to the forums!

You can get the EDID into a file and then set your system so that it reads that file instead of trying to fetch the data every time.

If your system is based on th Nvidia ION board, you need to insall the Nvidia proprietary driver  first, and then reboot your system.

This [thread]("http://ubuntuforums.org/showthread.php?t=1936293&highlight=nvidia") contains the details you need to set it up. It is a slightly different case, but the specifics apply for you. Take a look and tell us if you need more help with that.

Regards.

EDIT: in your case, you don't need to change cables at all.

---

### Post by 160R on 2012-03-19
I can get EDID. But what I was wondering if there is any data that would tell me if TV is ON or OFF, which EDID doesn't tell me?

---

### Post by papibe on 2012-03-19
Ohh, I see. Sorry if I misunderstood.

To be honest, I don't really know. However, since it is an interesting question I did a little research, and this is what I learned:

The usual tools, like xrandr, xset, and even nvidia-settings, will provide "false positives". That is, they will report the monitor is on even if it is not. Apparently this happens because most monitors can 'reply' request for data even if they are off (they just need to be plugged to the electricity).

Also, almost any monitor that was detected during boot will be later report as on.

It looks that you need low level tools like the ones available on the package ddccontrol. Here are a couple of interesting references: [this]("http://stackoverflow.com/questions/3433203/how-to-determine-if-lcd-monitor-is-turned-on-from-linux-command-line") and [this]("http://stackoverflow.com/questions/5813195/detecting-if-the-monitor-is-powered-off").

I hope that help you get in the right direction. It would be interesting to see what else you can find out.

Regards.

---

### Post by 160R on 2012-03-23
papibe:

Thank you very much. I tried ddccontrol program but it says my TV doesn't have DDC/CI info. But thanks anyway. Well I hope something comes by.
 
I think I deserve to tell why I'm needing this. 
 
Well I hava HTPC with ubuntu 10.04 and XBMC running(auto start at boot). For XMBC navigating I use [flirc]("http://flirc.tv/"), and TV's remote control. But when I'm switching DVB-T channels on TV, HTPC is receiving keyboard events (through TV's remote control and flirc). So I wanted to block keyboard events, based on information I was trying to get.

---

