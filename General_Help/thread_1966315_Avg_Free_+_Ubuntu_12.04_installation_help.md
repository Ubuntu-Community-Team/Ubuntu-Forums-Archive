---
title: "Avg Free + Ubuntu 12.04 installation help"
date: 2012-04-27
forum: General Help
---

### Post by mobal on 2012-04-27
Hello!

I have some problem with the Avg Free installer. I know av is not necessary but i need one.

So my problem:

```
mobal@endeavour:~$ sudo apt-get install -f
[sudo] password for mobal: 
Csomaglisták olvasása… Kész0%
Függ&#337;ségi fa építése       
Állapotinformációk olvasása… Kész
0 frissített, 0 újonnan telepített, 0 eltávolítandó és 1 nem frissített.
1 nincs teljesen telepítve/eltávolítva.
A m&#369;velet után 0 B lemezterület kerül felhasználásra.
Beállítás: avg2012flx (2012.1786) ...
Installing 'avgd' service initscripts...
ln: ”/etc/init.d/avgd” szimbolikus link létrehozása meghiúsult: A fájl már létezik
dpkg: hibás feldolgozás: avg2012flx (--configure):
 installed post-installation script alfolyamat 1 hibakóddal kilépett
Hibák történtek a feldolgozáskor:
 avg2012flx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Sorry for my language - hungarian - but u can see the error!

mobal,

---

### Post by techsupport on 2012-04-27
I don't recommend AVG. Use ClavAV (free) or Bitdefender (free for one year), it is down this list:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

:guitar:

---

### Post by mobal on 2012-04-27
> **techsupport said:**
> I don't recommend AVG. Use ClavAV (free) or Bitdefender (free for one year), it is down this list:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

:guitar:

Hello!

Yes, i know, i know but i need avg. So. No solution? The deb package is simply not compatible with 12.04?

---

### Post by rcain on 2012-07-11
Hi Mobal,
I have just experienced similar problem. Vis:

1) visited [http://free.avg.com/gb-en/download.prd-alf.line-2012](http://free.avg.com/gb-en/download.prd-alf.line-2012) - and selected:
[URL="http://download.avgfree.com/filedir/inst/avg2012flx-r1793-a5062.i386.deb"]AVG Free Edition for Linux
 (avg2012flx-r1793-a5062.i386.deb)[/URL]
 
- selected 'open with ubuntu software centre'

2) it automatically ran download and install - which worked fine up until last few lines of install script where it said: 

"...
Package Operation Failed. Registering with license ... yada yada...

/usr/bin/avgctl : 17 : exec : /opt/avg/av/bin/avgctl : not found

dpkg error processing avg2012flx (-install) : sub process installed post installation script returned error exit status 127 : errors were encountered while processing avg2012flx
..."

BUT - ubuntu software centre flags it as INSTALLED (and says "...these programs must be run from a terminal - avgfctl, avgctl, etc etc"

3) so, i checked in:

rcain@ubuntu:~$ cd /usr/bin
rcain@ubuntu:/usr/bin$ ls -l avg*
lrwxrwxrwx 1 root bin 29 Jun 11 13:13 avgcfgctl -> /opt/avg/av/bin/avgwrapper.sh
lrwxrwxrwx 1 root bin 29 Jun 11 13:13 avgctl -> /opt/avg/av/bin/avgwrapper.sh
lrwxrwxrwx 1 root bin 29 Jun 11 13:13 avgdiag -> /opt/avg/av/bin/avgwrapper.sh
lrwxrwxrwx 1 root bin 29 Jun 11 13:13 avgdump -> /opt/avg/av/bin/avgwrapper.sh
lrwxrwxrwx 1 root bin 29 Jun 11 13:13 avgevtlog -> /opt/avg/av/bin/avgwrapper.sh
lrwxrwxrwx 1 root bin 29 Jun 11 13:13 avgscan -> /opt/avg/av/bin/avgwrapper.sh
lrwxrwxrwx 1 root bin 29 Jun 11 13:13 avgsetup -> /opt/avg/av/bin/avgwrapper.sh
lrwxrwxrwx 1 root bin 29 Jun 11 13:13 avgspmctl -> /opt/avg/av/bin/avgwrapper.sh
lrwxrwxrwx 1 root bin 29 Jun 11 13:13 avgupdate -> /opt/avg/av/bin/avgwrapper.sh
lrwxrwxrwx 1 root bin 29 Jun 11 13:13 avgvvctl -> /opt/avg/av/bin/avgwrapper.sh

 - hmm!! - all there all right - BUT , all pointing logical links to same avgwrapper.sh!

4) so, i checked in :

rcain@ubuntu:~/temp$ ls -l /opt/avg/av/bin
total 13139
-rwx------ 1 root bin  795120 Jun 11 13:13 avgavid
-rwxr-xr-x 1 root bin  162776 Jun 11 13:13 avgcfgctl
-rwxr-xr-x 1 root bin  540948 Jun 11 13:13 avgctl
-rwx------ 1 root bin 1233660 Jun 11 13:13 avgd
-rwxr-xr-x 1 root bin 2114208 Jun 11 13:13 avgdiag
-rwxr-xr-x 1 root bin  121680 Jun 11 13:13 avgdump
-rwxr-x--- 1 root bin  573192 Jun 11 13:13 avgevtlog
-rwx------ 1 root bin  729232 Jun 11 13:13 avgoad
-rwxr-xr-x 1 root bin  470936 Jun 11 13:13 avgscan
-rwxr-xr-x 1 root bin  869068 Jun 11 13:13 avgscand
-rwx------ 1 root bin  692052 Jun 11 13:13 avgsched
-rwxr-x--- 1 root bin    1423 Jun 11 13:13 avgsetup
-rwx------ 1 root bin  614060 Jun 11 13:13 avgspamd
-rwx------ 1 root bin  134128 Jun 11 13:13 avgspmctl
-rwx------ 1 root bin 1124504 Jun 11 13:13 avgtcpd
-rwx------ 1 root bin 2264728 Jun 11 13:13 avgupd
-rwxr-x--- 1 root bin  462720 Jun 11 13:13 avgupdate
-rwxr-xr-x 1 root bin  467224 Jun 11 13:13 avgvvctl
-rwxr-xr-x 1 root bin     392 Jun 11 13:13 avgwrapper.sh

 - interesting! - all files expected seem to be there!

5) BUT - when i try:

rcain@ubuntu:~/temp$ sudo avgctl --start
[sudo] password for rcain: 
/usr/bin/avgctl: 17: exec: /opt/avg/av/bin/avgctl: not found

 - avg cannot find its self!!

Conclusions: broken deb package on ubuntu - as you surmised - HOWEVER, i do not think this can be a serious breakage - just something wrong with paths set in avgwrapper.sh perhaps? 

Can anyone out there in AVG dev or UBUNTU dev assist?

Any help very gratefully received.

---

