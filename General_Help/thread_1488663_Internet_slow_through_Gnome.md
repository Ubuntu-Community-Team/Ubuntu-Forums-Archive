---
title: "Internet slow through Gnome"
date: 2010-05-20
forum: General Help
---

### Post by grunt0r on 2010-05-20
I'm having a woeful time with an install of 10.04 and slow response from  anything gui based trying to get out to the web. From terminal wget/  aptitude/ ping etc is fine, standard response and download rates.
Trying from Thunderbird, Chromium, Opera, Thunderbird, update manager,  hell anything with a gui is horrid however, often it won't load at all,  often I'll see some form of response but then it will hang on waiting  etc. Whats strange is google.com is snappy, really snappy, google.com's  are the only things that will load normally.

I've disabled IPV6 system wide through grub. I've also tried in just Firefox through about:config. I can't see anything in any  logs, including xsession and messages/ syslog. 
I've tried opendns, my ISP's DNS  and running through a Cisco router  caching from my ISP all to no avail, response times from ping etc don't  seem to indicate any large delays from DNS, and actually throwing an IP  into a web browser doesn't seem to speed things much either.

Using Ethernet through below adaptor:
03:00.0 Ethernet controller: Atheros Communications L1 Gigabit Ethernet Adapter (rev b0)
x64 install of 10.04, clean.
Occurs on multiple users with clean profiles or not.
Actual network connectivity seems great, SSH and VNC sessions to this box are more then fine.

This has got me stumped, ready to roll this compy back to 9.10 just to  silence my Mother, but before I visit her next I figure I might as well  try to recover it.

Any ideas anyone?

---

### Post by dino99 on 2010-05-20
first check your video driver installation: system admin hardware driver, is yours activated ?

look at logs for warnings or errors (system admin log viewer)

---

### Post by grunt0r on 2010-05-20
Nvidia drivers are enabled, latest recommended version. 
I'm also not really seeing any log events that seem to be relevant :(

---

