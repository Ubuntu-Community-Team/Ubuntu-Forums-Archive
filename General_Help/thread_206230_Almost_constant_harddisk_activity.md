---
title: "Almost constant harddisk activity"
date: 2006-06-29
forum: General Help
---

### Post by tjansson on 2006-06-29
Formerly I ran Mandriva and I when doing on nothing on my laptop my harddisk spun down and there were now harddisk activity for minuttes. I use gkrellm, so I is easy to see that there is activity or not.  

However in Ubuntu my harddisk always writes something small to the harddisk every second or so. I tried to reduce my swappiness with 
```
sysctl -w vm.swappiness=10
```
but that didn't help. 

Then I was sugested to run the command
```

dirac ~ # find / -mount -mmin -5
/var/log/syslog
/var/log/daemon.log

```
which reports the files that haven been written to (or alter timestamp) on the harddisk in the last five minuttes. 

Appearently something is writing is looking into the logfiles and alters their timestamp every second or so. What could it be and even more important - how do I disable it?

---

### Post by mannheim on 2006-06-29
The first step might be to look at those two log files. What is writing to them?

On my system, most things there are related to user activity or cron jobs.

---

### Post by tjansson on 2006-06-29
[QUOTE=mannheim]The first step might be to look at those two log files. What is writing to them?
On my system, most things there are related to user activity or cron jobs.[/QUOTE]

On my laptop there are two network devices, eth0 which the wireless and the one i'm currently using. The second one is eth1 is for cabled network but is not connected and I seldom use - only at the university. 

```
dirac ~ # tail /var/log/syslog
Jun 30 00:26:42 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jun 30 00:26:53 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Jun 30 00:27:08 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Jun 30 00:27:27 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jun 30 00:27:38 localhost dhclient: No DHCPOFFERS received.
Jun 30 00:27:38 localhost dhclient: No working leases in persistent database - sleeping.
Jun 30 00:32:59 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jun 30 00:33:03 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jun 30 00:33:11 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Jun 30 00:33:27 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
dirac ~ # tail /var/log/daemon.log
Jun 30 00:27:38 localhost dhclient: No DHCPOFFERS received.
Jun 30 00:27:38 localhost dhclient: No working leases in persistent database - sleeping.
Jun 30 00:32:59 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jun 30 00:33:03 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jun 30 00:33:11 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Jun 30 00:33:27 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
Jun 30 00:33:47 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jun 30 00:33:54 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Jun 30 00:34:00 localhost dhclient: No DHCPOFFERS received.
Jun 30 00:34:00 localhost dhclient: No working leases in persistent database - sleeping.

```

---

### Post by mannheim on 2006-06-29
As an experiment, you could try disabling eth1 while you are not using it. (Eg, if you are using gnome, do System->Administration->Networking, select eth1 and click "Deactivate".) See if it helps.

Maybe someone knows how to eliminate those log entries without deactivating the eth1 interface.

---

### Post by syadnom on 2006-06-29
edit /etc/dhcp3/dhclient.conf


should look like 
> 
#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


and should be changed to

> 
#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
**retry 3600;**
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


this was the dhcp wont retry the connection for 1 hour instead of every minute.  we need not bother changing the timeout as you will likely not be concerned with the dhcp trying to connect for the first minute.


see if that helps you out

---

### Post by tjansson on 2006-06-30
I now removed "auto eth1" from the /etc/network/interfaces file and altered the dhclient.conf file to retry every hour instead, but the harddisk activity is still there. The writings continues but now the files are the same, but without any changes in them:

```

dirac tjansson # find / -mount -mmin -10
/var/log/syslog
/var/log/messages
/var/tmp/kdecache-tjansson/http/cleaned
/tmp/ksocket-tjansson

dirac tjansson # tail /var/log/syslog
Jun 30 11:57:35 localhost -- MARK --
Jun 30 12:17:01 localhost /USR/SBIN/CRON[8501]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jun 30 12:37:36 localhost -- MARK --
Jun 30 12:57:36 localhost -- MARK --
Jun 30 13:17:01 localhost /USR/SBIN/CRON[9654]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jun 30 13:37:36 localhost -- MARK --
Jun 30 13:57:38 localhost -- MARK --
Jun 30 14:17:01 localhost /USR/SBIN/CRON[10917]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jun 30 14:37:40 localhost -- MARK --
Jun 30 14:57:41 localhost -- MARK --

dirac tjansson # tail /var/log/messages
Jun 30 11:57:35 localhost -- MARK --
Jun 30 12:17:35 localhost -- MARK --
Jun 30 12:37:36 localhost -- MARK --
Jun 30 12:57:36 localhost -- MARK --
Jun 30 13:17:36 localhost -- MARK --
Jun 30 13:37:36 localhost -- MARK --
Jun 30 13:57:38 localhost -- MARK --
Jun 30 14:17:40 localhost -- MARK --
Jun 30 14:37:40 localhost -- MARK --
Jun 30 14:57:41 localhost -- MARK --

```

So now nothing is beeing written to the harddisk every second or so even though gkrellm shows that it does. It is not a gkrellm thing, as I can hear my harddisk spinning and clicking when it writes to the harddisk.

---

### Post by ayoli on 2006-06-30
this  hd activity could be writing of the journal of an ext3fs.

---

### Post by Castar on 2006-06-30
Or maybe Beagle indexing?

---

### Post by tjansson on 2006-07-02
[QUOTE=ayoli]this  hd activity could be writing of the journal of an ext3fs.[/QUOTE]
It could be so, but I do not think so since it is the same ext3 partion as I used under Mandriva, where there was no HD activity. Maybe Ubuntu handels ext3 different than Mandriva?

---

### Post by tjansson on 2006-07-02
[QUOTE=Castar]Or maybe Beagle indexing?[/QUOTE]
I don't use beagle at all, so that can't be the problem. But thanks for trying :D

---

### Post by freakcode on 2006-07-02
First of all, sorry for the english, its not my native language.

tjansson:

I'm with the exactly same problem! Don't know why other people doesnt have this problem or dont pay attention to hdd activity... Its like 1 or 2 seconds, and then there is a very fast read/write.

In my case, its even worse, because when I have hdd I/O, OpenGL performance degrades (the OpenGL app simply FREEZES during the hdd access).

Playing around, I found what was making those reads/writes... I stopped dbus service before getting into X, and the activity stopped. BUT stopping dbus caused bugs on Gnome and disabled some of its features. So, stoping it isnt the "right thing" to do. And before you ask me, NO, IT IS NOT SWAP (0k used, always).

Another thing I found is that, when I run X from root account, my OpenGL apps dont "freezes" during the hd I/O. It run smooth, but the hd is also in activity. I think this happens because "root" processes has more privilege or attention from the kernel than user accounts, so it dont "freeze" even with the hd constant accesses.

So, I have no solution at all, because I cant use the system on root account everytime, neither stop dbus.

I AM THE THIRD PERSON WHO COMPLAINS ABOUT THIS ON THE FORUM. PLEASE, MAKE THIS THREAD TO BE A BUG-REPORT.

For helping on solutions, following is my setup:

Hardware:
AMD Athlon 64 3000+
Asus K8N (nForce3 chipset)
512 DDR400 RAM
PATA Seagate 40gb 7200 RPM on /dev/hda (where Linux is installed)
MSI GeForce FX5200

Some Linux setup info:

$ uname -a
Linux 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686 GNU/Linux

$ hdparm  /dev/hda
/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 78165360, start = 0

Notes:
Using nvidia modules from the binary installer, version 8762 and installed it by hand.
The same problem was happening with the original 'nv' driver from ubuntu.

Installed linux-kernel-k7 with synaptic.
The same problem was happening with the original 386 kernel from ubuntu.

*** The only thing that stops the activity is killing dbus! ***

---

### Post by heldal on 2006-07-03
The dbus/HAL problem is describes elsewhere. Eg:

[http://ubuntuforums.org/showthread.php?t=188901](http://ubuntuforums.org/showthread.php?t=188901)

A bugreport has also been submitted:

[https://launchpad.net/distros/ubuntu/+bug/48499](https://launchpad.net/distros/ubuntu/+bug/48499)

---

### Post by jonrkc on 2006-07-08
I'm having the same problem, and as a result my CPU is heating up much more than it needs to--my brand new CPU.  :(

So if it helps bring attention to whatever is wrong here, I'm putting in my bid for a fix, too.

EDIT: After viewing the bug reports, I'd better add that my problem is the almost constant DHCPDiscover messages that are being logged.  That's the apparent cause of the frantic activity in my case, on a desktop machine with two hard drives on the same primary IDE channel, and a CD/DVD-burner as master on the secondary IDE channel, nothing in slave position.

---

