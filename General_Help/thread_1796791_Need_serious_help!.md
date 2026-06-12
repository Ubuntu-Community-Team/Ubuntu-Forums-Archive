---
title: "Need serious help!"
date: 2011-07-04
forum: General Help
---

### Post by kimothy1987 on 2011-07-04
Hi. I have serious trouble with my ubuntu 11.04 installation. My ubuntu (root/home) partition keeps filling up until its totally filled up, but i dont understand by what.

The first thing i discovered was that kern.log and uwf.log was each 8gb large! It's filled with networking info. se below.

kern.log:
```
 L=64 ID=0 DF PROTO=UDP SPT=6900 DPT=20684 LEN=73 
Jul  3 08:02:51 kimothy-desktop kernel: [171281.635128] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.112 DST=95.239.138.105 LEN=93 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=6900 DPT=20684 LEN=73 
Jul  3 08:02:51 kimothy-desktop kernel: [171281.647491] [UFW AUDIT] IN=eth0 OUT= MAC=00:24:1d:21:48:72:00:23:69:21:79:60:08:00 SRC=99.251.233.215 DST=192.168.1.112 LEN=84 TOS=0x00 PREC=0x00 TTL=107 ID=47899 PROTO=UDP SPT=38500 DPT=6900 LEN=64 
Jul  3 08:02:51 kimothy-desktop kernel: [171281.665250] [UFW AUDIT] IN=eth0 OUT= MAC=00:24:1d:21:48:72:00:23:69:21:79:60:08:00 SRC=76.248.241.25 DST=192.168.1.112 LEN=159 TOS=0x00 PREC=0x00 TTL=109 ID=4677 DF PROTO=TCP SPT=5966 DPT=6918 WINDOW=257 RES=0x00 ACK PSH URGP=0 
Jul  3 08:02:51 kimothy-desktop kernel: [171281.700032] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.112 DST=76.248.241.25 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=17625 DF PROTO=TCP SPT=6918 DPT=5966 WINDOW=123 RES=0x00 ACK URGP=0 
Jul  3 08:02:51 kimothy-desktop kernel: [171281.737345] [UFW AUDIT] IN=eth0 OUT= MAC=00:24:1d:21:48:72:00:23:69:21:79:60:08:00 SRC=125.46.24.186 DST=192.168.1.112 LEN=84 TOS=0x00 PREC=0x00 TTL=110 ID=29204 PROTO=UDP SPT=8793 DPT=6900 LEN=64 
Jul  3 08:02:51 kimothy-desktop kernel: [171281.739717] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.112 DST=76.248.241.25 LEN=151 TOS=0x00 PREC=0x00 TTL=64 ID=17626 DF PROTO=TCP SPT=6918 DPT=5966 WINDOW=123 RES=0x00 ACK PSH URGP=0 
```

uwf.log:
```
 OUT=eth0 SRC=192.168.1.112 DST=123.232.124.99 LEN=157 TOS=0x00 PREC=0xC0 TTL=64 ID=65401 PROTO=ICMP TYPE=3 CODE=3 [SRC=123.232.124.99 DST=192.168.1.112 LEN=129 TOS=0x00 PREC=0x00 TTL=46 ID=1549 PROTO=UDP SPT=29663 DPT=6911 LEN=109 ] 
Jul  3 08:02:33 kimothy-desktop kernel: [171263.767490] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.112 DST=83.128.57.178 LEN=422 TOS=0x00 PREC=0x00 TTL=64 ID=20758 DF PROTO=TCP SPT=6911 DPT=60335 WINDOW=115 RES=0x00 ACK PSH URGP=0 
Jul  3 08:02:33 kimothy-desktop kernel: [171263.808295] [UFW AUDIT] IN=eth0 OUT= MAC=00:24:1d:21:48:72:00:23:69:21:79:60:08:00 SRC=83.128.57.178 DST=192.168.1.112 LEN=154 TOS=0x00 PREC=0x00 TTL=116 ID=6135 DF PROTO=TCP SPT=60335 DPT=6911 WINDOW=258 RES=0x00 ACK PSH URGP=0 
Jul  3 08:02:33 kimothy-desktop kernel: [171263.808327] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.112 DST=83.128.57.178 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=20759 DF PROTO=TCP SPT=6911 DPT=60335 WINDOW=115 RES=0x00 ACK URGP=0 
Jul  3 08:02:34 kimothy-desktop kernel: [171263.848641] [UFW AUDIT] IN=eth0 OUT= MAC=00:24:1d:21:48:72:00:23:69:21:79:60:08:00 SRC=83.128.57.178 DST=192.168.1.112 LEN=245 TOS=0x00 PREC=0x00 TTL=116 ID=6144 DF PROTO=TCP SPT=60335 DPT=6911 WINDOW=258 RES=0x00 ACK PSH URGP=0 
Jul  3 08:02:34 kimothy-desktop kernel: [171263.848657] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.112 DST=83.128.57.178 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=20760 DF PROTO=TCP SPT=6911 DPT=60335 WINDOW=123 RES=0x00 ACK URGP=0 
Jul  3 08:02:34 kimothy-desktop kernel: [171263.867974] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.112 DST=83.128.57.178 LEN=370 TOS=0x00 PREC=0x00 TTL=64 ID=20761 DF PROTO=TCP SPT=6911 DPT=60335 WINDOW=123 RES=0x00 ACK PSH URGP=0 
Jul  3 08:02:34 kimothy-desktop kernel: [171263.908362] [UFW AUDIT] IN=eth0 OUT= MAC=00:24:1d:21:48:72:00:23:69:21:79:60:08:00 SRC=83.128.57.178 DST=192.168.1.112 LEN=145 TOS=0x00 PREC=0x00 TTL=116 ID=6147 DF PROTO=TCP SPT=60335 DPT=6911 WINDOW=257 RES=0x00 ACK PSH URGP=0 
Jul  3 08:02:34 kimothy-desktop kernel: [171263.940025] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.112 DST=83.128.57.178 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=20762 DF PROTO=TCP SPT=6911 DPT=60335 WINDOW=123 RES=0x00 ACK URGP=0 
Jul  3 08:02:34 kimothy-desktop kernel: [171263.968284] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.112 DST=83.128.57.178 LEN=120 TOS=0x00 PREC=0x00 TTL=64 ID=20763 DF PROTO=TCP SPT=6911 DPT=60335 WINDOW=123 RES=0x00 ACK PSH URGP=0 
Jul  3 08:02:34 kimothy-desktop kernel: [171263.968897] [UFW AUDIT] IN=eth0 OUT= MAC=00:24:1d:21:48:72:00:23:69:21:79:60:08:00 SRC=71.65.215.168 DST=192.168.1.112 LEN=58 TOS=0x00 PREC=0x00 TTL=44 ID=15799 PROTO=UDP
```

I deleted these but it never really solved my problem, so I have kept searching for the problem and deleted as much as possible but i cant seem to find where the space have gone.

One thing I think it might be is that the fat log files I deletet in nautilus (sudo) is in roots trash bin maybe??? But i cant seem to find them, and when i open trash bin in nautilus (sudo) it crashes.

I would post a screenshot, but i cant because printscrean gives me an error because of disk space, so here in a picture i have taken.

[[img]http://bildr.no/thumb/920859.jpeg[/img]](http://bildr.no/view/920859)


Please! I need help quickly because it breaking down here!

---

### Post by coffeecat on 2011-07-04
> **kimothy1987 said:**
> One thing I think it might be is that the fat log files I deletet in nautilus (sudo) is in roots trash bin maybe??? But i cant seem to find them, and when i open trash bin in nautilus (sudo) it crashes.

I don't know why your system logs are getting so big but I agree that the deleted ones are probably still sitting in root's trash. If you open a root nautilus and simply use the delete key, that is where deleted files go. If you use a root nautilus, you need to use the shift-delete key combination to delete them completely.

To delete the files that are in root's trash, open a terminal, and:

```
sudo -i
cd /root/.local/share
rm -R Trash
```

I could have given you just one line to do that, but a single typo in it could have wiped out your complete installation, so I've given you the more long-winded, but safer version.

If by chance lack of hard drive space prevents you from even running commands in a terminal, boot up the live CD to the live desktop. Mount your Ubuntu partition from the Places sidebar in a nautilus window. Now open a terminal, and:

```
gksu nautilus
```

Navigate to /root/.local/share in your installed Ubuntu (you'll find that in /media/somethingorother/root/.local/share) and delete the Trash folder and contents with shift-delete.

---

### Post by kimothy1987 on 2011-07-04
THAT DID THE TRICK. I have 21GB free:D

Thank you so much!

I still wonder why my log files gets so big, any way to limit their size or do a clean-up or something like that???

Thanks again.

---

### Post by Grenage on 2011-07-04
> **kimothy1987 said:**
> THAT DID THE TRICK. I have 21GB free:D

Thank you so much!

I still wonder why my log files gets so big, any way to limit their size or do a clean-up or something like that???

Thanks again.

You'll want to change the ufw options; lower the logging threshold, I imagine. ;)

---

### Post by kimothy1987 on 2011-07-08
Hi. Thanks for all the help i got, but it was short lived. Now the log files has been filled up again, and i only got 1.3 gb left. kern.log and ufw.log is each 6.3GB!

[[img]http://bildr.no/thumb/923596.jpeg[/img]](http://bildr.no/view/923596)

[[img]http://bildr.no/thumb/923600.jpeg[/img]](http://bildr.no/view/923600)

What can I do??? I fills up inn less then a week!

---

### Post by LowSky on 2011-07-08
kimothy1987  the best thing to ask you is what were the last 10 things you did before the issue arose. Did you install any software?

I know it isn't the best advice but sometimes its the quickest fix. Save your data and start fresh. Just reinstall.

---

### Post by coffeecat on 2011-07-08
@kimothy1987, did you read Grenage's post? (#4). It looks as though it's ufw that's mostly responsible for spamming your logs.

---

### Post by dino99 on 2011-07-08
how are ufw settings ? (if you asked to log everything, then ...)

with synaptic, install logrotate

zeitgeist log lot of thing too, not sure you really need this stuff

---

