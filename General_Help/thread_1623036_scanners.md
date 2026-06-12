---
title: "scanners"
date: 2010-11-16
forum: General Help
---

### Post by Karlof on 2010-11-16
Hi 

why does avasys support all in one epson sx 215 scanners on ubuntu  10.4

but not on ubuntu 10.10 I thought each issue was a step forward 

 Ubuntu 10.10 is saying the drivers are not dependable ????

Help please

---

### Post by sisco311 on 2010-11-16
Are you sure that you are trying to install the right packages in the right order?

For 32-bit Ubuntu you need:
[list]
[*]iscan-data_1.4.0-1_all.deb
[*]iscan_2.26.0-3.ltdl7_i386.deb
[*]iscan-network-nt_1.1.0-2_i386.deb
[/list]

For 64-bit:
[list]
[*]iscan-data_1.4.0-1_all.deb
[*]iscan_2.26.0-3.ltdl7_amd64.deb
[*]iscan-network-nt_1.1.0-2_amd64.deb
[/list]

Direct links:
[http://linux.avasys.jp/drivers/iscan-data/1.4.0/](http://linux.avasys.jp/drivers/iscan-data/1.4.0/)
[http://linux.avasys.jp/drivers/iscan/2.26.0/](http://linux.avasys.jp/drivers/iscan/2.26.0/)
[http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/](http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/)

What's the error message you get?

---

### Post by Karlof on 2010-11-16
Hi sisco 311

the message reads" no dependancy on i scan data"

Cheers

---

### Post by sisco311 on 2010-11-16
Strange, iscan-date depends only on udev (which is installed by default) and xsltproc.

So try installing xsltproc:
```
sudo apt-get update
sudo apt-get install xsltproc
```

---

### Post by Karlof on 2010-11-16
Sorry sisco 311 no joy

where next

---

### Post by laure_f_o on 2010-11-18
Hello, I had the same problem, and with this post and this other one I solved it.

[http://www.ubuntu-es.org/node/140771](http://www.ubuntu-es.org/node/140771)

you also need the **libltdl3 **than you can find here[B].

[/B][http://packages.debian.org/lenny/libltdl3](http://packages.debian.org/lenny/libltdl3)

Thanks all.

---

### Post by Karlof on 2010-11-21
Hi Laure -f-0


I could not get a result with your advice    however

I googled avasys site and downloaded  iscan_2.26.1.3ltdl7_i386deb on the
bottom of the page for all in one scanners epson

I also installed xsane which is on the ubuntu software programmes


problem now solved  Thanks to all who contributed

karlof

---

