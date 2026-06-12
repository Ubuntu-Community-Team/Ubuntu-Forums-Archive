---
title: "I need a good advice for strange problem?"
date: 2006-04-25
forum: General Help
---

### Post by Anilkumar on 2006-04-25
Hello everybody,

I am broadband user in India . I have unlimted download from morning 2am to 8am.
Now i want to use this unlimted time for downloading the movies through by using torrrents softwares like bittorrent etc.

My questions are 
1.How can i automatically boot ubuntu at 2 am?
2.How can i automatically start the software i like at 2.05 am?
3.How can i shutdown the ubuntu automatically?
4.How can i schedule the programs?
5.Suggest me any good softwares for downloading movies by using torrents?
( i already installed azureus but not working so i have only bittorrent in my ubuntu)


Plz fix me this problem . ang suggest me the goodways.

---

### Post by enopepsoo on 2006-04-25
I am not sure about turning the computer on, but to start up bit torrent and shut down the system you could use cron jobs.

not sure if you know how to use cron, so
```
sudo gedit /etc/crontab
```
and that file is well documented on how to set up a new job.

Edit:  It occured to me that for the sake of completeness I could add:

```
shutdown now -hP
``` would be the command line argument to powerdown.

---

### Post by Anilkumar on 2006-04-29
Thank you

---

### Post by Sutekh on 2006-04-29
You can also use shutdown with a specified time
```
sudo shutdown -h 08:00
```
Will shutdown the system for a halt (no reboot) at 08:00AM

---

### Post by IYY on 2006-04-29
What the guys above me said, plus a question: why don't you just leave your computer on? It would make things much simpler, and it's what most Linux users do anyway (some have years of uptime ;) )

---

