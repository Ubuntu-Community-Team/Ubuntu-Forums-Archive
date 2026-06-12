---
title: "rsyslog.d usage"
date: 2011-06-07
forum: General Help
---

### Post by nanotiva on 2011-06-07
Hi

I have been trying to create an rsyslog config for a software package that I use. I want to use the local7 facility for this package, and split the messages according to priority across several files. I would like the config to be a file which can just be dropped into rsyslog.d without having to modify the rsyslog.conf or 50-defaults.conf.

I created a file called 40-test.conf, in which I have the following:

local7.none                        /var/log/messages
local7.none                        /var/log/syslog
local7.=info                    -/var/log/test.info
local7.=debug                    -/var/log/test.debug
local7.=notice;local7.=warning    -/var/log/test.notice
local7.=err                        -/var/log/test.error

I am getting the correct local7 messages in the correct 'test' files, but i am also still getting local7 messages in /var/log/messages and /var/log/syslog, so it seems the local7.none has no effect.

Is this the correct method of achieving what I want? What am I doing wrong?

Any help would be much appreciated.

---

### Post by nanotiva on 2011-06-10
Can anyone suggest a better place to post this thread where I will have a better chance of getting help?

Thanks

---

### Post by ron.kirt on 2011-08-15
I have similar problem, its logging in both /var/log/message and /var/log/boot.log

Were you able to solve it?

---

### Post by nanotiva on 2011-08-16
> **ron.kirt said:**
> I have similar problem, its logging in both /var/log/message and /var/log/boot.log

Were you able to solve it?

I was able to solve this by adding "& ~" after each line in the 40-test.conf file. So the file now looks like this:

local7.=info -/var/log/test.info
& ~
local7.=debug -/var/log/test.debug
& ~
local7.=notice;local7.=warning -/var/log/test.notice
& ~
local7.=err -/var/log/test.error
& ~

Hope this helps..

---

