---
title: "Hellanzb 0kb/s"
date: 2011-08-11
forum: General Help
---

### Post by Micheal_Schumacher on 2011-08-11
Hi guys ;)

hellanzb_0.13-6.1_all.deb 

is what i have installed, got it configured perfectly imo but for some reason im getting this error in a log file...

2011-08-11 05:41:26,507 hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
2011-08-11 05:41:26,512 Using: Twisted-10.2.0
2011-08-11 05:41:26,512 python: 2.7.1+ (r271:86832, Apr 11 2011, 18:05:24) 
2011-08-11 05:41:26,512 [GCC 4.5.2]
2011-08-11 05:41:26,512 os: Linux-2.6.38-10-generic (i686)
2011-08-11 05:41:26,513 initFillServers: fillserver support disabled
2011-08-11 05:41:26,515 recoverStateFromDisk recovered: RecoveredState: version: 0.13 newzbinCookie keys: []
downloading: {u'education.pdf': {u'totalBytes': u'2939461209', u'id': 0, u'name': u'education.pdf'}}
processing: {}
queued: {}
2011-08-11 05:41:26,773 stdinEchoOff - OFF
2011-08-11 05:41:26,810 virginmedia[0] CONNECTION MADE
2011-08-11 05:41:26,821 virginmedia[1] CONNECTION MADE
2011-08-11 05:41:26,829 virginmedia[2] CONNECTION MADE
2011-08-11 05:41:26,842 virginmedia[3] CONNECTION MADE
2011-08-11 05:41:26,855 virginmedia[4] CONNECTION MADE
2011-08-11 05:41:26,868 virginmedia[0] MODE READER successful
2011-08-11 05:41:26,869 virginmedia[5] CONNECTION MADE
2011-08-11 05:41:26,877 virginmedia[2] MODE READER successful
2011-08-11 05:41:26,878 virginmedia[6] CONNECTION MADE
2011-08-11 05:41:26,879 virginmedia[1] MODE READER successful
2011-08-11 05:41:26,890 virginmedia[7] CONNECTION MADE
2011-08-11 05:41:26,894 virginmedia[3] MODE READER successful
2011-08-11 05:41:26,909 virginmedia[4] MODE READER successful
2011-08-11 05:41:26,911 virginmedia[8] CONNECTION MADE
2011-08-11 05:41:26,918 virginmedia[9] CONNECTION MADE
2011-08-11 05:41:26,922 virginmedia[5] MODE READER successful
2011-08-11 05:41:26,926 virginmedia[2] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:26,926 virginmedia[2] CONNECTION LOST
2011-08-11 05:41:26,930 virginmedia[6] MODE READER successful
2011-08-11 05:41:26,930 virginmedia[0] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:26,931 virginmedia[0] CONNECTION LOST
2011-08-11 05:41:26,935 virginmedia[1] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:26,936 virginmedia[1] CONNECTION LOST
2011-08-11 05:41:26,938 virginmedia[7] MODE READER successful
2011-08-11 05:41:26,944 virginmedia[3] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:26,944 virginmedia[3] CONNECTION LOST
2011-08-11 05:41:26,959 virginmedia[4] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:26,959 virginmedia[4] CONNECTION LOST
2011-08-11 05:41:26,966 virginmedia[9] MODE READER successful
2011-08-11 05:41:26,970 virginmedia[8] MODE READER successful
2011-08-11 05:41:26,972 virginmedia[5] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:26,972 virginmedia[5] CONNECTION LOST
2011-08-11 05:41:26,981 virginmedia[6] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:26,981 virginmedia[6] CONNECTION LOST
2011-08-11 05:41:26,987 virginmedia[7] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:26,988 virginmedia[7] CONNECTION LOST
2011-08-11 05:41:27,015 virginmedia[9] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:27,016 virginmedia[9] CONNECTION LOST
2011-08-11 05:41:27,030 virginmedia[8] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:27,031 virginmedia[8] CONNECTION LOST
2011-08-11 05:41:28,443 virginmedia[8] CONNECTION MADE
2011-08-11 05:41:28,501 virginmedia[8] MODE READER successful
2011-08-11 05:41:28,558 virginmedia[8] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:28,559 virginmedia[8] CONNECTION LOST
2011-08-11 05:41:29,127 virginmedia[8] CONNECTION MADE
2011-08-11 05:41:29,174 virginmedia[8] MODE READER successful
2011-08-11 05:41:29,224 virginmedia[8] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:29,225 virginmedia[8] CONNECTION LOST
2011-08-11 05:41:30,285 virginmedia[8] CONNECTION MADE
2011-08-11 05:41:30,333 virginmedia[8] MODE READER successful
2011-08-11 05:41:30,382 virginmedia[8] AUTHINFO failed: 502 Authentication Failed
2011-08-11 05:41:30,383 virginmedia[8] CONNECTION LOST

Virginmedia does not require any authentication i have the username and password set to None python's default value for such action so im at a loss here. I like my programs to be terminal based so i can get myself in tune with command line tasks. It's not a firewall issue or anything like that im pretty sure of it.

---

