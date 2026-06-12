---
title: "Oracle SQL Developer can't connect"
date: 2011-11-21
forum: General Help
---

### Post by genoskill on 2011-11-21
I Installed Oracle Database 10g and downloaded SQL Developer. When I try to test a new connection, this appears in red letters:

[COLOR=Red]Status : Failure -Test failed: IO Error: The Network Adapter could not establish the connection[/COLOR]

I've been like 3 hours trying to solve this, but I don't know wtf to do.



---------------------------

_HOW DID I SOLVE THIS_: following this guide: [https://forums.oracle.com/forums/thread.jspa?threadID=2200434](https://forums.oracle.com/forums/thread.jspa?threadID=2200434)

and here is another one for Oracle 11g: [https://forums.oracle.com/forums/thread.jspa?threadID=2227554](https://forums.oracle.com/forums/thread.jspa?threadID=2227554)

---

### Post by genoskill on 2011-11-21
Im not using the package (RPM) that appears on the download page ([http://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/index.html](http://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/index.html))

Im using "Oracle SQL Developer for other platforms" I unzipped it. I execute it with "sqldeveloper.sh".

---

### Post by genoskill on 2011-11-22
bump post help please

---

### Post by genoskill on 2011-11-23
now I can't even start the Database because when I go to [http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex) firefox says "Unable to connect"

---

### Post by Serpher on 2011-11-23
Try connecting to the database, then immediately run the following command and post the results:

```
sudo tail -50 /var/log/messages
```

---

### Post by genoskill on 2011-12-02
Hi, since I was frustraded, I tried to install it on a debian partition. I followed this guide: 

[https://forums.oracle.com/forums/thread.jspa?threadID=2227554](https://forums.oracle.com/forums/thread.jspa?threadID=2227554)

and it worked great.

---

