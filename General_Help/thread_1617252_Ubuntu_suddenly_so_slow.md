---
title: "Ubuntu suddenly so slow"
date: 2010-11-09
forum: General Help
---

### Post by kanishkdudeja on 2010-11-09
i installed ubuntu 10.10 on my bro's pc around 2 weeks back..it ws running fine till a day back..suddenly its slowed up..it starts freezing for around 10 seconds in between..example when i play a song..the song will jus freeze in between..what can cause this problem ? 

its shows 100% cpu usage even if im only playing a song..

is der some problem in ubuntu ?

or with the ram ? i hav 512 mb of ram

i recently installed my printer driver - hplip around 2 days ago..can der be some prob with that..it doesnt look like it because i installed the same on my laptop and its working fine..

---

### Post by Verbeck on 2010-11-09
try the command **top** from a terminal to see which process is eating up the resources

---

### Post by kanishkdudeja on 2010-11-09
im not able to get..

some user lp is eating up the resources..

my username is sushant..

im attaching the screenshot..

---

### Post by Verbeck on 2010-11-09
afaik, lp and gs are some how related to printing
i dont know much about it so i'd recommend waiting for someone else to sort it out before killing the process

---

### Post by kanishkdudeja on 2010-11-09
fixed it..

lp is the printing service..

1 job ws in the print queue..as soon as a removed it..its all fine now..

lol looks like a silly thing..a pending print job could consume about 50% ram..

---

### Post by kanishkdudeja on 2010-11-09
anyway from where could i get a basic list of commands that can be run from the terminal in ubuntu ?

like top to see memory allocation..
mount to mount drives..
apt-get to install packages..

etc etc

---

### Post by Verbeck on 2010-11-09
these might help
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)
[http://ss64.com/bash/](http://ss64.com/bash/)
and [URL="http://www.google.com/"]http://www.google.com/ :)
[/URL]

---

### Post by tajiknomi on 2010-11-09
[SIZE=2]For  commands[/SIZE],Follow the link..
.. [http://www.reallylinux.com/docs/basic.shtml](http://www.reallylinux.com/docs/basic.shtml)[]("http://ss64.com/bash/")

---

### Post by kanishkdudeja on 2010-11-09
thanks guys

---

