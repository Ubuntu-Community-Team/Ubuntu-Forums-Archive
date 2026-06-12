---
title: "Kernel AIO - Asynchonous I/O to files"
date: 2011-02-06
forum: General Help
---

### Post by rpaskudniak on 2011-02-06
Greetings family!

I am surprised that my searches on this subject in this forum turned up zilch. I started to post this as a question but then I found the answer before posting.  But I figured it might as well be posted.

I recall using kernel asynchronous disk I/O for raw devices on RH Linux.  I used to tell the SA's how to set the KAIO-related kernel parameters but I don't recall these parameter names now. I know I installed libaio1 to support it but I need a reminder: What are the names of the KAIO parameters?

The answer, which I found on Johan Louwers Personal Blog, can be found at [_this URL_]("http://johanlouwers.blogspot.com/2010/02/aio-max-nr-parameter-for-oracle.html"), is:
```
fs.aio-max-nr
```
This defaults to 65535 but I set to to 1.5 million, just for jollies (and for my Informix server).  I set this value in /etc/sysctl.conf and immediately applied is using the command
```
sysctl -p /etc/sysctl.conf
```
You can see these parameters in action in the /proc "file system":
```
/proc/sys/fs/aio-max-nr  # Max KAIO events
/proc/sys/fs/aio-nr      # Number of AIO events now active
```
I'm happy to hear any additional related parameters.

---

