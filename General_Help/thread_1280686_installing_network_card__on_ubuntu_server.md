---
title: "installing network card  on ubuntu server"
date: 2009-10-02
forum: General Help
---

### Post by enricoca on 2009-10-02
HI guys!
I installed UBUNTU 8.04.2 Server. On my PC, i have this network card: Atlantis-Land A02-SG32 ver.1.2, which mount the RTL8169 chipset. All works fine but the speed of the nic is abnormally low (it's less than 1MB/s). On the same system, i installed windows xp and the speed is about 13MB/s, so i don't think the card is damaged. The current driver installed, is r8169 and the output of ethtool command has, beetwen other stuff, the following lines:
Supported link modes: 10baseT..
100baseT..
1000baseT/Full
....
Speed: 1000Mb/s
Duplex: Full
Port: Twisted Pair
...
So, it seams it's all ok.
So, I think it's a driver problem. I tried to install the driver provided with the NIC, but I get errors.
In the driver CD, I have a folder:
2.4.x_2.6.x that contains Makefile and the subfolder src. The src folder contains others makefile and a source file named r1000_n.c. I copied the 2.4.x_2.6.x folder in my home directory, than i cd in 2.4.x_2.6.x folder and typed the command:
make install
but i get the error:
....
Makefile:28: /src/Makefile_linux26x: No such file or directory
.....
In the subfolder src of the folder 2.4.x_2.6.x, there is the file Makefile_linux26x, but from the error message it seems ittry to look for it in the path /src and not in the correct path /home/my_name/2.4.x_2.6.x/src
Any suggestion? how can i install the r1000_n driver? 
 
PS: I have already installed the build-essential package
 
Thanx in advance for any reply!
 
Enrico

---

### Post by Giblet5 on 2009-10-02
Your manufacturer's driver source is assuming a specific linux distro that you are not using (knoppix, maybe).

How are you testing the throughput of your nic?
What's at the other end of the wire from that nic?

Windows doesn't make a good test platform; it doesn't network well, even with Windows, and it's worse with anything else.

What's the output of ```
sudo ipconfig eth0
``` assuming that nic is eth0...

---

### Post by enricoca on 2009-10-02
Hi Giblet5,
 
i tested the throughput connecting the linux machine to a windows xp machine (with an integrated gigabit nic) )with a crossover cat5e cable. On unbuntu server, I installed Samba server ver. 3.0.28a, and the test consist in copying a 448MB-sized folder from windows machine to the share /backup on the linux machine (the medium file size, is 279KB). On the linux machine, ther is also an integrated Rhine 100Mbit/s nic, which throughput is about 9-10MB/s with the same test. (so..among the other stuff...it seems that the atlantis-land nic is not so good even in windows OS, because is only 3MB/s faster than a simple 100Mbit/s Rhine nic!)
 
The output of ifconfig eth1 is:
 
eth1      Link encap:Ethernet  HWaddr 00:18:e7:18:7f:41  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::218:e7ff:fe18:7f41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:121628 (118.7 KB)  TX bytes:36434 (35.5 KB)
          Interrupt:17 Base address:0x400 
 
So, any suggestion?
 
Thanx.
 
Enrico

---

### Post by Giblet5 on 2009-10-02
Windows does not communicate with linux, unix, vms, mvs, solaris, hpux, etc. very well at all.

I won't say it's intentional, even if it clearly is.

That said, you may not be able to get very good throughput to a Windows box.

I just did some tests.

Copying a 1G file from 9.10 to Vista Ultimate over a 1Gbps LAN yielded 14MBps rate (avg). That's 140Mbps out of 1000Mbps.

Copying that same 1G file from 9.10 to a 9.04 linux box yielded 83MBps (avg). That's 830Mbps out of 1000Mbps.

That's a big difference, huh.

That same Vista box can transfer that 1G file to an XP box at 28MBps avg. The only reason it's THAT fast is because XP isn't as messed up as Vista (and because Vista recognizes the other end as Windows).

Networking is, and has always been, an afterthought with Microsoft. From the time they licensed TCPIP from Trumpet Winsock, back in the late 80's, until today when they still dump that trash in wsockNNN.dll, networking is a kluge with them. At least they have crummy networking: You used to have to buy it from a third party cuz Microsoft was all "net hunh?".

Teh Googles has more on this. The terms "vista", "slow", and "network" will turn up a discussion or two on the topic.

The short of it is that it's a mistake to interact with Windows and assume that slowness is on the non-Windows end.

---

### Post by Giblet5 on 2009-10-02
Valid test:

```
sudo apt-get install openssh-server
```

Select a file of size, eg MyBigFile.iso
```
scp MyBigFile.iso 'hostname':MyBigFile-copy.iso
```

This will dump stats during the transfer, although the stats will be skewed by the fact that it's being used to send AND receive, plus the disk I/O hit. Take the final "MB/s" value and guesstimate an additional 25% to offset the skewed double I/O and that's a rough estimate of what that nic can push.

---

### Post by sabre2th on 2009-10-02
Honestly, I didn't read every word here, but it seems like a driver issue.

I had a similar issue with a wireless adapter on my Myth box.  The solution for me was to install linux-backports-modules.  After a restart, the signal and speed were back where they should be.

As for the Windows thing... it's not so much MS/Windows sabotage as Samba just isn't that fast.

---

### Post by enricoca on 2009-10-03
I agree that is not ideal the interaction between linux and windows world but....sometimes you must do it. So i would like to install the r1000_n driver in place of the r8169. I don't know if it's better but i would try. can you give me some help to do it? the readme.txt file of the nic tell only to execute make install command but i get the error i showed above:
 
....
Makefile:28: /src/Makefile_linux26x: No such file or directory
.....

@ sabre2th
 
can you tell me how to install linux-backports-modules?  thanx
 
enrico

---

### Post by sabre2th on 2009-10-03
> **enricoca said:**
> I agree that is not ideal the interaction between linux and windows world but....sometimes you must do it. So i would like to install the r1000_n driver in place of the r8169. I don't know if it's better but i would try. can you give me some help to do it? the readme.txt file of the nic tell only to execute make install command but i get the error i showed above:
 
....
Makefile:28: /src/Makefile_linux26x: No such file or directory
.....

@ sabre2th
 
can you tell me how to install linux-backports-modules?  thanx
 
enrico
It's something of a long shot, but it's quick and easy to try.  Assuming you're running Hardy, just do this in terminal and reboot:
```
sudo apt-get install linux-backports-modules-hardy
```

If it doesn't work, go ahead and remove it:
```
sudo apt-get purge linux-backports-modules-hardy
```

Good luck!

---

### Post by dcstar on 2009-10-03
[http://ubuntuforums.org/showthread.php?p=7619818](http://ubuntuforums.org/showthread.php?p=7619818)

---

### Post by enricoca on 2009-10-05
thank you dcstar,
I read your link but it's not a file system mounting problem. In the same linux box, i have installed a 10/100Mb/s nic that is more than 10 times faster than the AtlantisLand _gigabit_ nic! so... I think is a driver problem. I just would like to try install the provided driver, but i get error! I need the correct procedure to install the r1000_n.c driver.
 
Enrico

---

