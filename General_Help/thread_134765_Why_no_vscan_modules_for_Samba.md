---
title: "Why no vscan modules for Samba"
date: 2006-02-22
forum: General Help
---

### Post by el3ktro on 2006-02-22
I recently switched a productive file server from Gentoo to Ubuntu, but I'm missing the vscan modules for Samba, which made it possible to scan all files on the Samba server on-the-fly. I can't find the vscan modules in any of Ubuntu's default repos. Are there any Ubuntu/Debian debs for them? Where can I get them?

Tom

---

### Post by mynameisjohn on 2006-06-06
don't know if you're still interested but i don't think there are any debs about. 

there are a few sites concerning a debian install, here is my history (lazily pasted) for my dapper setup. once to bear in mind is that an upgrade to samba will blow the virus protection away. someone might find it useful anyway. :)

i think there were some erros putting clam on (to explain my reiteration!)

  190  apt-get install clamav arj unzoo clamav-freshclam clamav-daemon
  191  apt-get install clamav-base
  192   
  193  mkdir /usr/src/sources
  194  cd /usr/src/sources
  195  apt-get install dpkg-dev
  196  apt-get source samba
  197  apt-get build-dep samba
  198  cd samba-3.0.22/
  199
  200  ./debian/rules configure-stamp
  201  cd source
  202   
  203  
  204  
  205 
  206  make proto
  207  cd ../..
  208  wget [http://www.openantivirus.org/snapshots/samba3-vscan-0.4.0-snapshot1.tar.gz](http://www.openantivirus.org/snapshots/samba3-vscan-0.4.0-snapshot1.tar.gz)
  209   
  210  tar xvzf samba3-vscan-0.4.0-snapshot1.tar.gz
  211  cd samba3-vscan-0.4.0-snapshot1
  212  ./configure --with-samba-source=/usr/src/sources/samba-3.0.22/source/
  213  make && make install
  214  cp clamav/vscan-clamav.conf /etc/samba/samba-vscan-clamav.conf
  215  vi /etc/samba/samba-vscan-clamav.conf
  216  vi /etc/samba/smb.conf

hths

mnij.

---

### Post by aaron1234nz on 2007-02-16
one more line is needed:
cp /usr/src/samba-vscan-0.3.6b/vscan-clamav.so /usr/lib/samba/vfs/

if the vsf-object is missing from the proper location - the samba share will not show up.

---

### Post by jbcola on 2007-04-07
There is another way, without the need of the samba sources...

Just get the rpm of samba-vscan-clamav :
[http://rpmseek.com/rpm-pl/samba-vscan-clamav.html?hl=de&cbd=0:S:0::105](http://rpmseek.com/rpm-pl/samba-vscan-clamav.html?hl=de&cbd=0:S:0::105)

Convert it with alien, and install it with dpkg.

It was easy, the only thing i had to change was the socket path for clamd:
clamd socket name =  /var/run/clamav/clamd.ctl

JL

---

