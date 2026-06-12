---
title: "Help with curl a bit"
date: 2010-08-01
forum: General Help
---

### Post by hakermania on 2010-08-01
Let's say I have a site's url. 
I have it's ftp admin username and passwd..
How can I upload there ( in / directory ) a file named app.log using curl ?
I read the manual but I understood nothing:(

---

### Post by junapp on 2010-08-01
looking at:
[http://www.astahost.com/info.php/downloadupload-file-ftp-proxy-server-39curl39_t15055.html](http://www.astahost.com/info.php/downloadupload-file-ftp-proxy-server-39curl39_t15055.html)

would this be useful?
curl --upload-file app.log --verbose -u yourusername:yourpassword [ftp://sharethespace.com:21]("ftp://sharethespace.com/")

---

### Post by hakermania on 2010-08-01
Yes the problem is that the password lefts the PC as plain text and a sniffer can "thief" it very easily

---

