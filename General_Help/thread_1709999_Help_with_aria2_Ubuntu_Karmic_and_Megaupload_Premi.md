---
title: "Help with aria2 Ubuntu Karmic and Megaupload Premium"
date: 2011-03-19
forum: General Help
---

### Post by titansking on 2011-03-19
Hello,

Has anyone had luck with making aria2 work with megaupload premium accounts? I have google'd around a lot, but couldn't find anything useful out there. Maybe i am not looking at the right place!

Appreciate if anyone can help here. 

Below is my system config:
Ubuntu 9.10 (Karmic)
aria2 version 1.10.9

my aria2.conf file looks like this:

```
continue
http-user=USERNAME
http-passwd=PASSWORD
http-auth-scheme=basic
allow-overwrite=true
dir=~/Downloads/megaupload
file-allocation=prealloc
enable-http-pipelining=true
use-head=true
input-file=~/scripts/input.megaupload
log-level=debug
max-connection-per-server=2
summary-interval=120
```

I run the command to download as: 

```
aria2c --conf-path=~/.aria2/aria2.conf -l ~/scripts/aria2.log

```
After i do this, i just see an index.html thats downloaded. I think that megaupload just never takes my username/password. Below is the output of my aria2.log file.

```

2011-03-19 16:46:39.019923 INFO - [main.cc:192] <<--- --- --- ---
2011-03-19 16:46:39.020101 INFO - [main.cc:193]   --- --- --- ---
2011-03-19 16:46:39.020110 INFO - [main.cc:194]   --- --- --- --->>
2011-03-19 16:46:39.020131 INFO - [main.cc:196] Logging started.
2011-03-19 16:46:39.021053 INFO - [MultiUrlRequestInfo.cc:161] You may encounter the certificate verification error with HTTPS server. See --ca-certificate and --check-certificate option.
2011-03-19 16:46:39.021111 DEBUG - [RequestGroupMan.cc:540] 1 RequestGroup(s) added.
2011-03-19 16:46:39.021138 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:0, write:0, hup:0, err:0
2011-03-19 16:46:39.021179 DEBUG - [FeedbackURISelector.cc:171] Selected from normCands
2011-03-19 16:46:39.021193 DEBUG - [FeedbackURISelector.cc:97] FeedbackURISelector selected http://www.megaupload.com/?d=RGDXG7D8
2011-03-19 16:46:39.021238 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:0, write:0, hup:0, err:0
2011-03-19 16:46:39.026796 INFO - [AbstractCommand.cc:637] CUID#6 - Resolving hostname www.megaupload.com
2011-03-19 16:46:39.052726 DEBUG - [KqueueEventPoll.cc:241] Failed to delete socket event:Bad file descriptor
2011-03-19 16:46:39.052779 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:0, write:0, hup:0, err:0
2011-03-19 16:46:39.052825 INFO - [AbstractCommand.cc:726] CUID#6 - Name resolution complete: www.megaupload.com -> 174.140.154.13, 174.140.154.14, 174.140.154.15, 174.140.154.20, 174.140.154.21, 174.140.154.22, 174.140.154.23, 174.140.154.24, 174.140.154.12
2011-03-19 16:46:39.052886 INFO - [HttpInitiateConnectionCommand.cc:134] CUID#6 - Connecting to 174.140.154.13:80
2011-03-19 16:46:39.346217 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:0, write:1, hup:0, err:0
2011-03-19 16:46:39.346422 INFO - [HttpConnection.cc:102] CUID#6 - Requesting:
HEAD /?d=RGDXG7D8 HTTP/1.1
User-Agent: aria2/1.10.9
Accept: */*,application/metalink4+xml,application/metalink+xml
Host: www.megaupload.com
Pragma: no-cache
Cache-Control: no-cache
Authorization: Basic ********


2011-03-19 16:46:39.720918 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:39.721012 INFO - [HttpConnection.cc:150] CUID#6 - Response received:
HTTP/1.1 200 OK
Date: Sat, 19 Mar 2011 08:46:39 GMT
Server: Apache
Last-Modified: Sat, 19 Mar 2011 08:46:39 GMT
Expires: Sat, 19 Mar 2011 08:46:39 GMT
Cache-Control: no-store, no-cache, must-revalidate
Cache-Control: post-check=0, pre-check=0
Pragma: no-cache
Set-Cookie: mcpop=100931-1300610799%3B; expires=Sun, 20-Mar-2011 08:46:39 GMT; path=/; domain=.megaupload.com
Vary: Accept-Encoding
Content-Type: text/html; charset=UTF-8
2011-03-19 16:46:39.721487 DEBUG - [RequestGroup.cc:1035] Finding PreDownloadHandler for path /Users/vishal/Downloads/megaupload/index.html.
2011-03-19 16:46:39.721504 DEBUG - [RequestGroup.cc:1049] No PreDownloadHandler found.
2011-03-19 16:46:39.721548 INFO - [DownloadEngine.cc:279] Pool socket for 174.140.154.13:80
2011-03-19 16:46:39.721571 DEBUG - [AbstractCommand.cc:346] CUID#6 - Pooling request URI=http://www.megaupload.com/?d=RGDXG7D8
2011-03-19 16:46:39.721611 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:0, write:0, hup:0, err:0
2011-03-19 16:46:39.721633 DEBUG - [FileEntry.cc:177] Picked up from pool: http://www.megaupload.com/?d=RGDXG7D8
2011-03-19 16:46:39.721652 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:0, write:0, hup:0, err:0
2011-03-19 16:46:39.721671 INFO - [AbstractCommand.cc:737] CUID#6 - DNS cache hit: www.megaupload.com -> 174.140.154.13, 174.140.154.14, 174.140.154.15, 174.140.154.20, 174.140.154.21, 174.140.154.22, 174.140.154.23, 174.140.154.24, 174.140.154.12
2011-03-19 16:46:39.721690 INFO - [DownloadEngine.cc:401] Found socket for 174.140.154.13:80
2011-03-19 16:46:39.721736 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:0, write:1, hup:0, err:0
2011-03-19 16:46:39.721811 INFO - [HttpConnection.cc:102] CUID#6 - Requesting:
GET /?d=RGDXG7D8 HTTP/1.1
User-Agent: aria2/1.10.9
Accept: */*,application/metalink4+xml,application/metalink+xml
Host: www.megaupload.com
Pragma: no-cache
Cache-Control: no-cache
Authorization: Basic ********
Cookie: mcpop=100931-1300610799%3B;


2011-03-19 16:46:40.088942 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.089024 INFO - [HttpConnection.cc:150] CUID#6 - Response received:
HTTP/1.1 200 OK
Date: Sat, 19 Mar 2011 08:46:39 GMT
Server: Apache
Last-Modified: Sat, 19 Mar 2011 08:46:39 GMT
Expires: Sat, 19 Mar 2011 08:46:39 GMT
Cache-Control: no-store, no-cache, must-revalidate
Cache-Control: post-check=0, pre-check=0
Pragma: no-cache
Set-Cookie: mcpop=100931-1300610799%3B99677-1300610799%3B; expires=Sun, 20-Mar-2011 08:46:39 GMT; path=/; domain=.megaupload.com
Vary: Accept-Encoding
Transfer-Encoding: chunked
Content-Type: text/html; charset=UTF-8
2011-03-19 16:46:40.089196 DEBUG - [RequestGroup.cc:1035] Finding PreDownloadHandler for path /Users/vishal/Downloads/megaupload/index.html.
2011-03-19 16:46:40.089207 DEBUG - [RequestGroup.cc:1049] No PreDownloadHandler found.
2011-03-19 16:46:40.089335 DEBUG - [SegmentMan.cc:125] Attach segment#0 to CUID#6.
2011-03-19 16:46:40.089352 DEBUG - [SegmentMan.cc:139] index=0, length=0, segmentLength=0, writtenLength=0
2011-03-19 16:46:40.089472 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.093856 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.382658 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.383522 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.385588 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.448786 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.450439 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.681520 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.683019 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.771644 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.773431 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.773866 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.973411 DEBUG - [AbstractCommand.cc:122] CUID#6 - socket: read:1, write:0, hup:0, err:0
2011-03-19 16:46:40.973545 INFO - [DownloadCommand.cc:201] CUID#6 - The download for one segment completed successfully.
2011-03-19 16:46:40.973599 INFO - [DownloadEngine.cc:279] Pool socket for 174.140.154.13:80
2011-03-19 16:46:40.973646 DEBUG - [RequestGroup.cc:969] GID#1 - Request queue check
2011-03-19 16:46:40.973679 DEBUG - [ServerStat.cc:114] ServerStat:www.megaupload.com: singleConnectionAvgSpeed_ old:0.00KB/s new:24.24KB/s last:24.24KB/s
2011-03-19 16:46:40.973787 NOTICE - [RequestGroup.cc:1199] Download complete: /Users/vishal/Downloads/megaupload/index.html
2011-03-19 16:46:40.973819 DEBUG - [RequestGroup.cc:1057] Finding PostDownloadHandler for path /Users/vishal/Downloads/megaupload/index.html.
2011-03-19 16:46:40.973830 DEBUG - [RequestGroup.cc:1070] No PostDownloadHandler found.
2011-03-19 16:46:40.973841 DEBUG - [RequestGroup.cc:1163] GID#1 - Creating DownloadResult.
2011-03-19 16:46:40.973867 DEBUG - [RequestGroupMan.cc:459] 1 RequestGroup(s) deleted.
 
```

Appreciate any help. 

Regards,
Titan

---

