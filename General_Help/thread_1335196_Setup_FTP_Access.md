---
title: "Setup FTP Access"
date: 2009-11-23
forum: General Help
---

### Post by CrusaderAD on 2009-11-23
How can I setup FTP access to my Ubuntu server? Can someone point me to some tutorials? Thanks!

---

### Post by Giblet5 on 2009-11-23
Open the Synaptic Package Manager (System -> Administration -> Synaptic)

Click the "Search" button.

Enter vsftpd and do the search.

Select vsftpd for install. (Very Safe FTP Daemon)

When it's done, you can ftp to your system.

You'll want to configure it probably. It's pretty easy and the config is nicely commented.

```
sudo gedit /etc/vsftpd.conf
```

Mark this thread solved when you're satisfied. (Thread Tools at the top)

---

### Post by CrusaderAD on 2009-11-23
Cool, thanks! Two questions. When users login to the ftp, they will be using their respective user names made on the system which will log them into their home directory right? Second, I think I need to enable my firewall to give privedges... if it doesn't allow it, would I get this error?

Status:	Connection attempt failed with "ECONNREFUSED - Connection refused by server".

---

### Post by Giblet5 on 2009-11-23
I think vsftpd (on this release) configures "anonymous only" ftp service (by default).

Edit the config to allow user accounts as well (local_enable=YES and write_enable=YES), then restart the service via ```
sudo /etc/init.d/vsftpd restart
```

Yes, if you're using a firewall, you'll have to open port 21 to allow FTP traffic through. Most firewalls just call it "FTP"...

---

### Post by CrusaderAD on 2009-11-23
Can you limit directory browsing?

---

### Post by CrusaderAD on 2009-11-23
Nm, got it... it's an option in the vsftpd.conf file. Thanks for the help!

---

