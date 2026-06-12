---
title: "problems with proftpd"
date: 2011-06-01
forum: General Help
---

### Post by sailingbikeruk on 2011-06-01
Let me start by saying this is my first ever delve into linux! I have very limited knowledge so please be clear and concise and not assume anything. I am however an experienced IT professional albeit in Windows........ 

I needed an FTP server at work so I have setup Ubuntu 10.04 Desktop edition as a virtual machine on VMWare and installed proftpd and gadmin-proftpd.

It appears that all is OK, I can browse to the FTP site using IE, fire ftp, filezilla etc. but for some reason I get an error whenever I try to upload or download files. I will try and explain what happens

If I try to open files directly from IE such as a pdf I get a 404 file not found error

If I acces using Filezilla, I get a 550 error - no such file or directory (see log below)

Command:    OPTS UTF8 ON
Response:    200 UTF8 set to on
Status:    Connected
Status:    Starting download of /Ubiflex Application & Usage.pdf
Command:    CWD /
Response:    250 CWD command successful
Command:    PWD
Response:    257 "/" is the current directory
Command:    TYPE I
Response:    200 Type set to I
Command:    PASV
Response:    227 Entering Passive Mode (xx,xxx,xx,xx,xxx,xxx).
Command:    RETR Ubiflex Application & Usage.pdf
Response:    550 Ubiflex Application & Usage.pdf: No such file or directory
Error:    Critical file transfer error

Does anyone have any ideas?

Ian

---

