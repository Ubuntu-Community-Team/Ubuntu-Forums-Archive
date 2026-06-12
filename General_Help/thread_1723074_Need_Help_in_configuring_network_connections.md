---
title: "Need Help in configuring network connections"
date: 2011-04-06
forum: General Help
---

### Post by sandy0594 on 2011-04-06
Hi all,i am too new for linux..I installed Ubuntu 10.10 desktop edition from windows.When i am trying to configure network connections i am facing problems

```


udo pppoeconf

Sorry,no working ethernet card could be found.If you do have an interface card which was not autodetected so far,you probably wish to load the driver manually using the modconf utility.Run modconf now?  

 /usr/sbin/pppoeconf: 523: modconf: not found
 
 Ifconfig
  
   Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:20 errors:0 dropped:0 overruns:0 frame:0
            TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
              RX bytes:1304 (1.3 KB)  TX bytes:1304 (1.3 KB)


  
lspci -nn | grep Ethernet

  01:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)


```

```


sudo lshw -C network

*-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:febc0000-febfffff ioport:ec00(size=128)


```

So,by searching some posts..i downloaded AR81Family-linux-v1.0.1.14 and AR81Family-linux-v1-1.0.1.14.patch.But,what disgusting is i couldn't install them due to some errors

```


 sandy@ubuntu:/media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/AR81Family-linux-v1.0.1.14/src$ sudo make install
  Makefile:105: *** Linux kernel source not configured - missing autoconf.h.  Stop.
   
  sandy@ubuntu:~$ patch -p1  /media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/AR81Family-linux-v1-1.0.1.14.patch/AR81Family-linux-v1-1.0.1.14.patch
  The program 'patch' is currently not installed.  You can install it by typing:
  sudo apt-get install patch
   
  sandy@ubuntu:~$ sudo apt-get install patch
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Unable to locate package patch

```

can anyone explain me in detail as how to sort out this problem

---

### Post by sandy0594 on 2011-04-07
Why ubuntu forum is too slow to reply?

---

