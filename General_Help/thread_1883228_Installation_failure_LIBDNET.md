---
title: "Installation failure: LIBDNET"
date: 2011-11-18
forum: General Help
---

### Post by despuit on 2011-11-18
Hello all, I am attempting to set up snort however each time I run sudo ./configure -prefix=usr/local/snort --enable-sourcefire I receive a return error of "dnet header not found".

I attempted to un-install libdnet but failed as I did with snort so I proceeded regardless with a manual installation and experienced a few issues:

wget [http://libdnet.googlecode.com/files/libdnet-1.12.tgz](http://libdnet.googlecode.com/files/libdnet-1.12.tgz)
tar xvfz libdnet-1.12.tgz
cd libdnet-1.12/
./configure
make
checkinstall 
dpkg -i libdnet_1.12-1_i386.deb
ln -s /usr/local/lib/libdnet.1.0.1 /usr/lib/libdnet.1

Errors:

checkinstall (Does not run, command does not exist)
dpkg -i libdnet_1.12-1_i386.deb (Can not locate file libdnet_1.12-1_i386.deb)

Can any one provide any insight on this issue as it would be most helpful.

Thank you for the reply, worked perfectly now to deal with the other thousands of errors. :P

---

### Post by Dangertux on 2011-11-18
Easy fix install libdnet from repos 

```

sudo apt-get install libdumbnet-dev

```

More details on compiling snort from source here : dangertux.wordpress.com/2011/10/12/compiling-snort-2-9-1-1-daq-0-62/


Hope this helps.

---

### Post by ram7 on 2013-02-02
Yes this solves issue thanks.:P

---

