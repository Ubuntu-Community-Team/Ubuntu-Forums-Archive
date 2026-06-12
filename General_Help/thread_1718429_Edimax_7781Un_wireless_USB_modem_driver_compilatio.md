---
title: "Edimax 7781Un wireless USB modem driver compilation and installation problems"
date: 2011-03-31
forum: General Help
---

### Post by shanept on 2011-03-31
Hi forums,

I recently bought the Edimax 7781Un wireless modem specifically because it works with Linux. The OS does recognise the device and tries to connect to the router, however it connects and has the two semi-circles going round then it eventually disconnects. I thought it was my wireless device with little signal strength therefore I bought this one. However this one connected once for 20 seconds, 89% strength and disconnects. I booted up win7 and it works fine, so I have put it down to the driver or the OS.

Trying to compile the driver, I am up to the make step after following instruction [here]("http://ubuntuforums.org/showthread.php?p=7900042"). I type make, it does a few things and errors a fair few things, the last line ending in [make] *** [LINUX] Error 2

Another possibility (I think) for this connection problem could be my AMP installation, however I have neither apache, php or mysql running and I still have the problem.

I read somewhere that make requires more files, is this true? And if it is, where can I get it without an internet connection on my linuxbox? (I am currently using my brothers w7 computer).

Thanking you in advance,
shanept

---

### Post by shanept on 2011-03-31
Sorry I forgot to mention I can see the access point

---

### Post by shanept on 2011-03-31
It is currently working, I am using it now however it will most likely drop out any second. Please help!!!

---

### Post by shanept on 2011-03-31
Error message from compilation:
root@shane-ubuntu:/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0# make
make -C tools
make[1]: Entering directory `/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.35-28-generic-pae/build SUBDIRS=/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
  CC [M]  /home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o
/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c: In function &#8216;RTMPReadParametersHook&#8217;:
/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:928: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:929: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:930: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:930: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:1593: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:1594: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
make[2]: *** [/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/shane/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
make: *** [LINUX] Error 2

---

