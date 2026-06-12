---
title: "Canon Pixma iP1600"
date: 2011-02-27
forum: General Help
---

### Post by Trennik on 2011-02-27
This has been posted before - a couple times. I found a couple articles. 

One in English

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200)

one in... Italian?

[http://wiki.ubuntu-it.org//Hardware/StampantiScanner/CanonPixmaIP1600#head-389ae624541d5fc9d681c37d6b31ac31a8c1834b](http://wiki.ubuntu-it.org//Hardware/StampantiScanner/CanonPixmaIP1600#head-389ae624541d5fc9d681c37d6b31ac31a8c1834b)

They're both seemingly doing the same thing - but they're not quite the same. 

Neither article points to the correct area to download the required iP2200 packages. I navigated around the website at the end of the download link(s) and managed to download the package I *thought* was correct - only after downloading I got some errors when trying to unpack. Unexpected end of file... was my download corrupt? I downloaded it several times successfully, and opened the archive in 'Ark' ... I was able to see the packages in the archive, and I tried to extract them. I got 3 *.rpm files extracted... and so I think I need to convert those to *.deb files, right? 

I think that's the step I'm stuck on - between the Italian guide and the English guide - both which seem to be wrong - and the fact that I'm a complete Linux noob - has me turning in circles with a funny look on my face. :confused:

My intuition tells me that the terminal commands in the italian guide might be what I need. 
```

sudo alien --to-deb --scripts *i386.rpm
sudo dpkg -i *.deb
```correct?

then... this step? 

```

cd /usr/lib
sudo ln -s /lib/libpng12.so.0 libpng.so.3
sudo ln -s libtiff.so.4 libtiff.so.3
sudo ln -s libxml2.so.2 libxml.so.1
sudo ldconfig
```which is not quite the same as the English version which has the command

```

sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3
```and that's very similar - but different. 


TL;DR. I can't get my Canon Pixma iP1600 to work on Ubuntu 9.10
I've found several posts with the same question which led me to 
2 sets of instructions for the same workaround and I can't quite get it
to work. Please help.

---

### Post by Trennik on 2011-02-27
I'm getting an error when I try to convert the *.rpm files - like this: 

```
sudo alien cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip2200-2.60-1.i386.rpm
error: incorrect format: unknown tag
mkdir: cannot create directory `cnijfilter-common-2.60': File exists
unable to mkdir cnijfilter-common-2.60:  at /usr/share/perl5/Alien/Package.pm line 257.

```

.. ?

---

### Post by Trennik on 2011-02-27
I think I figured out more of the problem... although it doesn't help me print anything on the printer. 

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200)

Near the top, where it's easy to read: 
[B]
This does not work for AMD64. [/B]

That's what I have. I realized what was wrong when I was finally getting alien to work and this error came up - 

```

dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)

```I'm not sure what to do at this point to get the printer to work.

[EDIT] 

Found this:
[http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html](http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html)
and this:
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

but I can't find the driver files referenced to download
1. libcnbj-2.6_0-1_i386.deb
2. bjfilter-2.6_1-1_i386.deb
3. pstocanonbj_3.3-1_i386.deb

... another dead end. 
[/EDIT]

---

### Post by pmalvr on 2011-10-16
I had my canon pixma iP1600 printer working well in Ubuntu 11.04 (I followed the second answer wrote [here ]("http://askubuntu.com/questions/41615/how-to-install-canon-pixma-ip1600")to accomplish that).

Then I upgraded my Ubuntu to version 11.10 but the upgrade went wrong and I was forced to reinstall Ubuntu 11.10 from scratch. After that, I tried to install my printer just as I did before but I wasn't able to print with success anymore.

I reinstalled Ubuntu 11.10 a second time, this time without encrypting my home folder and I was able to print successfully. To take any thoughts I reinstalled Ubuntu 11.10 a third time and again I could not print anything.

So, can someone help me to put my printer working in Ubuntu 11.10 with my home folder encrypted?

Thanks in advance.

---

