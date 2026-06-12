---
title: "&quot;make&quot; command problem // autoconfig.h missing?"
date: 2011-03-19
forum: General Help
---

### Post by pigimon on 2011-03-19
well im trying all day today to get my internet working, i have an amilo m7440  with ubuntu 10.10 2.6.// 35-28-generic . So i found this "fsam7440" thing that could help me ( i guess ) i followed these steps 

How to Install
1. Extract fsam7440-0.1.tar.bz2
  tar xfj fsam7440-xxx.tar.bz2

2. Compile the module
  cd fsam7440-xxx
  make

3. Install the module
  make install

4. Test it
  modprobe fsam7440




but when im typing the make command (2nd command of step 2) it says :

pigimon@pigimon-AMILO-M-Series:~/Downloads/fsam7440-0.4$ make
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/pigimon/Downloads/fsam7440-0.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/pigimon/Downloads/fsam7440-0.4/fsam7440.o
/home/pigimon/Downloads/fsam7440-0.4/fsam7440.c:40: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/home/pigimon/Downloads/fsam7440-0.4/fsam7440.o] Error 1
make[1]: *** [_module_/home/pigimon/Downloads/fsam7440-0.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [default] Error 2



any ideas? thanks!

---

### Post by lithopsian on 2011-03-19
You might want to correct the post title so that it has the correct filename.  I only came in here by chance because I had no idea what autoconfig.h was.  autoconf.h is a standard Linux header file and should be included on all machines.  You can search for it under   /usr/src/linux-headers-2.6.35-28-generic but it should be there.

So the issue is probably a configuration one related to your make file.  Perhaps looking in the wrong kernel version headers?

---

### Post by pigimon on 2011-03-22
oh ok thanks, changing the name to autoconf.h about the wrong kernel didn't quite understand what you said... im a newb so... :P  are you talking about linux/autoconf.h ? should it be "/usr/src/linux-headers-2.6.35-28-generic" ?

---

### Post by pigimon on 2011-03-25
so anyone?

---

### Post by Trocco on 2011-03-26
I am having some what of the same issue. I have an Asus Eee PC 1005HAB Internet was working great. I went to use it again last night and poof no Internet. I did some research found I needed to install the following drivers AR81Family-linux-v1.0.0.10.tar.gz I extracted them, then went to run make and i get "linux kernel source not configured missing autoconf.h. 

so after this I did uname -r to get the Linux Headers which are 2.6.35-28-generic so i went to packages.ubuntu.com found my generic headers installed them rebooted still no autoconf.h file. I am at a loss. I checked /usr/src and under that I have all the linux headers directories and not one of them have an autoconf.h O I also tried running make xconfig and got the same error message. Though I though make xconfig will auto generate the autconf.h file. 

If anyone has any other suggestions please let me know. I use this laptop for my Certified Ethical Hacker course i really don't want to format cause of the tools and settings i installed and configured. 

Thanks,

Tom

---

### Post by Trocco on 2011-03-26
[http://ubuntuforums.org/showthread.php?t=1597605&highlight=autoconf.h](http://ubuntuforums.org/showthread.php?t=1597605&highlight=autoconf.h) 
This post helped me out I can no run the make command now that the autoconf.h file exists but i get some error messages which I am guessing I need to use a generic driver? here is the error I am getting. . . any thoughts?

```
  root@ubuntu:~/src# make
  make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/rocco/src modules
  make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
    CC [M]  /home/rocco/src/at_common_main.o
    CC [M]  /home/rocco/src/atl1e_main.o
  /home/rocco/src/atl1e_main.c: In function ‘atl1e_request_irq’:
  /home/rocco/src/atl1e_main.c:156: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
  include/linux/interrupt.h:135: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int,  void *)’
  /home/rocco/src/atl1e_main.c: In function ‘atl1e_probe’:
  /home/rocco/src/atl1e_main.c:287: error: ‘struct net_device’ has no member named ‘open’
  /home/rocco/src/atl1e_main.c:288: error: ‘struct net_device’ has no member named ‘stop’
  /home/rocco/src/atl1e_main.c:289: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
  /home/rocco/src/atl1e_main.c:290: error: ‘struct net_device’ has no member named ‘get_stats’
  /home/rocco/src/atl1e_main.c:291: error: ‘struct net_device’ has no member named ‘set_multicast_list’
  /home/rocco/src/atl1e_main.c:292: error: ‘struct net_device’ has no member named ‘set_mac_address’
  /home/rocco/src/atl1e_main.c:293: error: ‘struct net_device’ has no member named ‘change_mtu’
  /home/rocco/src/atl1e_main.c:294: error: ‘struct net_device’ has no member named ‘do_ioctl’
  /home/rocco/src/atl1e_main.c:313: error: ‘struct net_device’ has no member named ‘vlan_rx_register’
  /home/rocco/src/atl1e_main.c:316: error: ‘struct net_device’ has no member named ‘poll_controller’
  /home/rocco/src/atl1e_main.c: In function ‘atl1e_set_multi’:
  /home/rocco/src/atl1e_main.c:1865: error: ‘struct net_device’ has no member named ‘mc_list’
  /home/rocco/src/atl1e_main.c:1865: error: dereferencing pointer to incomplete type
  /home/rocco/src/atl1e_main.c:1866: error: dereferencing pointer to incomplete type
  make[2]: *** [/home/rocco/src/atl1e_main.o] Error 1
  make[1]: *** [_module_/home/rocco/src] Error 2
  make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
  [FONT=&quot]make: *** [default] Error 2[/FONT]
```

---

### Post by pigimon on 2011-04-08
hmmm weird... the whole thread here is wrong tho we should post it in a new one, the name i put is wrong :( "autoconfig.h) lol.. maybe a reason we are not getting any answers :P

---

