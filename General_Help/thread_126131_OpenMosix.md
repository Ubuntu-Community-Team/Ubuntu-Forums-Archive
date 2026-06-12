---
title: "OpenMosix"
date: 2006-02-05
forum: General Help
---

### Post by evilgold on 2006-02-05
I've searched and searched, but i cant find anything on getting openmosix running with ubuntu. Can anyone give me a HINT on how to do this?. I'm assuming i have to compile a new kernel with the modules... 

so my question is: where can i get the kernel sources, and how can I add openmosix to them.

---

### Post by Iandefor on 2006-02-05
[quote=evilgold]I've searched and searched, but i cant find anything on getting openmosix running with ubuntu. Can anyone give me a HINT on how to do this?. I'm assuming i have to compile a new kernel with the modules... 

so my question is: where can i get the kernel sources, and how can I add openmosix to them.[/quote] Open up a terminal, and type in ```
uname -r
``` it should return some number like "2.6.12-10-386". Now, enter ```
sudo aptitude install linux-source-2.6.12 linux-headers-386
``` Now you have kernel sources and headers. Then you can install openmosix. The howto is here: [http://howto.x-tend.be/openMosix-HOWTO/](http://howto.x-tend.be/openMosix-HOWTO/)

Just out of curiosity, why do you need a cluster?

---

### Post by evilgold on 2006-02-05
[QUOTE=Iandefor]Open up a terminal, and type in ```
uname -r
``` it should return some number like "2.6.12-10-386". Now, enter ```
sudo aptitude install linux-source-2.6.12 linux-headers-386
``` Now you have kernel sources and headers. Then you can install openmosix. The howto is here: [http://howto.x-tend.be/openMosix-HOWTO/](http://howto.x-tend.be/openMosix-HOWTO/)

Just out of curiosity, why do you need a cluster?[/QUOTE]


Thank you for the reply, I mainly want it just to see how it effects performance. I have 4 or so headless boxes that i really have no use for other then to cluster, most of my systems are <1ghz. I've done somthing similar with gentoo and distcc, this seemed like the next thing to try.

---

### Post by evilgold on 2006-02-07
Well I've read threw the openmosix how to, and gotten up to trying to compile the kernel but i am getting this error

```
/usr/src/linux-2.4.20/include/asm/smp.h:42: error: previous declaration of ‘smp_send_reschedule’ was here
In file included from /usr/src/linux-2.4.20/include/hpc/hpctask.h:13,
                 from /usr/src/linux-2.4.20/include/linux/sched.h:33,
                 from /usr/src/linux-2.4.20/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.20/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.20/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.20/include/hpc/defs.h:86: error: array type has incomplete element type
In file included from /usr/src/linux-2.4.20/include/linux/unistd.h:9,
                 from init/main.c:17:
/usr/src/linux-2.4.20/include/asm/unistd.h:375: warning: conflicting types for built-in function ‘_exit’
make: *** [init/main.o] Error 1

```

I used menuconfig to set it up, and then ran "make dep bzImage modules modules_install" as the how to says. I'm using gcc4, which  i think could be the problem but im not sure how to switch to a lower version.

I'm also using the kernel souce and openmosix patch for kernel 2.4.20, which is the version the guide uses. Unfortunetly the only files i found for 2.6 kernel are rpms. 

So what do i have setup wrong, and how do i get gcc make to use  version 3.4 or lower.

---

### Post by Tycoon on 2006-02-20
Hope I don't get flamed for being a new member and bringing back up an older post, but I need help too.  As I would just be making a new thread anyways I figured I could possibly help here a little bit along with getting help myself.  I'm brand new to Ubuntu myself.

I'm also using 5.10: so far I've gotten the 2.4.26 openmosix.RPM to install using Alien to convert to a .deb.  I had to manually add it to grub as it did not want to update.  When I rebooted into the 2.4 Kernel it immediately broke Gnome.  No surprise there.  Basically from what I've came to realize if you want the 2.4 Kernel in 5.10 you need to live without GUI since I've searched here and read Gnome relies on things from the 2.6 Kernel to work.

I then decided that I would really like to have a GUI so I re-installed 5.10 again.  This time I converted the 2.6 openMosix Beta.RPM that I already had downloaded and installed it.  I know it does not offer automatic migration but I only use the cluster for Distributed.net anyways and I could alway generate PIDs and migrate them by hand then forget about them for days/weeks/months till a power failure.

The 2.6 kernel rebooted fine.  I then installed the openMosix packages to get that on the system.  My problems came when I had to modify the /etc/hosts file.  I'm use to Fedora Core and openMosix clustering there.  Red Hat doesn't use the machine name in the hosts file.  So I went ahead and used my regular generic file without the machine name.  I then found out sudo relies on that, so DON"T remove it. You can not modify that again since you need sudo to edit the file!  I had to reboot into recovery mode using the install cd.  Once there I modified the hosts file, but to my dismay found out none of the modfications stay'd once I rebooted again.  I have done another clean install since.  

Can someone show me a working /etc/hosts file for Ubuntu?

I've used openMosix before to cluster 5 PCs to make ~2.5+ GHZ of processing power so I know how the gerenic ones look and work.  I'm just not to familiar with the machine name and IPv6 tables in the file.  I was hoping to try out Ubuntu with openMosix 2.6 and maybe get the thin clients or some diskless client program going as I do have machines without hard drives, floppy, and cd-roms.  I've already started to download 4.10 and I plan on rolling back to that as I believe that supports the 2.4 kernel if I can not get the hosts file problem solved.

---

### Post by Iandefor on 2006-02-20
@Tycoon: good luck with that :-D. I can't really help you with the /etc/hosts request, but I have a request for you: if you get OpenMOSIX working with Ubuntu, could you post a howto in the "Customization: Tips and Tricks" forum?

---

### Post by Tycoon on 2006-02-20
**Iandefor:**    Sure, no problem.  There has already been one user to do it with Warty / Hoary Ubuntu and [post about it]("http://www.ubuntuforums.org/showthread.php?t=17012").  I was just hoping to get it done with Breezy.  That way once Tab finishes the 2.6 openMosix it should be as simple as just running the converted .deb and upgrading to a fully operational openMosix cluster. WHEN I get it figured out I'll post the How-To.

---

### Post by Tycoon on 2006-02-20
Well I now have a cluster of one computer.  I need to install 5.10 on another pc and try to get them to link.

```
tycoon@ubuntu:/proc$ cat version
Linux version 2.6.15-openmosixbeta-om (root@mine2.x-tend.be) (gcc version 4.1.0 20060106 (Red Hat 4.1.0-0.14)) #1 Tue Jan 31 08:29:13 CET 2006

```

Example of my files:
```
tycoon@ubuntu:/etc$ cat hosts
192.168.5.1 localhost.localdomain
127.0.0.1 localhost ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
tycoon@ubuntu:/etc$ cat openmosix.map
1        192.168.5.1     1

```

Those should be correct and Sudo still works now!

```
tycoon@ubuntu:/etc/init.d$ sudo ./openmosix status
openMosix: Using map file /etc/openmosix.map
openMosix: WARN: Invalid configuration in map-file /etc/openmosix.map
openMosix: Falling back to autodiscovery mode using /sbin/omdiscd
Error: this is not OpenMosix!
tycoon@ubuntu:/etc/init.d$ sudo ./openmosix start
openMosix: Using map file /etc/openmosix.map
openMosix: WARN: Invalid configuration in map-file /etc/openmosix.map
openMosix: Falling back to autodiscovery mode using /sbin/omdiscd
Initializing openMosix...
Local processes already allowed to leave automatically.
automatic load-balancing already enabled.
touch: cannot touch `/var/lock/subsys//openmosix': No such file or directory
openMosix configuration was successful :)
tycoon@ubuntu:/etc/init.d$ sudo ./openmosix status
openMosix: Using map file /etc/openmosix.map
openMosix: WARN: Invalid configuration in map-file /etc/openmosix.map
openMosix: Falling back to autodiscovery mode using /sbin/omdiscd
Error: this is not OpenMosix!
tycoon@ubuntu:/etc/init.d$ mps
  PID TTY NODE STAT TIME COMMAND
 3499  ?    -1 S    0:00 bash
 3595  ?    -1 S    0:00 bash
 4153  ?    -1 R    0:00 mps
tycoon@ubuntu:/etc/init.d$ mosmon
mosmon: This is NOT a openMosix system!

```


As you can see it does not act at all like a finished Full Production openMosix.  I can not get it to read in at all from the openmosix.map now.  I'm pretty sure that .map file is correct as I removed everything else from it!  I think this is due to the 2.6 openMosix BETA leaving out pieces, as it's only suppose to be used for testers right now.  I guess not using a map file isn't a large problem if the omndiscd (automatic node discovery) works properly.  Worse case I ditch Breezy and go with Warty and put the 2.4.26 version on it.  I'm almost positive I can get that to work 100%.

---

### Post by Iandefor on 2006-02-20
^ Excellent! You're making pretty good progress with this. I commend you.

---

### Post by Tycoon on 2006-02-20
Well I've seem to hit a wall.  I installed Breezy on my HP E-PC 10 GB 866 P3 machine.  Installed the openMosix kernel and packages.  Both have the same kernels and maps but there not assigning node numbers to themselves so it's acting like openMosix is not configured.  I'm thinking it's a problem with omdiscd.  I need to get the map to work right.

Here's the current files:
```
tycoon@ubuntu:/etc$ cat hosts
192.168.5.1 localhost.localdomain
127.0.0.1 localhost ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
tycoon@ubuntu:/etc$ cat openmosix.map
1        192.168.5.1     2
tycoon@ubuntu:/etc/openmosix$ cat openmosix*
#
# This file can be used to change the default behaviour of the
# openMosix startup-script.
#

# Force autodiscovery-daemon to start, even with a valid .map-file
AUTODISC=1

# Specify which network interface the autodiscovery-daemon should listen to
AUTODISCIF=eth1

# Set the values of /proc/hpc/admin/overheads
# OVERHEADS=

# Set the values of /proc/hpc/admin/mfscosts
# MFSCOSTS=

# Set the openMosix node-id of this node
MYOMID=0

# Set maximum number of gateways between openMosix nodes (see man setpe)
# MOSGATES=

# Pass the following value to mosctl setspeed when starting the node
# man mosctl for details
 NODESPEED=10000

# Processes are allowed to migrate to other nodes.
 MIGRATE=yes

# Allow guest processes to arrive.
# BLOCK=no

# Don't use MFS
# MFS=yes

```

As you can see I'm manually forcing it to use auto discovery mode and assigning a node ID number.  So this pc should be Node # 0.

```
tycoon@ubuntu:/etc/init.d$ sudo ./openmosix reload
openMosix: Using map file /etc/openmosix.map
openMosix: WARN: Invalid configuration in map-file /etc/openmosix.map
openMosix: Falling back to autodiscovery mode using /sbin/omdiscd
Stopping openMosix...
openMosix: All remote processes were expelled and no further remote processes accepted.
Error: this is not OpenMosix!
Initializing openMosix...
Local processes already allowed to leave automatically.
automatic load-balancing already enabled.
touch: cannot touch `/var/lock/subsys//openmosix': No such file or directory
openMosix configuration was successful :)
tycoon@ubuntu:/etc/init.d$ mps
  PID TTY NODE STAT TIME COMMAND
 3595  ?    -1 S    0:00 bash
 4490  ?    -1 S    0:00 bash
 4501  ?    -1 R N227:33 ./dnetc
 5960  ?    -1 S    0:00 bash
 7751  ?    -1 S    0:00 bash
 7764  ?    -1 R N 11:39 ./dnetc -numcpu 0
 7765  ?    -1 S    0:00 bash
 8056  ?    -1 S    0:00 bash
 8296  ?    -1 R    0:00 mps
tycoon@ubuntu:/etc/init.d$ mosctl status
Node #(null) is not configured
tycoon@ubuntu:/etc/init.d$ ping 192.168.5.1
PING 192.168.5.1 (192.168.5.1) 56(84) bytes of data.
64 bytes from 192.168.5.1: icmp_seq=1 ttl=64 time=0.085 ms
64 bytes from 192.168.5.1: icmp_seq=2 ttl=64 time=0.067 ms
64 bytes from 192.168.5.1: icmp_seq=3 ttl=64 time=0.067 ms

--- 192.168.5.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2006ms
rtt min/avg/max/mdev = 0.067/0.073/0.085/0.008 ms
tycoon@ubuntu:/etc/init.d$ ping 192.168.5.2
PING 192.168.5.2 (192.168.5.2) 56(84) bytes of data.
64 bytes from 192.168.5.2: icmp_seq=1 ttl=64 time=0.215 ms
64 bytes from 192.168.5.2: icmp_seq=2 ttl=64 time=0.200 ms
64 bytes from 192.168.5.2: icmp_seq=3 ttl=64 time=0.200 ms

--- 192.168.5.2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.200/0.205/0.215/0.007 ms

```

As you can see it still says it's Node # -1, which means it's not configured.  As for the strange ./dnetc commands those are the Distributed.net Clients.  You need to run it with options -numcpu 0 to disable shared memory so it can migrate.

I went back took off autodiscovery and changed the openmosix.map to this:
```
tycoon@ubuntu:/etc$ cat openmosix.map
1       192.168.5.1     1
2       192.168.5.2     1
```

I shouldn't matter since the single line 1 192.168.5.1 2 means just start counting at 192.168.5.1 and the cluster only holds 2 pcs with the last being 192.168.5.2 and over course it made no difference.

Well, I think that's enough work for today.  Any ideas?   :cry:

---

### Post by Iandefor on 2006-02-20
You stepped out of my league a long time ago, sorry to say. I've no experience with clusters. Somebody, help!

---

### Post by Tycoon on 2006-02-21
[Found my answer to the map!]("http://sourceforge.net/mailarchive/forum.php?forum_id=7969&max_rows=25&style=nested&viewmonth=200506")

> From: <tab@sn...>arc.org (Vincent Hanquez) 
 Re: om2.6 installation questions?   
2005-06-28 03:20  
On Sun, Jun 26, 2005 at 08:40:48PM +0200, Kris Buytaert wrote:
> > 1 xxx.xxx.xxx.1 1
> > 2 xxx.xxx.xxx.2 2
> 
> The openmosix.map iss irrelevant for 2.6.

indeed.

> Did you enable debugging ?

there"s verbose migration option too that is useful.

> I remember from my tests that the output of wether a process migrated or
> not and on which node it was running wasn"t always correct. 
> 
> I also remember Tab already mailing me a fix for that , dunno if it is
> in SVN yet but I assume it is.

not it"s not, I was waiting for your feedback, and completly forget
about it.

-- 
Vincent Hanquez


[As for starting it:]("http://sourceforge.net/mailarchive/forum.php?thread_id=8912254&forum_id=7969")
> From: <tab@sn...>arc.org (Vincent Hanquez) 
 Re: openmosix 2.6   
2005-11-09 14:08  
On Mon, Nov 07, 2005 at 09:33:56PM +0200, jamie wrote:
> hi everyone,
> 
> How does one start openmosix 2.6? Is there an equivalent command to 
> /etc/init.d/openmosix start. Is the omd command equivalent? Or are these 
> tools still in heavy development. Is it best to revert back to the 2.4 
> kernel? Please explain.

2.6. is still in early development, and few people are actively working on it.
and for the moment I'm (unfortunately for oM) quite busy with my job.
things should get better though after the release.

you better use 2.4 in you want a "working" HPC.

-- 
Vincent Hanquez


[So exactly how do you order migration now:]("http://tab.snarc.org/docbook/om_internals.html")
> Ordering migration
Writing into the om/where file of a task (through /proc ) will start the migration process to the specified address. 

There's some specific keyword which specifies the local node, but most of the time the address is an identification number (ex: ipv4 address). We need to identify those addresses, which are written as a string into the dummy file. 

First we verify he address is not one of our keyword (ex: 'home'). If not we pass the identification to the function string_to_sockaddr(). This function will try sequentially each protocol parser that oM got (module or built-in). 

If a protocol parser succeeds to identify an address, the function returns with a valid sockaddr. If all protocol parser fails, the sockaddr is thus invalid, and the migration process is aborted. 

Example of migration ordering

# echo "192.168.1.1" > /proc/206/om/where
# echo "3ffe:a345::1" > /proc/2901/om/where
# echo "127.0.0.1" > /proc/999/om/where

[Another link explaining.]("http://howto.x-tend.be/openMosix.UKUUG2005/x117.html")

---

### Post by Tycoon on 2006-02-21
Sorry about hijacking your thread, evilgold.

OK, so further researching yeilds:  Map File is out totally, omdiscd is out totally, old 2.4 usertools are out.  Auto-discovery is now handled by the omd daemon, no clue where it is actually located but running it looks straight forward.
[ New user tools are released, but beware that there still not fully functional from the looks of the surgeforce.net trees:]("http://sourceforge.net/mailarchive/message.php?msg_id=13605515")
> omtoolsrepo: by yourself.
tabs trunk from: svn co svn://openmosix.snarc.org/om/userspace/trunk.

As for configuring the omd daemon most I can figure out is it works, but still says there all node -1 in mps.  That's mainly due to it controlling migration in the /proc system through the PIDs though.

[Example of a openMosix user starting up the omd daemon (left highlighting on so easier to find).]("http://article.gmane.org/gmane.linux.cluster.openmosix.general/9475/match=omd"):> [root <at> mpldev007 linux-2.6.13]# make xconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kconfig_load.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/i386/Kconfig

Turn on HPC (I enabled everything)

[root <at> mpldev007 linux-2.6.13]# make bzImage modules modules_install install

[root <at> mpldev007 daemon]# ./omd
sending to: 192.168.11.17
adding 192.168.11.17

Appears that the only thing holding me back is: getting the tools package and trying to start omd daemon.  Then I should beable to see other nodes and migrate by hand.  

If anyone wants to look around and see what's going on [check here.]("http://news.gmane.org/gmane.linux.cluster.openmosix.general")

I'm spending way to much time on this when I should be studying for a Linear Algebra Test tomorrow.  If I keep this up I'm going to be a 6th year senior...

---

### Post by Tycoon on 2006-02-21
Here's the latest update:
```
sudo apt-get update

sudo apt-get install subversion
sudo svn co svn://openmosix.snarc.org/om/userspace/trunk/
```
(Note the previous posted svn line is NOT correct, the link was wrong on the webpage due to a typo.)

That should get you up to the point where you have the trunk directory which has the tools, omd daemon, and various extras in it.

```
tycoon@ubuntu:~$ cd trunk
tycoon@ubuntu:~/trunk$ ls
AUTHORS  COPYING  daemon  debug  qa  README  tools
tycoon@ubuntu:~/trunk$ cd daemon
tycoon@ubuntu:~/trunk/daemon$ sudo cp omd.conf omd.conf_backup
Password:
tycoon@ubuntu:~/trunk/daemon$ sudo vi omd.conf
tycoon@ubuntu:~/trunk/daemon$ cat omd.conf
## This file contains the configuration of omd

## Lines that start in a # are comments.
## Most options should work fine with there defaults.


# Information about the network used by openmosix
[NETWORK]

# The port openmosix receives admin information on
PORT_ADMIN = 2901

# The port openmosix receives information on
PORT_INFO = 5428

# The port openmosix uses to find other nodes on the network
PORT_DISCOVERY = 5429

# The address openmosix uses to send broadcast messages over the network
# This should be the broadcast address used for openmosix's subnet
# You can use auto here if you would like openmosix to guess the
# broadcast address that it should use.
# Please note that auto is still alpha as of 040828
ADDR_BROADCAST = 192.168.5.255

# The address of this node on the network.  If you would like openmosix
# to try to guess this address then you can use a value of auto.
# Please note that auto is still alpha as of 040828
ADDR_MY = 192.168.5.1
tycoon@ubuntu:~/trunk/daemon$ ./omd
adding 127.0.0.1
sending to: 192.168.5.2
adding 192.168.5.2

```

I could not get it work without with the default filt that had AUTO flags on the addresses.  You also need to configure the other pc in the same but of course use the correct address.

Now my problem is everytime I try to manually migrate a PID where location it kills the process.  So I'll have to work on that later.

---

### Post by Iandefor on 2006-02-21
It strikes me that it might not be worth the trouble of getting Ubuntu running as a cluster?

---

### Post by Tycoon on 2006-02-21
Well it's the whole fact I'm almost positive I could get 4.10 ubuntu and 2.4.26 openmosix kernel working in about 10-15 minutes.  I've done that before with Fedora Core 1.  But the new 2.6.15 package is still in BETA form so basically there's little to no support or how-to's to use it.  As it's for testers only that don't mind trashing a system.  Basically I'm digging through the net to figure stuff out on my own.  It would be nice to have a How-To that someone already put together and all I did was printed and 3 hole punched like my 2.4 openmosix version.

When the 2.4.26 works it's extremely nice.  You just configure your .map file and it starts as soon as it boots.  You can add nodes on the fly and stuff as they boot and come in as long as there on the map file to begin with.  Processes automatically migrate and balance out for you.  You can see openmosix CPU speed configured (P3 1GHZ = 10000), load, and memory installed in the nodes.

I'd just hate to stop when I'm this close to getting it to work.  I believe something very bad is happening when it passes it to the client, but would be nice if I knew the commands to turn debugging on.  :evil:  But like you have stated it might just not be worth the effort, untill there is a fully functional user releasement package.

So unless anyone has some ideas I'll be erasing this setup and going with 4.10 Warty.  Just sad because I really wanted to try out thin clients and use a diskless implementation this time for less overhead on equipment.

I'm planning on trying out ['autocluster']("http://autocluster.wustl.edu"), unless anyone has any better ideas on software?

---

### Post by evilgold on 2006-02-22
wow, your way ahead of where i got, I couldnt even get the 2.6 openmosix kernel to boot. I'm afraid i cant really help you out, because I've pretty much just decided to wait for an offical kernel patch, instead of using the rpms.

---

### Post by zbyte64 on 2006-03-31
Hi, I just tried to get openmosix 2.6 up and i got the kernel to compile and boot :) Unfortunately i couldn't compile vesafb-tng :( I'll actually find out if its working when i get home and plug it in to my other openmosix computer. Now for how i got this far:

I had a terrible time trying to get a 2.6 kernel + openmosix patch so instead i used my gentoo box and emerge the 2.6 openmosx sources and then copied it to my ubuntu laptop. I compiled and it worked! Then for user space i found a repository that has just what i was looking for: deb [http://puga.vdu.lt/debian](http://puga.vdu.lt/debian) sarge main  -i installed the openmosix user space tools from there and it seems to work. But I won't know till i get home... anyways good luck.

---

### Post by Tycoon on 2006-04-04
Thanks for the update!

Do you know if you still have to manually write into the /proc system to force migration?

I eventually just gave up and switched to clusterknoppix.  It's old yes, but it works.  And I can do PXE booting right off the live cd.  I eventually got tired of rebuilding the OS each time with distributed.net software and network everytime I lost power so I did a HDD install of it and lost my PXE booting ability.  Small price to pay for more stability though.  If openmosix ever finishes the 2.6 fully I'll convert back to ubuntu and run it.

---

### Post by rick_1010 on 2006-09-17
So it sounds like the cluster will work fine in Ubuntu Hoary.. I am trying to get this to work also on Ubuntu and have tried Cluster Knoppix before. Cluster Knoppix doesn't seem to be very usable to me unless you literally go through and re-do everything in the system except for the openmosix part, as it doesn't have an effective package manager, it seems that apt-get is not working correctly without making some major changes (this is all because its only meant to be a bootable cd), anyways:

If Ubuntu Hoary version is used, wouldn't this still be a fairly good solution? Would it be possible to run some newer softwares on Hoary if you added in the necessary dependencies? If it would work I think its fine to have to use an older version of an distro, at least for my needs, I already knew going in this would take some work so as long as newer software can be used it should be ok.

---

