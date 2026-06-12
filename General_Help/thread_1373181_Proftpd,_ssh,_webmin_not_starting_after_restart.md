---
title: "Proftpd, ssh, webmin not starting after restart"
date: 2010-01-05
forum: General Help
---

### Post by black669 on 2010-01-05
Hi everybody!!
  I am using Ubuntu 9.10 and I have a problem with proftpd, ssh and webmin, they are not starting at startup anymore. I am absolutelly clueless how to fix this. The only way to start them remotely is by connecting with VNC to the computer and starting them via terminall.
  If u can please help me in this matter...THX in advance!!!

---

### Post by black669 on 2010-01-05
It seems the only way i can start them is by issuing theese commands in terminal : 

```

sudo /etc/init.d/ssh start
sudo /etc/init.d/proftpd start
sudo /etc/init.d/webmin start

```

---

### Post by Lars Noodén on 2010-01-05
Try setting them to go at start up:

```

# clear the deck
sudo update-rc.d -f **ssh** remove

# start daemon at default run levels
sudo update-rc.d **ssh** defaults

```

You may not want to use FTP at all.  OpenSSH has a built-in SFTP client.  You can access your machine **more** securely using SFTP than via FTPS, and old FTP is not secure at all.  

FileZilla, Nautilus, Konqueror, Fugu, Fetch, Dolphin and others support sftp.  Use a url like this:  sftp://black669@server.example.org/

---

### Post by black669 on 2010-01-05
THANK you verry much for the info on sftp, I'll definatelly give it a try!!!!
Unfortunately the main problem is still unsolved, ssh not starting:(

---

