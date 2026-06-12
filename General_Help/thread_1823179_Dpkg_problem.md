---
title: "Dpkg problem"
date: 2011-08-11
forum: General Help
---

### Post by kswix on 2011-08-11
Hi! My problem: when I try to apt-get upgrade system or install a new package in synaptic or terminal, I see this:

```
dpkg: ../../../lib/dpkg/dump.c:250: w_status: Assertion `pigp->trigpend_head' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

So, before I have a problem - Synaptic opened, told that /var/lib/dpkg/status don't exist, in the web I read that sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status can help to solve this problem. It help with this problem, but I have a new (see above).

Thanks in advance, kswix

---

### Post by jerrrys on 2011-08-11
looks like a bug

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Assertion+%60pigp-%3Etrigpend_head%27+failed&sa=Search&cof=FORID:9#896](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Assertion+%60pigp-%3Etrigpend_head%27+failed&sa=Search&cof=FORID:9#896)

---

### Post by kswix on 2011-08-12
Thanks for recommendation.  I found this: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/798803](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/798803)

```

  sudo mv /var/lib/dpkg/triggers/Unincorp.new Unincorp
  sudo apt-get update
  apt-get download dpkg
  dpkg -x dpkg_1.16.0.3ubuntu2_*.deb tmp-dpkg
   sudo cp -a tmp-dpkg/usr/bin/dpkg /usr/bin/dpkg
  sudo dpkg --unpack dpkg_1.16.0.3ubuntu2_*.deb
  sudo dpkg --configure -a
  sudo apt-get -f install

```

But now, on every install/remove packet, I see lines like these:
```
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 2.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 2.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN6> line 2.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN6> line 2.

```

What I must do?

---

### Post by dino99 on 2011-08-12
redo with dpkg -i

---

### Post by kswix on 2011-08-12
What is redo?

---

