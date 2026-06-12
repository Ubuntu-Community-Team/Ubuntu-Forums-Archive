---
title: "Ubuntu asterisk users ... I'm looking for help regarding voicemail"
date: 2009-07-30
forum: General Help
---

### Post by sr_guy on 2009-07-30
I am having an issue with the asterisk voicemail operator and regular voicemails are either garbled, or the voicemail or operator voices breakup. I'm not sure why. My default format for both voicemails and operator voice are wav format. At the time I was initially setting up and testing the asterisk VM I was not running any CPU intensive tasks.

I'm also running Mythtv backend & Frontend on this same machine. Even with those elements my live inbound/outbound calls sound crystal clear with no issues. Just the weird voicemail breakup issue.

My System:

-AMD Athlon 64(tm) Dual Core 2.8Ghz
-4Gig of DDR2 Ram
-OS Ubuntu 8.10 w/ Kernel Version 2.6.27-14-generic
-Asterisk version 1.4.22
-Running FreeBX 2.5.1.5
-120gig hdd


voicemail.conf


```
; website to fix voicemail permissions issue
; [http://www.trixbox.org/forums/trixbox-forums/help/voicemail-problem-11](http://www.trixbox.org/forums/trixbox-forums/help/voicemail-problem-11)

[default]
format=wav
1001 => 5101,First Extension,myemail@gmail.com,,attach=yes|saycid=yes|envelope=no|delete=no
```


Any suggestions or help is appreciated.

---

### Post by sr_guy on 2009-07-31
As an added test, I watched both "top" and FreePBX System Statistics and CPU utilization never topped past 1-7%

Memory utilization never topped past 9%.

---

