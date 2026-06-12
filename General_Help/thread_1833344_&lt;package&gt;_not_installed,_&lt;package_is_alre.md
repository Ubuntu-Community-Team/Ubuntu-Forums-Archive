---
title: "&lt;package&gt; not installed, &lt;package is already newest&gt;"
date: 2011-08-25
forum: General Help
---

### Post by altjx on 2011-08-25
Can someone please explain this to me? 

```
root@bt:~# onesixtyone 192.168.0.1
The program 'onesixtyone' is currently not installed.  You can install it by typing:
apt-get install onesixtyone
root@bt:~# sudo apt-get install onesixtyone
Reading package lists... Done
Building dependency tree       
Reading state information... Done
onesixtyone is already the newest version.
The following packages were automatically installed and are no longer required:
  iw linux-source-2.6.39.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by bruno9779 on 2011-08-25
It looks like onesixtyone is not in your PATH.

This could mean 3 things:

1. You have removed onesixtyone from PATH by mistake. In this case "sudo apt-get purge onesixtyone && sudo apt-get install onesixtyone"

2. Onesixtyone is not meant to be run. (eg. a library)

3. The installation of onesixtyone failed at some point. If so report it as a bug.

---

### Post by altjx on 2011-08-25
```
root@bt:~# apt-get purge onesixtyone && apt-get install onesixtyone
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  iw linux-source-2.6.39.4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  onesixtyone*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 226260 files and directories currently installed.)
Removing onesixtyone ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  iw linux-source-2.6.39.4
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  onesixtyone
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8,328B of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package onesixtyone.
(Reading database ... 226256 files and directories currently installed.)
Unpacking onesixtyone (from .../onesixtyone_0.3.2-bt4_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up onesixtyone (0.3.2-bt4) ...
root@bt:~# onesixtyone 192.168.0.1
The program 'onesixtyone' is currently not installed.  You can install it by typing:
apt-get install onesixtyone


```

Same issue. :( Thanks for your help.

---

### Post by bruno9779 on 2011-08-25
I have tried installing it myself, and it seems to work fine.

The command :

```
sudo find / -name onesixtyone
```

should give you the two following results:
```

/usr/share/doc/onesixtyone
/usr/bin/onesixtyone
```

If not, it really is an install bug

---

### Post by bruno9779 on 2011-08-25
You can download onesixtyone from here [http://www.phreedom.org/solar/onesixtyone/](http://www.phreedom.org/solar/onesixtyone/)

just unpack it somewhere like your home folder, cd there and:
```

sudo chmod +x onesixtyone
sudo mv onesixtyone /usr/bin
```

Now it is in your PATH. And should work fine.

If you want to remove it, you should do so manually:

```
sudo rm /usr/bin/onesityone
```

---

### Post by fdrake on 2011-08-25
i had the same problem with one command. The issue was that the name was a little bit different or longer than the package name. The program is for sure installed don't worry!. try this, bash will give you a suggestions of the commands:

```

apropos onesix

```

ps. you should not be logged as root to install a program and to run SNMP scanner for your net.

---

### Post by altjx on 2011-08-25
> **fdrake said:**
> i had the same problem with one command. The issue was that the name was a little bit different or longer than the package name. The program is for sure installed don't worry!. try this, bash will give you a suggestions of the commands:

```

apropos onesix

```ps. you should not be logged as root to install a program and to run SNMP scanner for your net.

I'm actually using BackTrack 5, but I've seen people on here post about it. I knew I'd get a faster response. Going to try that in a minute. Thanks guys. I'll update when I try it :)

---

### Post by bruno9779 on 2011-08-25
> **altjx said:**
> I'm actually using BackTrack 5,

That makes sense, I was wondering what was that -bt4 at the end of the program version

@fdrake in that case, apt wouldn't have advised to install onesixtyone. 

For example try to type onesixty**five** instead. It gives you an error and no install advice

---

### Post by altjx on 2011-08-25
> **bruno9779 said:**
> That makes sense, I was wondering what was that -bt4 at the end of the program version

Haha, yeah. Sorry if this pissed anyone off, I'm wondering if the solution will be very similar though. These forums are much more friendly it seems and much quicker with response. Just running through a BT4 book to familiarize myself with some pentesting tools before my promotion next year. Staying ahead =)

---

### Post by fdrake on 2011-08-25
> **bruno9779 said:**
> 
@fdrake in that case, apt wouldn't have advised to install onesixtyone. 


from the his first post

> ```

root@bt:~# sudo apt-get install onesixtyone
Reading package lists... Done
Building dependency tree       
Reading state information... Done
onesixtyone is already the newest version.

```

from his second post:

> ```

root@bt:~# apt-get purge onesixtyone && apt-get install onesixtyone
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  iw linux-source-2.6.39.4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  onesixtyone*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 226260 files and directories currently installed.)
Removing onesixtyone ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  iw linux-source-2.6.39.4
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  onesixtyone
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.

```

the package was already installed. apt is not the problem.
btw. he did not post yet 
```
whereis onesixtyone

```

---

### Post by bruno9779 on 2011-08-25
Fdrake, I meant about the name of the program, not about being root.

You are right, there is no need to log in as root to install a program and run a SNMP scanner.

But if onesixtyone command name had been different from the program name, apt wouldn't have advised to install onesixtyone.

---

### Post by fdrake on 2011-08-25
ops. i thought you meant about the program, not being installed, since you said about apt. my bad.

BTW. i installed onesixtyone in lucid and it runs by the command:
```

onesixtyone

```

something is fishy.....

---

### Post by altjx on 2011-08-25
Well, I was following the guide and it mentioned 

> onesixtyone
The onesixtyone can be used as a Simple Network Monitoring Protocol (SNMP)
scanner to find out if the SNMP string exists on a device. The difference with other
SNMP scanners is that it sends all SNMP requests as fast as it can (10 milliseconds
apart). Then it waits for responses and logs them. If the device is available, then it
will send responses containing the SNMP string.
To access onesixtyone, go to the menu Backtrack | Network Mapping | Identify
Live Hosts | Onesixtyone or you can open up a console and type onesixtyone.
Let's try onesixtyone to find out the SNMP strings used by a device located at
192.168.1.1. The following is the appropriate command:
#onesixtyone 192.168.1.1
The following is the scanning result:
Scanning 1 hosts, 2 communities
192.168.1.1 [public] VPN Router
192.168.1.1 [private] VPN Router
The SNMP strings found are public and private.
If we want the scanning to be more verbose, we can give option -d:
#onesixtyone -d 192.168.1.1
And the result is:
Debug level 1
Target ip read from command line: 192.168.1.1
2 communities: public private
Waiting for 10 milliseconds between packets
Scanning 1 hosts, 2 communities
Trying community public
Trying community private
192.168.1.1 [public] VPN Router
All packets sent, waiting for responses.
192.168.1.1 [private] VPN Router
done.

so i was only following that. I'm guessing the above posts won't help though since I was using BT I'm assuming, or think it's still worth a try? in the middle of a scan right now.

---

### Post by bruno9779 on 2011-08-25
before doing anything else, try the 2 commands we suggested:

```
whereis onesixtyone

```
```
sudo find / -name onesixtyone
```

if none of those can find it, just install it manually as I advised before

---

### Post by JohnFrank951 on 2013-02-18
##i am posting this in case that someone still have the same issue 

Using backtrack the only thing you have to do in order to run onesixtyone is typing in the terminal:


cd /pentest/enumeration/snmp/onesixtyone
./onesixtyone 


hope this will be useful to someone,
P.S. sorry for my bad english, lack of practice.

---

### Post by oldos2er on 2013-02-18
Old thread closed, please don't bump old threads.

---

