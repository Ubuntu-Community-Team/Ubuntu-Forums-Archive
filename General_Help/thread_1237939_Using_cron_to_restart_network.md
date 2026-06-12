---
title: "Using cron to restart network"
date: 2009-08-11
forum: General Help
---

### Post by xgm541 on 2009-08-11
ok first, some background information,

I use my linux box at home as an FTP server so that I can access my files at school which is far away. My internet provider is verizon online DSL. I have a router-modem in one which acts as a NAT. In other words, all my computers connected to the router share the same external IP which is assigned to the router. Therefore, connecting to my FTP server would result in trying to connect to my router on port 21 which is not possible.

The workaround for this is using pppoeconf to give my linux box its own external IP. Now, im sure some of you may know, but verizon DSL is not the most reliable. When it rains, especially during those big thunderstorms, my modem looses internet connection. Once internet service is restored, my linux box has no internet access because of the PPPoE assigned IP which now is most likely leased to another computer outside of my reach. In any case, I cannot come home and fix this problem whenever it rains.

So my solution, as I got thanks to the guys at the wonderful IRC chat is to reset my network interfaces using the command  "sudo /etc/init.d/networking restart". Once I run that, my pppoe service assigns a new IP to my computer. But once again, I cannot be home to run the command. 

So my way of solving that is having the command run once every two days, which I am aware is possible through crontab (amirite?). BUT, reading documentation on crontab made my head hurt more than usual. 

So long story short, how do I get "sudo /etc/init.d/networking restart" to run once every two days, automatically?

---

### Post by dcstar on 2009-08-11
> **xgm541 said:**
> ok first, some background information,

I use my linux box at home as an FTP server so that I can access my files at school which is far away. My internet provider is verizon online DSL. I have a router-modem in one which acts as a NAT. In other words, all my computers connected to the router share the same external IP which is assigned to the router. Therefore, connecting to my FTP server would result in trying to connect to my router on port 21 which is not possible.
.........

No, it is possible - it is called Port Forwarding and most NAT devices do it.

---

### Post by fluffman86 on 2009-08-11
Start by creating a file with the following in it:
```

0 0 * * * root /etc/init.d/networking restart

```
and save it anywhere as network.cron

Now use terminal to cd to the directory you save network.cron and type "sudo crontab network.cron" to add your cronfile to root's list of things to do.  To view root's crontab list, type "sudo crontab -l -u root" and it should show up.  If you no longer wish to do that cron list, you can remove it with "sudo crontab -r -u root"

Just so you know, ```
0 0 * * * root /etc/init.d/networking restart
``` will restart networking (as the user root) everyday at midnight.  To do it at 2:15am, use
```
15 2 * * * root /etc/init.d/networking restart
```
or for 2:15pm, use
```
15 14 * * * root /etc/init.d/networking restart
```

I hope everyday is OK, I think that would be better than every other day.  But if you want to do it every other day, you would need to pick which days of the week to do it.  Say monday, wednesday, and friday at 2:15am:
```
15 2 * * 1,3,5 root /etc/init.d/networking restart
```
where 1,3,5 = monday, wednesday, and friday.  Notice that there are *NO SPACES* there.  Sunday can be 0 or 7.

For more information, read [http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

One more thing...why not just use port forwarding on your router to point port 21 and 22 to your ftp box?  Seems that would be a bit easier.  And hopefully, your router would also have a place to enter a DynDNS account so you could log into it that way as well.  

I'm subscribing to this, so we can discuss it more if you like, or contact me on AIM.

---

### Post by p2bc on 2009-08-12
Ok If I understand the question slash problem, you was to connect you your machine at home, when sometime the IP address from you ISP changes either dynamically or through a release and renewal. 

There are so many solution too many to list, such as running a DNS server off you machine using BIND9, but I digress.

The easiest way with the littlest work would be to use a service like [www.dyndns.org](www.dyndns.org).

You set up a free account, paid accounts have more features, but the free account will do.
 So lets say you create an account user name "fluffman86" any time you go to "fluffman86.dyndns.org" you will automatically be pointed to your computer at home.  

Now you setup up the software on your computer to update the IP address to dyndns.org, could have it do it every min, every hour, day, whatever.

I won't go into details since it is out of the scope of Linux and this forum but I am sure you can find the solution. Some major router like D-Link and Linksys have this feature built in to update dyndns.org automatically when ever there is a change in status.

---

### Post by fluffman86 on 2009-08-12
except don't use fluffman86 because I'm already signed up there.  :D

---

### Post by p2bc on 2009-08-12
Oops, sorry. When I scrolled up to see the user name I saw the wrong one, did not realize you were not the original poster.  My Bad

---

### Post by xgm541 on 2009-08-13
Thanks a lot. I tried the crontab, but everytime I tried to add network.cron it would say file not found. So i added it manually. Hopefully it will work.

as a side note, my old router's port forwarding did not work properly, but that was years ago. How do i run pppoeconf to remove the pppoe connection so i can try port forwarding on my new router. 

Thanks.

---

### Post by asmoore82 on 2009-08-13
I would disable and remove the FTP server and install the OpenSSH server.
Then you can connect to port 22 with any sftp client such as filezilla
or nautilus itself and all of your communications are secure.

Then, of course, you would have to enable forwarding for port 22.
If you stick with FTP, make sure your clients are using passive mode -
and if you are not using anonymous FTP only, prepare for the inevitable security breach.

---

