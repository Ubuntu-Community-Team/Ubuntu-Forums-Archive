---
title: "pure-ftpd problem"
date: 2011-03-17
forum: General Help
---

### Post by peenta on 2011-03-17
Okey, so the thing is i want to have a FTP server for me and some friends to use on my computer running Ubuntu 10.10.
I have installed pure-ftpd and pureadmin and it works fine to connect and use if i use /home/ftpuser but since my hdd with Ubuntu aint that big i want to use my other hdd with 2TB /media/Storage/Share

I have a user called joe connected to /home/fpsuser and that works fine
But my users called ftp and curse that is connected to /media/storage/Share

gets ```
Status:    Resolving address of localhost
Status:    Connecting to [::1]:21...
Status:    Connection established, waiting for welcome message...
Response:    220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:    220-You are user number 1 of 50 allowed.
Response:    220-Local time is now 23:39. Server port: 21.
Response:    220-This is a private system - No anonymous login
Response:    220 You will be disconnected after 15 minutes of inactivity.
Command:    USER Curse
Response:    331 User Curse OK. Password required
Command:    PASS *****
Response:    530 Login authentication failed
Error:    Critical error
Error:    Could not connect to server
```and from pureadmin i get ```
pure-ftpd: (?@localhost) [INFO] New connection from localhost
Mar 17 23:39:55 Mark pure-ftpd: (?@localhost) [INFO] PAM_RHOST enabled. Getting the peer address
Mar 17 23:40:01 Mark pure-ftpd: (?@localhost) [WARNING] Authentication failed for user [Curse]
Mar 17 23:40:01 Mark pure-ftpd: (?@localhost) [INFO] Logout.

```I did try to change premissions on media and Storage to same that i have on /home/ftpuser and /media/Storage/Share but nothing changed

what do i have to do to be able to get users "home" in /media/Storage/Share ?

been using Ubuntu for over a year but please explain it simple :p thanks!

---

### Post by peenta on 2011-03-18
fooled around with the settings and saw that ftp and curse used wasn't added to ftpuser group :P

---

