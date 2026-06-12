---
title: "FTP Syntax Help"
date: 2012-10-05
forum: General Help
---

### Post by nc_jed on 2012-10-05
I'm having a total brain fart on this.  With Command Line FTP, can I specify a remote directory in a put statement or must I CD to it and put it directly?

i.e. Will this work?
ftp ftp.server.com
login
password
put /home/me/file.txt /remote/dir/1/2/3/file.txt
bye

Or must I do this?
ftp ftp.server.com
login
password
cd /remote/dir/1/2/3/
put /home/me/file.txt file.txt
bye

Not near an FTP server right now, so I can't test it.  thanks!

-Jed




(Edit: You can use dirs in the destination syntax - I found an FTP server and tested it).

---

