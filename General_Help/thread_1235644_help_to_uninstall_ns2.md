---
title: "help to uninstall ns2"
date: 2009-08-09
forum: General Help
---

### Post by abhay143 on 2009-08-09
hi folks
i am trying to uninstall ns2 
 this what i tried 
***********************************************
abhay@abhay-laptop:~$ sudo apt-get remove ns-allinone-2.31
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ns-allinone-2.31
abhay@abhay-laptop:~$ ns
Usage:      host [-v] [-a] [-t querytype] [options]  name  [server]
Listing:    host [-v] [-a] [-t querytype] [options]  -l zone  [server]
Hostcount:  host [-v] [options] -H [-D] [-E] [-G] zone
Check soa:  host [-v] [options] -C zone
Addrcheck:  host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options:  [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options:   [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage:  [-x [name ...]] [-X server [name ...]]
**************************************
but when i run the command ns , the output in the terminal shows that process ns is running

so i tried to kill ns 
************
abhay@abhay-laptop:~$ ps -ef|grep ns
root      2501     1  0 01:13 ?        00:00:00 /usr/sbin/console-kit-daemon
abhay     3527     1  0 01:14 ?        00:00:29 gnome-screensaver
abhay     3768  3734  6 01:15 ?        00:38:33 /usr/lib/opera/9.64/operapluginwrapper 73 76 /usr/lib/mozilla/plugins/flashplugin-alternative.so
abhay    13023 12832  0 11:12 pts/0    00:00:00 grep ns
abhay@abhay-laptop:~$ kill -9 13023
bash: kill: (13023) - No such process
abhay@abhay-laptop:~$ 
**********************
but it says that , there is no such process as ns


so please folks help me with the same

---

### Post by marshalium on 2009-08-09
> **abhay143 said:**
> hi folks
i am trying to uninstall ns2 
 this what i tried 
***********************************************
abhay@abhay-laptop:~$ sudo apt-get remove ns-allinone-2.31
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ns-allinone-2.31


Are you sure that "ns-allinone-2.31" is the name of the package containing ns? Usually package names do not have version numbers in them. And there is not a package named ns-allinone in the default Ubuntu repositories. 

Searching through the ubuntu packages on packages.ubuntu.com reveals that the package "host" contains the command "ns".
[http://packages.ubuntu.com/jaunty/i386/host/filelist](http://packages.ubuntu.com/jaunty/i386/host/filelist)

How did you install ns2? From a .deb package? A 3rd party apt repository? Compiling from source? Did you follow a howto somewhere?

> **abhay143 said:**
> 
abhay@abhay-laptop:~$ ns
Usage:      host [-v] [-a] [-t querytype] [options]  name  [server]
Listing:    host [-v] [-a] [-t querytype] [options]  -l zone  [server]
Hostcount:  host [-v] [options] -H [-D] [-E] [-G] zone
Check soa:  host [-v] [options] -C zone
Addrcheck:  host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options:  [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options:   [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage:  [-x [name ...]] [-X server [name ...]]
**************************************
but when i run the command ns , the output in the terminal shows that process ns is running


It doesn't look like ns is running to me. It looks like the ns command is just printing its usage statement. 


> **abhay143 said:**
> 
so i tried to kill ns 
************
abhay@abhay-laptop:~$ ps -ef|grep ns
root      2501     1  0 01:13 ?        00:00:00 /usr/sbin/console-kit-daemon
abhay     3527     1  0 01:14 ?        00:00:29 gnome-screensaver
abhay     3768  3734  6 01:15 ?        00:38:33 /usr/lib/opera/9.64/operapluginwrapper 73 76 /usr/lib/mozilla/plugins/flashplugin-alternative.so
abhay    13023 12832  0 11:12 pts/0    00:00:00 grep ns
abhay@abhay-laptop:~$ kill -9 13023
bash: kill: (13023) - No such process
abhay@abhay-laptop:~$ 
**********************
but it says that , there is no such process as ns


so please folks help me with the same

The process you tried to kill (13023) was just the grep process that you started in the command you ran. Notice that your command includes piping the output of "ps -ef" to "grep ns". And the process you are tried to kill was "grep ns".
It does not look like there is any ns process running.


I hope that explains some of what is going on.
If you let me know what process you used to install ns2 in the first place, then I can give you a hand uninstalling it.

Cheers,
Marshall

---

