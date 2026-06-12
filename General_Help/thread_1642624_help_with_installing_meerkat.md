---
title: "help with installing meerkat"
date: 2010-12-10
forum: General Help
---

### Post by mortsemious on 2010-12-10
hi, first post in the forum. anyway, i'm at the who are you? part of the installing process and it will not let me press the forward button. thanks.

---

### Post by Quackers on 2010-12-10
Don't start or end your username with capital letters :-) It's not allowed - it doesn't say so, but that's probably what's wrong. Future installers will have an error message - I believe :-)

---

### Post by mortsemious on 2010-12-10
thanks it worked, another question: when i click on the ubuntu software center it simply closes the applications and doesn't open the software center. any advice?

---

### Post by Quackers on 2010-12-10
One problem solved but found another :-)
Try opening Update Manager and in the bottom left of the window click on settings and the Software Sources window should open.

---

### Post by mortsemious on 2010-12-10
but whenever i try to install the updates with the update manager, after i have downloaded them it doesn't work. i tried again but got this:

package operation failed

the installation or removal of a software package failed

details

installArchives() failed:
  Extracting templates from packages: 15% 
Extracting templates from packages: 31%
 Extracting templates from packages: 46%
 Extracting templates from packages: 62%
 Extracting templates from packages: 78%
 Extracting templates from packages: 93%
 Extracting templates from packages: 100% 
Preconfiguring packages ...
  Extracting templates from packages: 15%
 Extracting templates from packages: 31%
 Extracting templates from packages: 46%
 Extracting templates from packages: 62%
 Extracting templates from packages: 78%
 Extracting templates from packages: 93%
 Extracting templates from packages: 100% 
Preconfiguring packages ... 
(Reading database ...
  (Reading database ... 5%
 (Reading database ... 10%
 (Reading database ... 15% 
(Reading database ... 20% 
(Reading database ... 25%
 (Reading database ... 30%
 (Reading database ... 35%
 (Reading database ... 40%
 (Reading database ... 45%
 (Reading database ... 50%
 (Reading database ... 55%
 (Reading database ... 60%
 (Reading database ... 65%
 (Reading database ... 70%
 (Reading database ... 75%
 (Reading database ... 80% 
(Reading database ... 85%
 (Reading database ... 90%
 (Reading database ... 95%
 (Reading database ... 100%
 (Reading database ... 117333 files and directories currently installed.) 
Preparing to replace libc-bin 2.12.1-0ubuntu6 (using .../libc-bin_2.12.1-0ubuntu9_i386.deb) ... 
Unpacking replacement libc-bin ... 
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error 
dpkg-deb: subprocess paste returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/libc-bin_2.12.1-0ubuntu9_i386.deb (--unpack): 
 short read on buffer copy for backend dpkg-deb during `./sbin/ldconfig.real' 
Errors were encountered while processing: 
 /var/cache/apt/archives/libc-bin_2.12.1-0ubuntu9_i386.deb

---

### Post by mortsemious on 2010-12-11
any help?

---

### Post by Quackers on 2010-12-11
In a terminal try
```
sudo dpkg --configure -a
```

---

### Post by argedion on 2010-12-11
try opening a terminal and doing the update I think its

sudo apt-get update

haven't had any issues with the update manager so I can guarantee this is what you want. I do hope it works for you though :)

---

