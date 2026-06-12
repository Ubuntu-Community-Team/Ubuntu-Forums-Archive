---
title: "High cpu usage"
date: 2012-10-07
forum: General Help
---

### Post by potatoos on 2012-10-07
This problem started after I resized my Wubi partition. After rebooting, my cpu usage monitor showed that I was constantly using about 50% of my cpu, even with no programs running. Usually with nothing running, it doesn't show more than about 10% cpu usage. This was just after start up. I opened system monitor and looked for programs that were using more cpu than normal, but there were non. It just seemed that everything was running normally, but an extra 50% cpu usage was added on with no programs being responsible. 
I am not sure how to properly insert an image (maybe I have to upload it to an image hosting site first) but system monitor showed that CPU1 was using ~100% while CPU2 was using `10%, and after a short while, they would switch. I assumed that that represented the individual cores, as my computer is a dual core. Is this some sort of virus, or is something malfunctioning? Nothing else seems to be out of the ordinary.

---

### Post by HiImTye on 2012-10-08
```
top
```is a great resource for determining CPU usage (among other things)

or, if you want something easier to see, use
```
sudo apt-get install htop
htop
```

---

### Post by potatoos on 2012-10-08
I ran htop and the cpu is being used by root and the command is /usr/sbin/cupsd -F.

I really need this fixed. Everything is running really slow.

---

### Post by twipley on 2012-10-08
One sure way would be to reinstall afresh, by the way.

---

### Post by potatoos on 2012-10-08
I have been trying to avoid a fresh install. I would like to get this fixed.

---

### Post by clay7 on 2012-10-08
Did you recently try to print anything? If so, delete any pending print jobs.

Otherwise, find the PID number of cupsd with htop and > kill -9 *PIDNUM*

---

### Post by HiImTye on 2012-10-09
well, CUPS is the main Unix printing service, so it's odd that it's using so much CPU. I'd check out what it's doing at [http://localhost:631](http://localhost:631)

---

### Post by potatoos on 2012-10-09
There are now two programs taking up my cpu and when I try to kill them with that command, I get this message:
```
sebastian@ubuntu:~$ kill -9 1014
bash: kill: (1014) - Operation not permitted
sebastian@ubuntu:~$ kill -9 4149
bash: kill: (4149) - Operation not permitted

```

Edit: That second program disappeared.

---

### Post by potatoos on 2012-10-09
I put "sudo" in front of that kill command and it killed the process, but then a new one showed up, the only difference being that it has a new PID.

---

