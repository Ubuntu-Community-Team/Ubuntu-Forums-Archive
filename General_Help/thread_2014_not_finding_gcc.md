---
title: "not finding gcc ?"
date: 2004-10-25
forum: General Help
---

### Post by jamaas on 2004-10-25
I've just changed from another distro.  When I try to configure the latest version of Mozilla (1.8a4) I get the following message?  I'm not sure why because when I build a database, and then locate gcc, I find it in /usr/bin  and that is in my $PATH statement as user .. so why no gcc?

Thanks a bunch 

Jim

====================
jamaas@Bossy:~/Downloads/mozilla $ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
=======================
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

---

### Post by kaput on 2004-10-25
Probably because it's not installed by default. Try installing it via Synaptic.

---

### Post by xeo on 2004-10-25
Where I get gcc for ubuntu? My modem isn't working and i can't connect to internet.

---

### Post by sfw5000 on 2004-10-25
> Where I get gcc for ubuntu? My modem isn't working and i can't connect to internet. 

It is definitely available in synaptic, but it might also be available on the install CD. In synaptic, make sure the install CD is listed as a repository and try installing frm there.

---

### Post by FLeiXiuS on 2004-10-25
sudo apt-get install gcc

Should be on the Ubuntu Warthog CD.

---

