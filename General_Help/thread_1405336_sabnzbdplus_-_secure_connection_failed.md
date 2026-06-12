---
title: "sabnzbdplus - secure connection failed"
date: 2010-02-12
forum: General Help
---

### Post by wt1 on 2010-02-12
Using Ubuntu Server 9.10 & SABnzbd+ 0.5.0 RC6

I was hoping someone could help me out. Keep in mind my knowledge of linux is limited but I am quickly learning. So far everything is working how I want but when I try to access SABnzbd+ from a secure https connection I get this error message:

Secure Connection Failed
An error occurred during a connection to x.x.x.x:9090.
SSL received a record that exceeded the maximum permissible length.
(Error code: ssl_error_rx_record_too_long)

Regular http connection works fine but I would like to connect via https. For IP address I tried using my servers static IP address, I also tried 0.0.0.0 and the hostname (mediaserver). None of which work. I think it has to do with my port (9090) on my desktop setup it was automatically set up as the ssl port for sabnzbd+ and worked without any further tweaking but that doesn't seem the case for my Ubuntu Server setup.

How can I configure port 9090 on the server as a ssl port that SABnzbd+ will use? I already have it set up in the SABnzbd+ client correctly I think its the server side that I have to tweak something. 

Hopefully this all makes sense, any suggestions? Thanks.

---

### Post by wt1 on 2010-02-13
Nobody else has issues connecting to Sabnzbd+ via https? Any help would be appreciated. I tried the Sab forums as well but nobody seems to understand my issue unfortunately.

---

### Post by -::Bas::- on 2010-03-28
I had the exact same issue, (on AMD64, ubunut Karmic / 0.5.1RC2 ), when I came to the conclusion the ports of http and https were the same!
Changing that in ~/.sabnzbd/sabnzbd.ini fixed that error for me.

---

