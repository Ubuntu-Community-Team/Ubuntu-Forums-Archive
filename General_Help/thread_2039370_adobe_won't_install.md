---
title: "adobe won't install"
date: 2012-08-08
forum: General Help
---

### Post by fantasticmuse on 2012-08-08
I swear, I'm typing in the right commands but nothing happens.

ashley@ashley-NV51B:~$ cd ~/Downloads

ashley@ashley-NV51B:~/Downloads$ ls
AdbeRdr9.5.1-1_i486linux_enu.bin   kq-data_0.99.cvs20070319-1.1_all.deb
kq_0.99.cvs20070319-1.1_amd64.deb  ohrrpgce_2012.06.15.alectormancy-5252_i386.deb

ashley@ashley-NV51B:~/Downloads$ chmod +x AdbeRdr9.5.1-1_i486linux_enu.bin 

ashley@ashley-NV51B:~/Downloads$ ./AdbeRdr9.5.1-1_i486linux_enu.bin
bash: ./AdbeRdr9.5.1-1_i486linux_enu.bin: No such file or directory

wth is going on?

---

### Post by Toz on 2012-08-11
Adobe Reader is also available from the official ubuntu repositories. On precise (ubuntu 12.04), it is at version 9.5.1-1 as well. Look for it in the Software Centre. Note, you'll have to have the partner repository enabled to see it. To enable the partner repository, from within the Software Centre, click on Edit-Software Sources, click on the "Other Software" tab and check "Canonical Partners".

---

