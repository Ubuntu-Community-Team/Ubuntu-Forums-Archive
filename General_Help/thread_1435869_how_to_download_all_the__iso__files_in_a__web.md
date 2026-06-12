---
title: "how to download all the  iso  files in a  web?"
date: 2010-03-22
forum: General Help
---

### Post by luofeiyu on 2010-03-22
in  [http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/](http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/)
you can see &#65306;
MD5SUMS 02-Feb-2010 15:06 2.5K
[ ] MD5SUMS.sign 22-Feb-2010 00:16 197
[ ] SHA1SUMS 02-Feb-2010 15:06 2.8K
[ ] SHA1SUMS.sign 22-Feb-2010 00:16 197
[ ] debian-504-i386-CD-1.iso 31-Jan-2010 20:05 646M
[ ] debian-504-i386-CD-2.iso 31-Jan-2010 20:10 646M
[ ] debian-504-i386-CD-3.iso 31-Jan-2010 20:11 648M
[ ] debian-504-i386-CD-4.iso 31-Jan-2010 20:12 629M
[ ] debian-504-i386-CD-5.iso 31-Jan-2010 20:12 648M
[ ] debian-504-i386-CD-6.iso 31-Jan-2010 20:13 647M
[ ] debian-504-i386-CD-7.iso 31-Jan-2010 20:13 635M
[ ] debian-504-i386-CD-8.iso 31-Jan-2010 20:14 641M
[ ] debian-504-i386-CD-9.iso 31-Jan-2010 20:14 586M
[ ] debian-504-i386-CD-10.iso 31-Jan-2010 20:01 648M
[ ] debian-504-i386-CD-11.iso 31-Jan-2010 20:01 635M
[ ] debian-504-i386-CD-12.iso 31-Jan-2010 20:01 539M
[ ] debian-504-i386-CD-13.iso 31-Jan-2010 20:02 647M
[ ] debian-504-i386-CD-14.iso 31-Jan-2010 20:02 644M
[ ] debian-504-i386-CD-15.iso 31-Jan-2010 20:02 645M
[ ] debian-504-i386-CD-16.iso 31-Jan-2010 20:03 637M
[ ] debian-504-i386-CD-17.iso 31-Jan-2010 20:03 636M
[ ] debian-504-i386-CD-18.iso 31-Jan-2010 20:04 646M
[ ] debian-504-i386-CD-19.iso 31-Jan-2010 20:04 645M
[ ] debian-504-i386-CD-20.iso 31-Jan-2010 20:05 619M
[ ] debian-504-i386-CD-21.iso 31-Jan-2010 20:06 647M
[ ] debian-504-i386-CD-22.iso 31-Jan-2010 20:06 642M
[ ] debian-504-i386-CD-23.iso 31-Jan-2010 20:07 648M
[ ] debian-504-i386-CD-24.iso 31-Jan-2010 20:07 647M
[ ] debian-504-i386-CD-25.iso 31-Jan-2010 20:08 641M
[ ] debian-504-i386-CD-26.iso 31-Jan-2010 20:08 594M
[ ] debian-504-i386-CD-27.iso 31-Jan-2010 20:09 641M
[ ] debian-504-i386-CD-28.iso 31-Jan-2010 20:09 648M
[ ] debian-504-i386-CD-29.iso 31-Jan-2010 20:10 648M
[ ] debian-504-i386-CD-30.iso 31-Jan-2010 20:11 612M
[ ] debian-504-i386-CD-31.iso 31-Jan-2010 20:11 156M
[ ] debian-504-i386-businesscard.iso 01-Feb-2010 17:45 36M
[ ] debian-504-i386-kde-CD-1.iso 31-Jan-2010 20:57 648M
[ ] debian-504-i386-netinst.iso 01-Feb-2010 17:46 150M
[ ] debian-504-i386-xfce+lxde-CD-1.iso 31-Jan-2010 20:59 646M
[ ] debian-update-5.0.4-i386-CD-1.iso 01-Feb-2010 21:01 616M
[ ] debian-update-5.0.4-i386-CD-2.iso 01-Feb-2010 21:02 612M
[ ] debian-update-5.0.4-i386-CD-3.iso 01-Feb-2010 21:02 614M
[ ] debian-update-5.0.4-i386-CD-4.iso 01-Feb-2010 21:03 613M
[ ] debian-update-5.0.4-i386-CD-5.iso 01-Feb-2010 21:04 631M
[ ] debian-update-5.0.4-i386-CD-6.iso 01-Feb-2010 21:04 395M
i want to dowload all  the iso files?
how to write the shell script?
curl -s [http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/](http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/) | grep |xargs curl
please help me make it.

---

### Post by soltanis on 2010-03-22
are you seriously planning on downloading all those files? Oh god...

Save what you pasted there to a file then do

```

cat file | awk '/\.iso/ { print "http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/$3"; }' | xargs -n1 wget

```

That will download every last ISO file in that directory.

Now, whether you want to/is this sane/will the sysadmin get extremely angry at you for this is another story.

---

### Post by ankspo71 on 2010-03-22
Hi,
I could be wrong, but I think they are providing all of those ISO's for people without internet. I think all you would really need is debian-504-i386-CD-1.iso and other packages can be downloaded though the package management system (apt-get, synaptic, etc)

Here are some more Sweden mirrors if it helps:

[LIST]
[*]Sweden: cdimage.debian.org: [HTTP]("http://cdimage.debian.org/debian-cd/")
[*]Sweden: ftp.df.lth.se: [FTP]("ftp://ftp.df.lth.se/debian-cd/")  [HTTP]("http://ftp.df.lth.se/debian-cd/")
[*]Sweden: ftp.ds.karen.hj.se: [FTP]("ftp://ftp.ds.karen.hj.se/debian-cd/") [HTTP]("http://ftp.ds.karen.hj.se/debian-cd/")
[*]Sweden: ftp.port80.se: [FTP]("ftp://ftp.port80.se/debian-cd/")  [HTTP]("http://ftp.port80.se/debian-cd/")
[*]Sweden: ftp.se.debian.org: [FTP]("ftp://ftp.se.debian.org/debian-cd/") [HTTP]("http://ftp.se.debian.org/debian-cd/")
[*]Sweden: ftp.sunet.se: [FTP]("ftp://ftp.sunet.se/pub/Linux/distributions/debian-cd/") [HTTP]("http://ftp.sunet.se/pub/Linux/distributions/debian-cd/")
[*]Sweden: mirrors.se.kernel.org: [FTP]("ftp://mirrors.se.kernel.org/debian-cd/") [HTTP]("http://mirrors.se.kernel.org/debian-cd/")
[/LIST]
[http://www.debian.org/CD/http-ftp/](http://www.debian.org/CD/http-ftp/)  (official mirror list)

If you don't have internet and you are able to run DVD's, then it would probably be better for you to download the DVD iso's, instead of downloading 30 cds or more.
Hope this helps

---

### Post by Dayofswords on 2010-03-22
yeah all you need ot cd-1 to install debian(or use one of the other cd-1's with kde or xfce)
all the others are every package in their repo

but if you really want to you could do this(this is how i'd do it oooh sooo inefficiently) 
```
wget -i /where/the/folder/is/downloadlist.txt
```
and the file for /where/the/folder/is/downloadlist.txt
```
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/MD5SUMS
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/MD5SUMS.sign
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/SHA1SUMS
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/SHA1SUMS.sign
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-1.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-2.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-3.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-4.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-5.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-6.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-7.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-8.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-9.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-10.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-11.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-12.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-13.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-14.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-15.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-16.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-17.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-18.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-19.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-20.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-21.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-22.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-23.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-24.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-25.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-26.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-27.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-28.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-29.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-30.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-CD-31.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-businesscard.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-kde-CD-1.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-netinst.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-xfce+lxde-CD-1.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-update-5.0.4-i386-CD-1.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-update-5.0.4-i386-CD-2.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-update-5.0.4-i386-CD-3.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-update-5.0.4-i386-CD-4.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-update-5.0.4-i386-CD-5.iso
http://ftp.acc.umu.se/debian-cd/5.0.4/i386/iso-cd/debian-update-5.0.4-i386-CD-6.iso
```

---

