---
title: "Getting FlashPlayer segfaults in my /var/log/messages file"
date: 2011-05-03
forum: General Help
---

### Post by laredotornado on 2011-05-03
Hi,

I'm using Ubuntu 11.04.  In my /var/log/messages file I'm getting all these bizarre seg faults.  I have the latest Firefox browser installed and the latest Flash plugin (10.2).  Yet, I'm still seeing these errors …

```

May  2 11:38:11 my-machine kernel: [246508.732097] npviewer.bin[24675]: segfault at 418 ip 00000000f60a0d36 sp 00000000ff9e3e68 error 6 in libflashplayer.so[f5e33000+b5
f000]
May  2 11:38:32 my-machine kernel: [246530.050836] lo: Disabled Privacy Extensions
May  2 11:38:51 my-machine kernel: [246548.376583] npviewer.bin[25089]: segfault at 418 ip 00000000f5ff0d36 sp 00000000ffc31d68 error 6 in libflashplayer.so[f5d83000+b5
f000]
May  2 11:39:02 my-machine kernel: [246559.556561] npviewer.bin[25264]: segfault at 0 ip 00000000f6121951 sp 00000000ff975b90 error 4 in libflashplayer.so[f5d59000+b5f0
00]
May  2 11:39:12 my-machine kernel: [246569.947476] npviewer.bin[25443]: segfault at 8 ip 00000000f608394a sp 00000000ffbe1eb0 error 4 in libflashplayer.so[f5e15000+b5f0
00]
May  2 11:39:20 my-machine kernel: [246577.604975] npviewer.bin[25567]: segfault at 418 ip 00000000f609fd36 sp 00000000ff94d4d8 error 6 in libflashplayer.so[f5e32000+b5
f000]
May  2 11:40:39 my-machine kernel: [246656.302675] lo: Disabled Privacy Extensions
May  2 11:40:52 my-machine kernel: [246669.390331] npviewer.bin[26479]: segfault at 418 ip 00000000f5fdfd36 sp 00000000ffbe4718 error 6 in libflashplayer.so[f5d72000+b5f000]

```


Any idea what they mean and how I can resolve them? - Dave

---

### Post by dentament on 2011-08-23
see this:
[http://www.elfnet.org/2010/11/29/npviewer-bin-segfault-libflashplayer-so/](http://www.elfnet.org/2010/11/29/npviewer-bin-segfault-libflashplayer-so/)

---

