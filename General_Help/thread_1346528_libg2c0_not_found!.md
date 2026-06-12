---
title: "libg2c0 not found!"
date: 2009-12-05
forum: General Help
---

### Post by krishnamohan on 2009-12-05
I recently upgraded from 9.04 to 9.10...Now when I try to run a particular program, it says 

***/Desktop/comphep-4.5.1/bin/s_comphep.exe: error while loading shared libraries: libg2c.so.0: cannot open shared object file: No such file or directory***


I cant get libg2c through sudo apt or synaptic..what is to be done? Is g77 not available for ubuntu?

---

### Post by conehead77 on 2009-12-05
take a look at this blogpost:
[http://0x5f.blogspot.com/2009/10/install-g77-in-ubuntu-904-jaunty.html](http://0x5f.blogspot.com/2009/10/install-g77-in-ubuntu-904-jaunty.html)

---

### Post by krishnamohan on 2009-12-05
This is what happened when I followed instructions...

[I][B]No candidate version found for g77
No candidate version found for g77
The following packages will be REMOVED:
  linux-headers-2.6.31-14{u} linux-headers-2.6.31-14-generic{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 82.0MB will be freed.
Do you want to continue? [Y/n/?] [/B]

[/I]
I said no.....

---

### Post by krishnamohan on 2009-12-05
I downloaded the deb package and everything is fine now...


***[http://packages.ubuntu.com/jaunty/libg2c0](http://packages.ubuntu.com/jaunty/libg2c0)***

---

### Post by krishnamohan on 2009-12-05
Thank you very much!:D

---

### Post by TheOneEyedMan on 2010-08-04
I ran into this problem with Tomlab (7.4) in Matlab (7.7) in 10.04. I was able to successfully install the program by ignoring the dependencies

By downloading the deb file from 
[http://packages.ubuntu.com/jaunty/libg2c0](http://packages.ubuntu.com/jaunty/libg2c0)

and then running 
sudo dpkg --force-depends -i libg2c0_3.4.6-8ubuntu2_amd64.deb

Hope that helps any tomlab / matlab linux user out there.

---

### Post by JaneMuci on 2010-10-18
It has helped me. Thank you. :)

---

