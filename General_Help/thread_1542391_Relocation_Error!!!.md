---
title: "Relocation Error!!!"
date: 2010-07-30
forum: General Help
---

### Post by Abhijit Navale on 2010-07-30
Hello all!!!

I am using Ubuntu Lucid 64 bit. I installed kubuntu to test it. but then i removed it. 

After that kde messed some stuff in my ubuntu e.g. mouse icons etc.

So to get back my gnome i followed instructions on this page:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

But After that i started getting problem running pgadmin3 and codelite.

When I try to run codelite from terminal i get this error:


codelite: relocation error: /usr/lib/codelite/libpluginu.so: symbol _ZN13wxAuiNotebook7SetFontERK6wxFont, version WXU_2.8 not defined in file libwx_gtk2u_aui-2.8.so.0 with link time reference

and When i try to run pgadmin3 from terminal i got this error:

pgadmin3: relocation error: pgadmin3: symbol _ZN21wxMemoryFSHandlerBase19AddFileWithMimeTypeERK8wxStringPKvmS2_, version WXU_2.8 not defined in file libwx_baseu-2.8.so.0 with link time reference

Thanks in advance!!!

---

### Post by awi on 2010-08-04
In this posts there are some steps to recompile, apparently official updates breaks a dependency, until is fixed you might have to recompile de pgadmin3 package

[https://bugs.launchpad.net/ubuntu/+source/pgadmin3/+bug/610975](https://bugs.launchpad.net/ubuntu/+source/pgadmin3/+bug/610975)

---

### Post by Abhijit Navale on 2010-08-04
> **awi said:**
> In this posts there are some steps to recompile, apparently official updates breaks a dependency, until is fixed you might have to recompile de pgadmin3 package

[https://bugs.launchpad.net/ubuntu/+source/pgadmin3/+bug/610975](https://bugs.launchpad.net/ubuntu/+source/pgadmin3/+bug/610975)

Reply no #9 is the solution worked for me. 
Giving it here:

[meux]("https://launchpad.net/%7Ereinhard-moser")             wrote             on 2010-07-30:                                                             [ #9]("https://bugs.launchpad.net/ubuntu/+source/pgadmin3/+bug/610975/comments/9")                                                        Hi,
   i have same problems on lucid i386. I now recompiled package and pgadmin3 works.
 apt-get source pgadmin3
sudo apt-get install debhelper libpq-dev libwxgtk2.8-dev libxml2-dev libxslt1-dev autotools-dev
cd pgadmin3-1.10.2
dpkg-buildpackage
sudo dpkg -i ../pgadmin3_1.10.2-1_i386.deb
 and pgadmin3 works again.
 Cheers



        

Thank you awi. now looking at it! 
:)

---

### Post by Abhijit Navale on 2010-08-04
Thankyou awi!
:)
It worked for me!!!
:D

---

### Post by deeeed on 2010-08-24
works for me, thanks!

---

### Post by Mario13 on 2010-08-24
Another solution is to downgrade libwxbase.  - Go to Synaptic - Search and select (click) on package libwxbase2.8-0 - Go to "Packages", "Force Version", and choose 2.8.10.1-0ubuntu1  It worked in Ubuntu 10.04. This solution is easy and doesn't touch pgAdmin. This solution is temporary until and upgrade of pgAdmin appears in the official repositories.

---

