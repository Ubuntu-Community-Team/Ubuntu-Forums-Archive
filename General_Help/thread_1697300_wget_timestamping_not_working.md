---
title: "wget timestamping not working?"
date: 2011-02-28
forum: General Help
---

### Post by mclaborn on 2011-02-28
I'm trying to use --timestamping on wget to avoid downloading large files that have not changed. Below is my output.  The timestamp on the locally saved file matches that in the Last-Modified header, yet every time I issue the wget, it downloads the file again.  What am I missing?



[FONT=Courier New]**wget --verbose --timestamping --server-response --directory-prefix=/home/mclaborn/jOERun/Mailer --no-directories [http://172.16.0.197:8881/ServerInventory/guiapp.jar](http://172.16.0.197:8881/ServerInventory/guiapp.jar)**
--2011-02-28 15:50:13--  [http://172.16.0.197:8881/ServerInventory/guiapp.jar](http://172.16.0.197:8881/ServerInventory/guiapp.jar)
Connecting to 172.16.0.197:8881... connected.
HTTP request sent, awaiting response... 
  HTTP/1.1 200 OK
  Server: nginx/0.7.67
  Date: Mon, 28 Feb 2011 21:50:14 GMT
  Content-Type: application/java-archive
  Connection: keep-alive
  ETag: W/"5485601-1298927962000"
  Last-Modified: Mon, 28 Feb 2011 21:19:22 GMT
  Content-Length: 5485601
Length: 5485601 (5.2M) [application/java-archive]
Saving to: `/home/mclaborn/jOERun/Mailer/guiapp.jar'

100%[============================================================================================================================================================================>] 5,485,601    154K/s   in 33s     

2011-02-28 15:50:47 (160 KB/s) - `/home/mclaborn/jOERun/Mailer/guiapp.jar' saved [5485601/5485601]

**TZ="UTC" ls -alh --time-style=full-iso /home/mclaborn/jOERun/Mailer/guiapp.jar**
-rw-r--r-- 1 mclaborn mclaborn 5.3M 2011-02-28 21:19:22.000000000 +0000 /home/mclaborn/jOERun/Mailer/guiapp.jar
[/FONT]

---

