---
title: "rsyslog/avahi using 100% CPU"
date: 2011-04-11
forum: General Help
---

### Post by ackey on 2011-04-11
Hi Everyone,

I noticed my laptop being a bit laggy, and found that rsyslog and avahi-daemon are using most of my CPU and a huge hunk of memory.  The answer (initially) was that I had tried to set up postfix awhile ago, and gave up without setting it up properly.  It was trying to send mail and failing - generating huge amounts of log messages.

I uninstalled postfix and restarted.  It hasn't fixed my rsyslog/avahi problem and I am out of ideas.  I see that there is an avahi-daemon error message being output about half a million times a second.  
 ```

Apr 11 16:00:01 whobuntu CRON[3520]: (ackey) MAIL (mailed 14 bytes of output but got status 0x0001#012)
Apr 11 16:00:01 whobuntu avahi-daemon[892]: server.c: Packet too short or invalid while reading response record. (Maybe a UTF-8 problem?)
Apr 11 16:01:02 whobuntu avahi-daemon[892]: last message repeated 436274 times
Apr 11 16:02:03 whobuntu avahi-daemon[892]: last message repeated 440105 times
Apr 11 16:02:37 whobuntu avahi-daemon[892]: last message repeated 253717 times
Apr 11 16:02:37 whobuntu ntpd_initres[1422]: host name not found: clock.tricity.wsu.edu
Apr 11 16:02:37 whobuntu avahi-daemon[892]: server.c: Packet too short or invalid while reading response record. (Maybe a UTF-8 problem?)
Apr 11 16:03:02 whobuntu avahi-daemon[892]: last message repeated 219811 times
Apr 11 16:03:02 whobuntu /usr/bin/crontab[3896]: (ackey) LIST (ackey)
Apr 11 16:03:02 whobuntu avahi-daemon[892]: server.c: Packet too short or invalid while reading response record. (Maybe a UTF-8 problem?)


```
And my uname info is:
```

Linux whobuntu 2.6.32-31-generic #60-Ubuntu SMP Thu Mar 17 22:14:33 UTC 2011 i686 GNU/Linux

```

In my attempt to get mail working I installed other mail programs, but I don't remember which ones.  I assume they are borking avahi, but I don't know how to find out what is calling it.

Any and all debugging help is appreciated.

---

### Post by ackey on 2011-04-11
Interestingly this appears to only occur on my wired network and not the wireless network.  That makes me think it has nothing to do with sending mail.

---

