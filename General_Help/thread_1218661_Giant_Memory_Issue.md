---
title: "Giant Memory Issue"
date: 2009-07-20
forum: General Help
---

### Post by neogenz on 2009-07-20
I'm a newbie to linux and got Ubuntu 9.0.4 installed as a program in XP. I boot into Ubuntu most the time for the past 2 weeks now to get myself familiarize with the system.
I found a few issues but many are solved by my own research, but I have a big problem with how Ubuntu handles SWAP memory.

I got 1.2GB of ram, and 1024MB of SWAP. Ubuntu seem to use a lot of SWAP at times to an unacceptable level.
Yesterday, my laptop slowed down significantly so I check System Monitor. The memory usage is only 275.3MB (22.2%) an Swap usage is (99.8%)! I was only watching two films using mplayer and surfed a little with firefox.
This is not the first time it happened, I had issues but I increased the swap to what it is now, but really dissapointing memory managment would just chew it away.

I also took some screenshot, any help is appreciated.

---

### Post by HermanAB on 2009-07-20
Howdy,

How do you know how much swap is used?

Try to use 'htop' to check system performance.  It tends to give a better picture of what is going on than most other performance tools.

Anyhow, movie decoding is processor intensive.  Your machine more likely runs out of processor steam, not memory space.

---

### Post by lensman3 on 2009-07-20
What does the "free" command line say.  "free" reports the memory from the appropriate file /proc/meminfo.

It is possible under Linux to create a file type swap file that is just like a Windows XP swap file.  The command that creates it is "swapon".  The general rule of thumb is 2x your ram.  Linux doesn't need a partition for swapping, it can use a file.

Linux uses free memory to buffer I/O.  The only part of a program that would get swapped out is the data stacks.  The program that is running is just swapped back in from where it resides on the HD if a code page was swapped out.  Linux uses free memory differently than Windows and reports it differently.

Hope this helps.

---

### Post by earthpigg on 2009-07-21
the 99% swap usage is _*very*_ unusual. something is amis.

have you done anything similar to what is recommended in this thread? or possibly some 'power user' trying to help you?

[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

can you show us the output of this command, please:

> cat /etc/sysctl.conf


edit: the command you want to run to take a look at current memory usage is this - 

> free -m

the -m tag shows it in megabytes, which are easier to read/comprehend/etc

---

### Post by neogenz on 2009-07-21
My System Monitor (system>admin>system monitor) is where I got my stats from, and when my hdd start to read and write  (and slowing down my system significantly) for a prolong period of time I started to pay some attention to the swap. This is the same problem which led me to find the swap was only about 250mb (default after install, no UI to config) in the first place....

Free tells me this:
@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       1268580    1238880      29700          0     168508     838932
-/+ buffers/cache:     231440    1037140
Swap:      1048568        860    1047708




cat /etc/sysctl.conf 			 		tells me this:
@ubuntu:~$ cat /etc/sysctl.conf 
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling ([http://lkml.org/lkml/2008/2/5/167](http://lkml.org/lkml/2008/2/5/167)),
# and is not recommended.
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
# The contents of /proc/<pid>/maps and smaps files are only visible to 
# readers that are allowed to ptrace() the process
# kernel.maps_protect = 1



These are the stats right now, I know this problem is hard to diagonis as it's hard to replicate, what should I be looking when this problem come again?
I will also try the tweak as well.
And thanks for all your quick replies~ I love the sense of community here. :P

---

### Post by earthpigg on 2009-07-21
> @ubuntu:~$ free
total used free shared buffers cached
Mem: 1268580 1238880 29700 0 168508 838932
-/+ buffers/cache: 231440 1037140
Swap: 1048568 860 1047708

that is telling us that only 860 kb of swap space is being used, not very significant.... meaning you weren't having the problem when you posted that.

next time you are _*in the middle of*_ experiencing the problem, show us the output of the following command, please:

> free _**-m**_

then, open up gnome-system-monitor, and sort by %cpu. tell us what the top 2 or 3 processes are.

---

