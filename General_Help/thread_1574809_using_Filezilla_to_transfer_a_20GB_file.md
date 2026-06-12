---
title: "using Filezilla to transfer a 20GB file"
date: 2010-09-14
forum: General Help
---

### Post by weasker on 2010-09-14
So i have a windows vista laptop that has a 20GB file that i want to use FileZilla to transfer that over to my desktop. I installed filezilla client on both computers. For host, on vista do i type in the ip address of the ubuntu desktop and then on the ubuntu desktop type in the vista's ip address for host and use the same port numbers? using the vista's ip address as 192.168.0.3 and port 22 and the desktop address is 192.168.0.6  i am getting a message like:


Status: connecting to 192.168.0.6
Response: fzSftp started
command: open "*name*@192.168.0.6"22
Error: connection timed out
error: could not connect to server

i hit quickconnect on both sides and they both give me same results (obviously adjusted for the ip address). Could someone help me figure out what the heck i am doing? I have not used filezilla before.

---

### Post by robsoles on 2010-09-14
It sounds like you are trying to get a filezilla client to behave as server and it won't.

You would be better off just exposing a windows share on the vista machine 'in the usual way' and then trying to hit that using 'network' under 'places' on your ubuntu machine. Or you could google about setting up samba server on the ubuntu machine and then log onto that as a windows share from your vista machine.

Otherwise [http://www.google.com/search?q=ftp+server+ubuntu](http://www.google.com/search?q=ftp+server+ubuntu)

---

### Post by asmoore82 on 2010-09-14
Please don't google ubuntu+ftp+server!

Non-Anonymous FTP has been obsoleted by sFTP.

To use sFTP, simply install the OpenSSH Server Ubuntu package.
```
sudo apt-get install openssh-server
```

Then, on the vista machine, make sure to tell filezilla port "22" and it will know what to do!

EDIT: looking closer at your error message, it looks like FileZilla is already favoring sFTP/22 :cool:

---

### Post by robsoles on 2010-09-14
> **asmoore82 said:**
> Please don't google ubuntu+ftp+server!

Non-Anonymous FTP has been obsoleted by sFTP.

To use sFTP, simply install the OpenSSH Server Ubuntu package.
```
sudo apt-get install openssh-server
```

Then, on the vista machine, make sure to tell filezilla port "22" and it will know what to do!

EDIT: looking closer at your error message, it looks like FileZilla is already favoring sFTP/22 :cool:

1. I suggest to OP they use samba/windows file sharing instead.

2. It's all "in-house" - I very doubt OP is going to expose their server to the internet but of things to be wrong about this one would be less surprising to me.

3. I would be markedly surprised not to find that the majority of results for the google search "ftp server ubuntu" point out that anonymous FTP is the plague and SFTP is the way to go.


I didn't know that openssh-server automatically made SFTP service available without installing an FTP server, I'll have to try that sometime.

---

