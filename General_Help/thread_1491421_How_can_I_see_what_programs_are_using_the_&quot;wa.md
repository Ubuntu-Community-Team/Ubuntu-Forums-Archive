---
title: "How can I see what programs are using the &quot;wa&quot;-part of the CPU?"
date: 2010-05-23
forum: General Help
---

### Post by motin on 2010-05-23
I often find the system sluggish and with CPU usage on 100%. A large percentage is usually "wa" type of cpu usage, but not top neither htop can tell me what program is actually using this part of the cpu... It seems only able to show "us" and/or "sy" parts...?

This leads to having to guess to what program is actually slowing the computer down by lots. Not very efficient...

How can I see what programs are using the "wa"-part of the CPU?

---

### Post by motin on 2010-05-23
I seem to be looing for the iotop program...

[http://www.linuxquestions.org/questions/linux-software-2/how-do-i-identify-what-process-are-making-up-the-wa-statistic-692545/](http://www.linuxquestions.org/questions/linux-software-2/how-do-i-identify-what-process-are-making-up-the-wa-statistic-692545/)

But then because of the messages within, I stumbled upon
[https://bugs.launchpad.net/ubuntu/+source/iotop/+bug/513127](https://bugs.launchpad.net/ubuntu/+source/iotop/+bug/513127)

Where a comment mentions that htop has IO columns as well, accessed by F2-Setup -> Columns. 

The IO columns greatly shows what programs are using the most IO and thus are most probable of causing the IO wait CPU blockage...

---

