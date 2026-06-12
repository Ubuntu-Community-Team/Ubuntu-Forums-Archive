---
title: "Segmentation Fault"
date: 2011-02-22
forum: General Help
---

### Post by KLStringer on 2011-02-22
I'm trying to setup Calibre and when I go to start the content server with the calibre-server command I keep getting segmentation faults in libc-2.10.1.so

I have no idea what this means or how I go about fixing it.

---

### Post by KLStringer on 2011-02-22
output of ```
dmesg | grep segfault


[18596460.237083] calibre-server[20088]: segfault at 1841a48 ip 00182f43 sp bfd1127c error 4 in libc-2.10.1.so[110000+13e000]
[18666404.390031] calibre-server[18351]: segfault at 1457a48 ip 00182f43 sp bfd1853c error 4 in libc-2.10.1.so[110000+13e000]
[18667698.416446] calibre-server[20664]: segfault at 1c8fa48 ip 00d55f43 sp bff7947c error 4 in libc-2.10.1.so[ce3000+13e000]
```

The first two lines are from trying to pass variables with the command and the last line is just the calibre-server command w/o variables.

---

### Post by K_Light2003 on 2011-03-28
I get the same when I run mine on my headless server, however it does seem to run okay. But I would like to know why as well. 

Calibre 0.7.52 on Ubuntu 10.10 maverick

```
$ dmesg | grep segfault
[   17.137956] calibre-server[775]: segfault at 4 ip 00286a7d sp bfa95100 error 4 in libpython2.7.so.1.0[21b000+134000]
[   17.151280] calibre-server[801]: segfault at 4 ip 00286a7d sp bfa95100 error 4 in libpython2.7.so.1.0[21b000+134000]
[36677.815774] calibre-server[1240]: segfault at 4 ip 002a9a7d sp bff7a1e0 error 4 in libpython2.7.so.1.0[23e000+134000]
[36677.822534] calibre-server[1245]: segfault at 4 ip 002a9a7d sp bff7a1e0 error 4 in libpython2.7.so.1.0[23e000+134000]
[45918.572941] calibre-server[1544]: segfault at 4 ip 0017ba7d sp bfb77810 error 4 in libpython2.7.so.1.0[110000+134000]
[45918.579712] calibre-server[1549]: segfault at 4 ip 0017ba7d sp bfb77810 error 4 in libpython2.7.so.1.0[110000+134000]
```When I installed the prerequisites I used :
```

sudo apt-get install xdg-utils  imagemagick python-imaging python-mechanize python-lxml python-dateutil  python-cssutils python-beautifulsoup python-dnspython python-poppler  libpodofo-utils libwmf-bin python-chm
```Installing “libpython2.7” binary package didn't fix it. I'm not overly worried, but it would be nice to know.

---

