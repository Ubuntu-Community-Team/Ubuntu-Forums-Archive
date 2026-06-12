---
title: "upload file to my server"
date: 2011-03-08
forum: General Help
---

### Post by vivek.pandey on 2011-03-08
hi everyone
  i have apache server running on my laptop. i am trying to upload files on it. i tied from terminal first connecting to server by ftp and then put but i am getting an error
```


vivek@NEO:~$ ftp localhost
Connected to localhost.localdomain.
220 (vsFTPd 2.3.0)
Name (localhost:vivek): vivek
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> put
(local-file) /home/vivek/1.html
(remote-file) /var/www/1001.html
local: /home/vivek/1.html remote: /var/www/1001.html
200 PORT command successful. Consider using PASV.
550 Permission denied.
ftp> 

```
i have one method in which i can save the file in /var/www but that wont be uploading..
tried filezilla
when the local site(/homevivek/new.txt) as same as remote the file is transfered to the same place and not to the server and when i change remote site to /var/www there is an error 
anyone please help me
thanx to all in advance

---

### Post by vivek.pandey on 2011-03-08
bump?

---

### Post by vivek.pandey on 2011-03-09
double bump?

---

### Post by Habitual on 2011-03-09
Have a look over this link:
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)

---

### Post by vivek.pandey on 2011-03-09
> **Habitual said:**
> Have a look over this link:
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)

thanx for your help
i am getting following error

vivek@NEO:~$ sudo /etc/init.d/vsftpd start Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start vsftpd
vivek@NEO:~$ service vsftpd start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.81" (uid=1000 pid=21123 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
vivek@NEO:~$ 

i also checked conf file but couldnt find any connection to the error

---

