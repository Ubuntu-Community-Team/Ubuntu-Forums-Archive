---
title: "Hamachi on 9.10"
date: 2009-12-13
forum: General Help
---

### Post by Quarkrad on 2009-12-13
Think I've done all I need.  If I enter the command **hamachi-init** I get this in terminal:

Initializing Hamachi configuration (/home/dad/.hamachi). Please wait ..

  generating 2048-bit RSA keypair .. ok
  making /home/dad/.hamachi directory .. ok
  saving /home/dad/.hamachi/client.pub .. failed


If I then enter **hamachi start** I get:

dad@dadubuntu:~$ hamachi start
13 09:31:53.747 [   0] [ 5475] tap: connect() failed 2 (No such file or directory)

I've managed to get hamachi working on one 9.10 pc - having trouble on this one!  Any help appreciated.

---

### Post by cyb3rkn19ht on 2010-01-14
To fix the first problem delete all the files in folder /home/dad/.hamachi. Then run **hamachi-init** again.
The second problem is fixed by running the following code in a terminal.
```
sudo chmod 777 /var/run/tuncfg.sock
```Tell me if you get **go-online <network>** working, I can't :(

---

