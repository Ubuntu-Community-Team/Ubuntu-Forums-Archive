---
title: "FTP user access probelm"
date: 2012-06-21
forum: General Help
---

### Post by suresh_vandiyur on 2012-06-21
Hi All,

I am using proftpd ftp server in ubuntu server. Am not able find the configuration file of the proftpd ftp server. i checked in /etc (like /etc/proftpd)and /usr/share/proftpd,/usr/local/proftpd/, there is no directory called proftpd. please help me where is located the proftpd config file.

Thank you,

Regards,
Suresh Babu

---

### Post by spikoley on 2012-06-21
It's been a while since I set it up, but I found some [documentation]("https://help.ubuntu.com/community/ProFTPD") that says it's here /etc/proftpd/proftpd.conf.  Most configuration files are found in /etc.

You can always use *locate* to find a file.  First you update the DB.

```
sudo updatedb
```

```
locate proftpd.conf
```

or you can use the *find* command.

```
man find
```

---

