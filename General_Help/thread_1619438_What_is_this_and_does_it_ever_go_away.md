---
title: "What is this and does it ever go away?"
date: 2010-11-11
forum: General Help
---

### Post by bowens44 on 2010-11-11
I am using Ubuntu 10.10.   After closing digikam, conky shows me that digikam still has about 2.5% ram.

This is what I see when I do a ps aux |grep digikam"


```
:~/.kde/share/config$ ps aux|grep digikam
bob      16282 33.9  2.0 1131628 165804 ?      Sl   19:57   0:09 digikam -caption 'digiKam' --icon digikam
bob      16333  0.6  0.3 388072 32604 ?        Sl   19:57   0:00 kdeinit4: kio_digikamdates [kdeinit] digikamdates local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamS16282.slave-socket
bob      16334  0.3  0.3 382584 28400 ?        Sl   19:57   0:00 kdeinit4: kio_digikamalbums [kdeinit] digikamalbums local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamx16282.slave-socket
bob      16348  0.0  0.1 162444 10104 ?        S    19:57   0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamm16282.slave-socket
bob      16349  0.0  0.1 162444  9840 ?        S    19:57   0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamb16282.slave-socket
bob      16350  0.0  0.1 162444 10100 ?        S    19:57   0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamw16282.slave-socket
bob      16352  0.1  0.1 162444  9840 ?        S    19:57   0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamq16282.slave-socket
bob      16353  0.0  0.1 162444  9840 ?        S    19:57   0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamH16282.slave-socket
bob      16354  0.0  0.1 162444  9840 ?        S    19:57   0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamR16282.slave-socket
bob      16355  0.0  0.1 162444  9840 ?        S    19:57   0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamI16282.slave-socket
bob      16356  0.0  0.1 162444 10100 ?        S    19:57   0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamC16282.slave-socket
bob      16357  0.0  0.1 162444  9840 ?        S    19:57   0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamu16282.slave-socket
bob      16358  0.0  0.1 162444  9840 ?        S    19:57   0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamy16282.slave-socket
bob      16359  0.0  0.1 162444  9840 ?        S    19:57   0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamz16282.slave-socket
bob      16360  0.0  0.1 162444  9840 ?        S    19:57   0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-bob/klauncherMT2969.slave-socket local:/tmp/ksocket-bob/digikamk16282.slave-socket
```

I would expect this to free up the ram it's using after I close digikam. It doesn't.

So what is this and why doesn't free up?

If I do a killall digikam a couple of times it seems to eventually go away.

---

