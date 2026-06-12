---
title: "[Ubuntu Server] Small error connecting to vsFTP server"
date: 2010-07-17
forum: General Help
---

### Post by ZnoteOT on 2010-07-17
removed post. Too much google attention.

---

### Post by ZnoteOT on 2010-07-17
bump

---

### Post by ZnoteOT on 2010-07-17
bump

---

### Post by ZnoteOT on 2010-07-17
bump

---

### Post by ZnoteOT on 2010-07-17
Not much help to get here!

---

### Post by ZnoteOT on 2010-07-17
bump

---

### Post by ZnoteOT on 2010-08-12
bump! Does nobody know how to solve the problem? :S

1 month old and not a single member willingly to help me. :(

This forum is suppose to have 500 members online right now...

---

### Post by pipemartinm on 2010-08-12
What are the permissions on the directory? Is it readable by the FTP user you're using to connect?

---

### Post by ZnoteOT on 2010-08-12
Well I login with my ubuntu user acount over the ftp client, and I gain access to the home directory. Should I change the permissions for my own home directory?

There is no specific user for the ftp server, I just login with the same username and password as I would do over an ssh client.

Thank you so much for replying on my thread!

---

### Post by pipemartinm on 2010-08-12
Edit: Just had a look at the ubuntu config for vsftpd. It ships with write access turned off. Uncomment the following line in /etc/vsftpd.conf
```

# Uncomment this to enable any form of FTP write command.
write_enable=YES

```Then try the simple built in client rather than filezilla to test access.

```

matt@u9-nqy-net-02:~$ ftp 127.0.0.1
Connected to 127.0.0.1.
220 (vsFTPd 2.2.2)
Name (127.0.0.1:matt): matt
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> pwd
257 "/home/matt"
ftp> dir
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rw-r--r--    1 1000     1000          932 Mar 03 15:37 192.168.168.2
-rw-r--r--    1 0        0         1000000 Jun 03  2007 1meg.test
drwxr-xr-x    2 1000     1000         4096 Aug 12 10:05 Desktop
drwxr-xr-x    2 1000     1000         4096 Feb 12  2010 Documents
drwxr-xr-x    3 1000     1000         4096 Aug 06 14:33 Downloads
drwxr-xr-x    2 1000     1000         4096 Feb 12  2010 Music
drwxr-xr-x    4 1000     1000         4096 Aug 05 11:17 Pictures
drwxr-xr-x    2 1000     1000         4096 Feb 12  2010 Public
drwxr-xr-x    2 1000     1000         4096 Feb 12  2010 Templates
drwxrwxr-x    2 1000     1000         4096 May 05 10:30 Ubuntu One
drwxr-xr-x    2 1000     1000         4096 Feb 12  2010 Videos
-rw-r--r--    1 1000     1000          167 Feb 11  2010 examples.desktop
-rw-r--r--    1 1000     1000     11486661 May 05 15:46 mediawiki-1.15.3.tar.gz
-rw-r--r--    1 0        0               0 Aug 12 12:39 ping
226 Directory send OK.
ftp> mkdir test
257 "/home/matt/test" created
ftp> exit
221 Goodbye.
matt@u9-nqy-net-02:~$ touch ~/test/testfile
matt@u9-nqy-net-02:~$ ftp 127.0.0.1
Connected to 127.0.0.1.
220 (vsFTPd 2.2.2)
Name (127.0.0.1:matt): matt
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> cd test
250 Directory successfully changed.
ftp> get testfile
local: testfile remote: testfile
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for testfile (0 bytes).
226 Transfer complete.
ftp> exit
221 Goodbye.

```
The above is from a fresh install of Ubuntu 10.04 with only the write_enable setting changed from default.

---

### Post by ZnoteOT on 2010-08-15
removed post. Too much google attention.

---

### Post by pipemartinm on 2010-08-16
> **ZnoteOT said:**
> Remember I am using port 7398 not 22! I can not  use port 22, this might be the problem. So I have written Listen 7398, I  manage to connect, not to see the dir.
22? 22 is SSH not FTP, or are you trying to use FTP over SSH? If you're changing the default port, you'll need to jigger with a few things in the config file, I haven't done it myself but you'll need to set both ftp_data_port and listen_port. From your output i'm guessing listen_port should be 7398 and ftp_data_port should be 29442. You'll need to check that these are allowed through on your firewall. If it still doesn't work can you provide a copy of your vsftpd.conf (minus any sensitive information of course)

---

### Post by ZnoteOT on 2010-08-20
removed post. Too much google attention.

---

