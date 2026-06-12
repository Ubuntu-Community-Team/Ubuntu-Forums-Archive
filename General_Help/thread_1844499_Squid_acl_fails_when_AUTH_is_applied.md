---
title: "Squid acl fails when AUTH is applied"
date: 2011-09-15
forum: General Help
---

### Post by weird0.kid on 2011-09-15
Hi

I have been running squid for a while now and i am very happy with it.

I recently starting playing around with AD authentication with squid3 / samba (following this howto as a guideline: [http://wiki.squid-cache.org/ConfigExamples/Authenticate/WindowsActiveDirectory](http://wiki.squid-cache.org/ConfigExamples/Authenticate/WindowsActiveDirectory) ).  

The authentication works fine...
except that its ignoring a few of my ACL's.

example:
acl badsites dstdom_regex -i "/etc/squid3/badsites"
http_access deny badsites

acl blockfiles urlpath_regex "/etc/squid3/blocks.files.acl"
http_access deny blockfiles

It allows everything!

however it still applies my delay pool entries:

acl school_times time MTWHF 07:30-15:00
acl time_sites dstdom_regex -i "/etc/squid3/limit"
delay_pools 1
delay_class 1 1
delay_parameters 1 8/16
delay_access 1 allow time_sites school_times


I am a bit stuck as to why.  Any suggestions of where i could go look to fixing this problem?

thanks

---

### Post by warnewed on 2011-09-15
i don't able to understand this so wait for few then i will give you your response.
 
[EZ Breathe](http://ezbreatheventilationsystem.posterous.com/ez-breathe-ventilation-system-review-breathe)

---

