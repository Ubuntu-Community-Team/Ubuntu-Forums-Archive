---
title: "ubiquity(ubiquity-front-end) installation problem"
date: 2010-07-04
forum: General Help
---

### Post by tomynho on 2010-07-04
Hello everyone.
I just wanted to try out the software named "remastersys". 
After downloading it's package, it said it requires four packages.
User-setup
libdebian-installer4
casper
ubiquity.
I successfully managed to install user-sedup, libdebian-installer4 and  casper.
The problem is with ubiquity.
When trying to install ubiquity, it says it requires ubiquity-front-end.
But when I tried to install ANY of ubiquity-front-end's (GTK,KDE and  deb...(something :D)),  it says it requires ubiquity... How can I install an application when  it's dependency requires the application to be installed? ](*,)

---

### Post by colorlessprism on 2010-07-04
i use remastersys quite a bit and never had to mess with dependencies. The Remastersys repository needs to be added to your /etc/apt/sources.list, this can be done with gedit (or another preferred text editor) or by going to System>Administration>Software Sources. copy and paste to your sources list:
(Note: this assumes Karmic, Lucid and Newer with grub2)
```

# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

```
for more detailed information please see this guide:
[http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

---

### Post by tomynho on 2010-07-04
> **colorlessprism said:**
> i use remastersys quite a bit and never had to mess with dependencies. The Remastersys repository needs to be added to your /etc/apt/sources.list, this can be done with gedit (or another preferred text editor) or by going to System>Administration>Software Sources. copy and paste to your sources list:
(Note: this assumes Karmic, Lucid and Newer with grub2)
```

# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

```for more detailed information please see this guide:
[http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

I forgot to mention, I did this the 1st time and I was not successful... 

Anyway, thanks for your reply.

---

