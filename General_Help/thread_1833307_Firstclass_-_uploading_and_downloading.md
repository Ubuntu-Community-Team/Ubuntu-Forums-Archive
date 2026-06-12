---
title: "Firstclass - uploading and downloading"
date: 2011-08-25
forum: General Help
---

### Post by fuzzy_onion on 2011-08-25
I've installed firstclass, which I need for my school email.  I works great until I try to download or upload anything when the program crashes.  I've installed v 10.014 from the firstclass website.

---

### Post by goodbye-windows(tm) on 2011-09-08
I had a problem also. Do you have a 32 bit computer? The company says it won't run on a 32 bit machine.

I downloaded an older version directly from terminal emulator, according to a message here in the forum, but had difficulties as well.

My error from the terminal was:

[COLOR=Red][B]art@ubuntu:~$ wget -c [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
--2011-09-08 00:46:17--  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Resolving www3.firstclass.com... 198.133.37.8
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10310832 (9.8M) [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

97% [=====================================> ] 10,104,064  80.6K/s   in 2m 4s   

2011-09-08 00:48:22 (79.5 KB/s) - Read error at byte 10104064/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:48:23--  (try: 2)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 206768 (202K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,105,944  --.-K/s   in 0.04s   

2011-09-08 00:48:23 (51.1 KB/s) - Read error at byte 10105944/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:48:25--  (try: 3)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 204888 (200K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,107,824  --.-K/s   in 0.04s   

2011-09-08 00:48:26 (44.0 KB/s) - Read error at byte 10107824/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:48:29--  (try: 4)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 203008 (198K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,109,704  --.-K/s   in 0.03s   

2011-09-08 00:48:29 (53.5 KB/s) - Read error at byte 10109704/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:48:33--  (try: 5)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 201128 (196K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,111,584  --.-K/s   in 0.03s   

2011-09-08 00:48:33 (53.4 KB/s) - Read error at byte 10111584/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:48:38--  (try: 6)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 199248 (195K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,113,464  --.-K/s   in 0.03s   

2011-09-08 00:48:38 (52.6 KB/s) - Read error at byte 10113464/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:48:44--  (try: 7)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 197368 (193K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,115,344  --.-K/s   in 0.03s   

2011-09-08 00:48:44 (52.5 KB/s) - Read error at byte 10115344/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:48:51--  (try: 8)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 195488 (191K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,117,224  --.-K/s   in 0.03s   

2011-09-08 00:48:52 (52.6 KB/s) - Read error at byte 10117224/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:49:00--  (try: 9)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 193608 (189K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,119,104  --.-K/s   in 0.04s   

2011-09-08 00:49:00 (51.2 KB/s) - Read error at byte 10119104/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:49:09--  (try:10)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 191728 (187K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,120,984  --.-K/s   in 0.04s   

2011-09-08 00:49:09 (51.8 KB/s) - Read error at byte 10120984/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:49:19--  (try:11)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 189848 (185K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,122,864  --.-K/s   in 0.03s   

2011-09-08 00:49:19 (53.3 KB/s) - Read error at byte 10122864/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:49:29--  (try:12)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 187968 (184K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,124,744  --.-K/s   in 0.03s   

2011-09-08 00:49:30 (52.8 KB/s) - Read error at byte 10124744/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:49:40--  (try:13)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 186088 (182K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,126,624  --.-K/s   in 0.03s   

2011-09-08 00:49:40 (52.6 KB/s) - Read error at byte 10126624/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:49:50--  (try:14)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 184208 (180K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,128,504  --.-K/s   in 0.03s   

2011-09-08 00:49:50 (53.0 KB/s) - Read error at byte 10128504/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:50:00--  (try:15)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 182328 (178K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,130,384  --.-K/s   in 0.03s   

2011-09-08 00:50:00 (52.7 KB/s) - Read error at byte 10130384/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:50:10--  (try:16)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 180448 (176K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,132,264  --.-K/s   in 0.04s   

2011-09-08 00:50:10 (51.8 KB/s) - Read error at byte 10132264/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:50:20--  (try:17)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 178568 (174K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,134,144  --.-K/s   in 0.03s   

2011-09-08 00:50:21 (52.7 KB/s) - Read error at byte 10134144/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:50:31--  (try:18)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 176688 (173K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,136,024  --.-K/s   in 0.03s   

2011-09-08 00:50:31 (52.8 KB/s) - Read error at byte 10136024/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:50:41--  (try:19)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 174808 (171K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,137,904  --.-K/s   in 0.03s   

2011-09-08 00:50:41 (54.9 KB/s) - Read error at byte 10137904/10310832 (Connection reset by peer). Retrying.

--2011-09-08 00:50:51--  (try:20)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 172928 (169K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,139,784  --.-K/s   in 0.04s   

2011-09-08 00:50:51 (52.2 KB/s) - Read error at byte 10139784/10310832 (Connection reset by peer). Giving up.

[/B][/COLOR]
I'm not sure what's going on as I am new to linux. The older version seemed like the way to go, but there is still some sort of issue.

Regards,

Art

---

