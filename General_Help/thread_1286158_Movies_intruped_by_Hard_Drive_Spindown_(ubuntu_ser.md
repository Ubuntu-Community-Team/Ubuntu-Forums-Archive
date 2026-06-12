---
title: "Movies intruped by Hard Drive Spindown (ubuntu server)"
date: 2009-10-08
forum: General Help
---

### Post by sammcj on 2009-10-08
I'm using Ubuntu server for my NAS.
When I play a movie (shared over SMB/AFP etc...) on my desktop every 10-15mins it lags up for a few seconds then comes right...

I am aware for the hdparm -S command but it has a maximum value of 255 (this equates to about 16 minutes from memory).

I would really like my hard drives to spin down after 10 minutes unless they are being used, obviously streaming a movie does not meet the data threshold to prevent the hard drives from spinning down during use.

Can anyone help me with adjusting this?

---

### Post by jbrown96 on 2009-10-08
I'm not really sure how to do it on the server end, but you can do it for your client. I know that VLC has a buffer/cache; you could try to increase that, then when the NAS stutters, VLC can use its buffer while the HD spins up. I think that all media players have a similar setting.

I just read the man page for hdparm. I seriously doubt that hard drive spindown is causing this problem. For the drive to spindown with the maximum value, your server would have to not make any reads for 20 minutes. There's no way that samba is streaming that much in advance. You could try something like sreadahead. This should make sure that any file that's needed will be read into memory before it's needed. This may improve the situation, but Ubuntu may already have this enabled.

---

### Post by StuartN on 2009-10-08
> **sammcj said:**
> I am aware for the hdparm -S command but it has a maximum value of 255 (this equates to about 16 minutes from memory).

The -S parameter is not linear, viz:

*A  value  of zero means "timeouts are disabled": the device will not automatically enter standby mode.  Values from 1 to  240 specify multiples of 5 seconds, yielding timeouts from 5 seconds to 20 minutes.  Values from 241 to 251 specify from 1 to 11 units of 30 minutes, yielding timeouts from 30 minutes to 5.5 hours.  A value of 252 signifies a  timeout  of  21  minutes.  A value  of 253 sets a vendor-defined timeout period between 8 and 12 hours, and the value 254 is reserved.  255 is interpreted  as 21  minutes  plus  15  seconds.  Note that some older drives may have very different interpretations of these values.*

So values 1-240 go up to 20 minutes, then 241 is 30 minutes, 242 is 60 minutes, ... 251 is 5.5 hours.

---

### Post by sammcj on 2009-10-08
Great, both posts give me something to go on.

Thanks for your help.
-Sam.

---

