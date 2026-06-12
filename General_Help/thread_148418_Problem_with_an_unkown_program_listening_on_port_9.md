---
title: "Problem with an unkown program listening on port 9000 and slimserver"
date: 2006-03-22
forum: General Help
---

### Post by FaytlND on 2006-03-22
Hey everyone, I am having a slight problem while trying to set up slimserver.  I managed to get it installed with their package through apt-get, however I am haveing a problem running it.  It requires port 9000 to be free, but when I try to start it, the program tells me port 900 is in use.  So I ran netstat, and I get this:
```

patrick@ubuntu:~$ sudo netstat -pant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:32769         0.0.0.0:*               LISTEN     7610/hpiod
tcp        0      0 0.0.0.0:9090            0.0.0.0:*               LISTEN     7983/perl
tcp        0      0 127.0.0.1:32770         0.0.0.0:*               LISTEN     7630/python
tcp        0      0 0.0.0.0:9000            0.0.0.0:*               LISTEN     7983/perl
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     7735/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     7968/smbd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     8441/cupsd
tcp        0      0 0.0.0.0:3483            0.0.0.0:*               LISTEN     7983/perl
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     7968/smbd
tcp        0      0 192.168.0.198:60494     64.233.161.104:80       ESTABLISHED8268/firefox-bin
tcp        0      0 192.168.0.198:49419     216.109.126.70:80       CLOSE_WAIT 8212/python
tcp        0      0 192.168.0.198:43594     66.151.148.233:80       ESTABLISHED8268/firefox-bin
tcp        0      0 192.168.0.198:33271     72.246.31.35:80         ESTABLISHED8268/firefox-bin
tcp        0      0 127.0.0.1:32769         127.0.0.1:49419         ESTABLISHED7610/hpiod
tcp        0      0 127.0.0.1:631           127.0.0.1:37560         ESTABLISHED8441/cupsd
tcp        0      0 192.168.0.198:36012     72.246.31.25:80         ESTABLISHED8268/firefox-bin
tcp        0      0 127.0.0.1:49419         127.0.0.1:32769         ESTABLISHED7630/python
tcp        1      0 192.168.0.198:47153     64.233.185.19:443       CLOSE_WAIT 8200/python
tcp        1      0 192.168.0.198:47107     64.233.185.19:443       CLOSE_WAIT 8200/python
tcp        0      0 192.168.0.198:54266     72.246.31.32:80         ESTABLISHED8268/firefox-bin
tcp        0      0 127.0.0.1:37560         127.0.0.1:631           ESTABLISHED8186/gnome-cups-ico

```

So it appears there is a prgram just names 7983/perl listening on port 9000, and I have no clue what it is or how to stop it.  Any ideas?  Thanks in advance for the help.

---

### Post by Pistahh on 2006-03-22
The process with pid=7983 listens on that port. Do a 

  ps axu | grep 7983

to find out which process that is.

---

### Post by Pistahh on 2006-03-22
ps axuwww | grep 7983

is better, it shows more lines of output if the command is too long.

---

### Post by FaytlND on 2006-03-22
Thanks for the help. After doing some snooping I did figure out that it was indeed slimserver already running. The reason I could not connect was that using "localhost" did not work. My computer name is "ubuntu" and I had to go to [http://ubuntu:9000](http://ubuntu:9000) to get in. I found that out by looking at the log. All is good now.

---

