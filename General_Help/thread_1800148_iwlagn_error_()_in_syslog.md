---
title: "iwlagn error (?) in syslog"
date: 2011-07-08
forum: General Help
---

### Post by Mzwo on 2011-07-08
Hi all,

I've had a rummage around my syslog and came upon line after line of this:

```
Jul  6 01:53:14 mzwo-laptop kernel: [ 7328.739676] iwlagn 0000:05:00.0: Received BA when not expected
Jul  6 01:53:14 mzwo-laptop kernel: [ 7328.856562] iwlagn 0000:05:00.0: Received BA when not expected
Jul  6 01:53:15 mzwo-laptop kernel: [ 7329.432370] iwlagn 0000:05:00.0: Received BA when not expected
Jul  6 01:53:25 mzwo-laptop kernel: [ 7339.713339] iwlagn 0000:05:00.0: Received BA when not expected
Jul  6 01:53:25 mzwo-laptop kernel: [ 7339.781435] iwlagn 0000:05:00.0: Received BA when not expected
Jul  6 01:53:26 mzwo-laptop kernel: [ 7340.164980] iwlagn 0000:05:00.0: Received BA when not expected
Jul  6 01:53:31 mzwo-laptop kernel: [ 7345.601357] iwlagn 0000:05:00.0: Received BA when not expected
Jul  6 01:53:31 mzwo-laptop kernel: [ 7345.961447] iwlagn 0000:05:00.0: Received BA when not expected
Jul  6 01:53:31 mzwo-laptop kernel: [ 7346.039624] iwlagn 0000:05:00.0: Received BA when not expected
```

What is xubuntu (11.04) trying to tell me?

Thanks Matt

---

### Post by Rubi1200 on 2011-07-08
Apparently this has something to do with certain Intel wireless cards.

See here for more information and a possible workaround:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762007](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762007)

---

### Post by Mzwo on 2011-07-11
thanks for the link. alas, the proposed workarounds merely reduced the number of error messages (no more flooding), but hasn't made it disappear.

any suggestions?

Cheers,
Matt

---

### Post by Mzwo on 2011-07-11
Just gone back to 10.10 (I say pooh to natty) and the error has yet to be recorded. 

funny, that, since evrything else works so damn fine with 11.04. 

not.

thanks anyways,

Matt

---

