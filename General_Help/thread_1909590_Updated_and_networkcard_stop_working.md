---
title: "Updated and networkcard stop working"
date: 2012-01-15
forum: General Help
---

### Post by jsimoes on 2012-01-15
Runned ubuntu updates and network card stop working.
 
Network card PCI info is Realtek Semicondutores Co. Ltd. RTL 8139/8139C/8139C+ (rev 10)
 
I'm still learning ubuntu, I instaled and found the the PCI Ethernet Card on lshw and found the message "hasn't been claimed".
 
Don't know if it helps, but 2.6.33-37-generic was among the updates.
 
Can any one help me please.
 
"lspci | grep 8139  
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) "
201:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
1root@ubuntu:~$ lspci | [COLOR=#ff1493]grep[/COLOR] 8139 
201:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
1root@ubuntu:~$ lspci | [COLOR=#ff1493]grep[/COLOR] 8139 
201:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
 
"lsmod | [COLOR=#ff1493]grep[/COLOR] 8139 
8139too                18545  0 
8139cp                 16186  0 
mii                    4381  2 8139too,8139cp"
 
"dmesg | [COLOR=#ff1493]grep[/COLOR] 8139 
[    3.631942] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004) 
[    4.280361] 8139cp 0000:02:0d.0: This ([COLOR=#ff1493]id[/COLOR] 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 81939too 

[    4.284116] 8139too Fast Ethernet driver 0.9.28 
[    4.284423] 8139too 0000:02:0d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
8139too Chip not responding, ignoring board
8139too PCI INT A disabled
8139too proble of 0000:02:0d.0 failed with error -5

---

### Post by jsimoes on 2012-01-29
Tried the "sudo lshw -C network" command.
 
Listed the Ethernet Controller information, the word UNCLAIMED standup... I will search some more about this...
 
Found that: UNCLAIMED (no driver has been detected for this node)

---

### Post by jsimoes on 2012-01-29
Not very usefull so far... but found a reference to the driver...
[http://manpages.ubuntu.com/manpages/precise/en/man4/rl.4freebsd.html#contenttoc0](http://manpages.ubuntu.com/manpages/precise/en/man4/rl.4freebsd.html#contenttoc0)
 
The strangest thing... Realtek site says:
 
"Linux driver (driver has built-in the kernel)"
 
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)
 
I don't understand.

---

### Post by jmarcf on 2012-01-29
Try this fix I posted [http://ubuntuforums.org/showthread.php?t=1917331](http://ubuntuforums.org/showthread.php?t=1917331)

---

### Post by varunendra on 2012-01-31
Hi jsimoes, welcome to the forums!

The kernel version 2.6.33-37 is too old now. Which version of Ubuntu are  you using? I suggest to upgrade to at least 10.04 (natively supports kernel 2.6.35.xx), and update again.  Maybe that'll fix the issue automatically. Try the live CDs of both  10.04 and 11.10 to see if any works well for your hardware.

> **jmarcf said:**
> Try this fix I posted [http://ubuntuforums.org/showthread.php?t=1917331](http://ubuntuforums.org/showthread.php?t=1917331)
That fix is for 8168, isn't it? While the OP has 8139 chip:
> **jsimoes said:**
> 
"lspci | grep 8139  
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-**8139/8139C/8139C+** (rev 10) "

---

### Post by jsimoes on 2012-02-25
Thank you for the replies. 

Today I tried again and got it working, don't know why, but changing the networkcard to another PCI slot worked. I don't use this PC to often... probably an hardware contact problem... maybe it was a strange coincidence the update...

As for the version of the kernel:
$ uname -r
2.6.32-37-generic

In About Ubuntu I found the following: "You are using Ubuntu 10.04 LTS"

Once again, thank you for the replies.

---

