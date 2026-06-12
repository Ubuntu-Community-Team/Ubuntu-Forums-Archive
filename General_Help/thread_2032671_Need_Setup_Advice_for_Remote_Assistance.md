---
title: "Need Setup Advice for Remote Assistance"
date: 2012-07-24
forum: General Help
---

### Post by Petro Dawg on 2012-07-24
I was recently given a computer tower at work, which they were going to throw away due to a failed hard drive.  I spent about $100 (USD) for a new 40GIG HD, 2 GIG RAM, and some other accessories to make it a complete system along with the extra hardware I had laying around at home.  I installed Xubuntu12.04 as the operating system (as the processor is just not quite up to par to run Ubuntu12.04).  It runs great and I decided to give this computer to my Mother to replace her current useless POS (which is running Win95 I believe). 

Here's the issue:  I live about 16 hours away from my mother.  I'll be there next week to setup and install the computer, but after that, I will not be regularly available to locally assist with any problems she may have.  

Here's the question:  Does anyone know of, and have successfully used, any good software which would allow me to remotely log on to and control her computer if and when she has any problems that need fixed???  

Free is great, but I would be willing to pay (some) for the software if it is excellent and no free substitutions are available.  I've done a little research on this, but I would like to get an opinion from someone who uses Ubuntu or Xubuntu and has successfully done something like this.

I run both Win7 and Ubuntu12.04 on my end, if that makes any difference.

---

### Post by dino99 on 2012-07-24
[http://www.google.fr/#hl=fr&sclient=psy-ab&q=ubuntu+remote+control&oq=ubuntu+remote+control&gs_l=hp.3..0j0i30l3.2823.8877.0.9190.21.11.0.6.6.0.161.937.7j4.11.0...0.0...1c.TmLQY6Idwv4&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=95d976ace56bc2fe&biw=1680&bih=895](http://www.google.fr/#hl=fr&sclient=psy-ab&q=ubuntu+remote+control&oq=ubuntu+remote+control&gs_l=hp.3..0j0i30l3.2823.8877.0.9190.21.11.0.6.6.0.161.937.7j4.11.0...0.0...1c.TmLQY6Idwv4&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=95d976ace56bc2fe&biw=1680&bih=895)

---

### Post by PhilGil on 2012-07-24
I use TeamViewer with my family and friends. It's free (as in beer) for non-commercial use, works reasonably well, and supports Windows, Mac and Linux. I also recently saw a glowing review of a new Chrome extension that supports remote access. Both computer have to have Chrome/Chromium installed for the extension to work, though.

You can also use SSH, but be sure to follow the setup guidelines carefully as it can put your computer at risk if it is not secured properly.

---

### Post by Petro Dawg on 2012-07-24
> **dino99 said:**
> [http://www.google.fr/#hl=fr&sclient=psy-ab&q=ubuntu+remote+control&oq=ubuntu+remote+control&gs_l=hp.3..0j0i30l3.2823.8877.0.9190.21.11.0.6.6.0.161.937.7j4.11.0...0.0...1c.TmLQY6Idwv4&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=95d976ace56bc2fe&biw=1680&bih=895](http://www.google.fr/#hl=fr&sclient=psy-ab&q=ubuntu+remote+control&oq=ubuntu+remote+control&gs_l=hp.3..0j0i30l3.2823.8877.0.9190.21.11.0.6.6.0.161.937.7j4.11.0...0.0...1c.TmLQY6Idwv4&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=95d976ace56bc2fe&biw=1680&bih=895)

Thanks, but, did you see the article dates that this search pulls up?  Articles from 2004 & 2007 are nice, but don't provide much info about current software options.

I'm looking at Remmina Remote Desktop Client (standard install on ubuntu) and Desktop Sharing Preferences, just not sure the best way to set these up.

---

### Post by Petro Dawg on 2012-07-24
> **PhilGil said:**
> I use TeamViewer with my family and friends. It's free (as in beer) for non-commercial use, works reasonably well, and supports Windows, Mac and Linux. I also recently saw a glowing review of a new Chrome extension that supports remote access. Both computer have to have Chrome/Chromium installed for the extension to work, though.

You can also use SSH, but be sure to follow the setup guidelines carefully as it can put your computer at risk if it is not secured properly.


Thanks, I'll look at that too.

---

### Post by lukeiamyourfather on 2012-07-24
I'd use ssh (and ssh with X tunneling for anything with a GUI). Just install it from the repositories and you're good to go. It uses the system usernames and passwords to verify users wanting to connect.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-07-24
Go for TeamViewer without any doubts. It's by far the most supported, most stable and by many elements most elegant out there. Plus, it's available for so many platforms, including Android (meaning you can control a remote computer from your mobile phone). I've been using it for 7 years now. Good stuff.

---

### Post by Petro Dawg on 2012-07-24
Thanks everyone, 

I tried messing with native ubuntu VPN clients and was having all sorts of trouble getting computers connected.  So I tried TeamViewer and its by far the simplest choice, works like a charm.

I'll be putting this on my mother-in-law's and my wife's computer too.  I love it.

---

