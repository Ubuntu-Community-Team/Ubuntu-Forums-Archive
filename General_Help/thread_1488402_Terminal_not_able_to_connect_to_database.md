---
title: "Terminal not able to connect to database???"
date: 2010-05-20
forum: General Help
---

### Post by Elliotal on 2010-05-20
Got a problem with terminal.

Just upgraded to 10.04, trying to watch a dvd and it doesnt work.

so i go to the ubuntu website, download the required pack (ubuntu restriced extras)

and then type in the code:

 ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

when i do this, terminal keeps trying to connect to a database, but it is not able to, see below....

```

--2010-05-20 06:43:26--  http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... failed: Connection timed out.
Retrying.

--2010-05-20 06:43:48--  (try: 2)  http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages
Connecting to packages.medibuntu.org|88.191.82.11|:80... failed: Connection timed out.
Retrying.

```
Im at university and sitting behind a proxy. however, i had no problem doing this with ubuntu 9.10 and i can access internet, update, software centre ect...

Any ideas??

---

### Post by dcstar on 2010-05-20
> **Elliotal said:**
> 
.........
Im at university and sitting behind a proxy. however, i had no problem doing this with ubuntu 9.10 and i can access internet, update, software centre ect...

Any ideas??

[http://blog.zenlinux.com/?p=366](http://blog.zenlinux.com/?p=366)
[https://bugs.launchpad.net/ubuntu/+source/wget/+bug/232469](https://bugs.launchpad.net/ubuntu/+source/wget/+bug/232469)

---

### Post by Elliotal on 2010-05-20
> **dcstar said:**
> [http://blog.zenlinux.com/?p=366](http://blog.zenlinux.com/?p=366)


Cheers mate, this website has a quick work around. i need to add ```
export no_proxy=$(echo $no_proxy | sed 's/,$//')
``` to my ~/.bashrc.

How do i do this??

---

### Post by dino99 on 2010-05-20
other mirrors, choose one as medibuntu server is down time to time:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

or:
deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free
deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free

or
deb [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) lucid free non-free
deb-src [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) lucid free non-free

or

deb [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free
deb-src [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free

---

### Post by Elliotal on 2010-05-21
Perfect cheers mate

---

