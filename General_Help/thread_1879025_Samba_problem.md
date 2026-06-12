---
title: "Samba problem"
date: 2011-11-10
forum: General Help
---

### Post by crutch145 on 2011-11-10
Since upgrading to 11.10, I can no longer access my samba shares from my Windows 7 laptop.  If I go to my Network to view devices on the network, it doesn't even see my ubuntu computer at all.  Even if I type in \\computername, it doesn't connect.  I have verified that my ufw still has the Samba rule to allow from any location.  

Thanks,

Justin

---

### Post by zcartist on 2011-11-10
Did you check to see if your workgroup names match up? just a thought

---

### Post by capscrew on 2011-11-10
> **crutch145 said:**
> Since upgrading to 11.10, I can no longer access my samba shares from my Windows 7 laptop.  If I go to my Network to view devices on the network, it doesn't even see my ubuntu computer at all.  Even if I type in \\computername, it doesn't connect.  I have verified that my ufw still has the Samba rule to allow from any location.  

Thanks,

Justin
maybe the Ubuntu host doesn't know its own name.  Post the output from Ubuntu of this ```
testparm --parameter-name netbiosname
```

What is the hostname of the Ubuntu machine?  Post he output of ```
cat /etc/hosts
```

---

### Post by crutch145 on 2011-11-10
For the second output, I see that it says terps for 127.0.1.1 instead of sr1810nx (which is the name I changed this computer to around the same time that I upgraded to 11.10).  Could that be the problem?  

justin@sr1810nx:~$ testparm --parameter-name netbiosname
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[PSC-1500-series]"
Processing section "[dv4-1125nr]"
Processing section "[sambashare]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Press enter to see a dump of your service definitions

SR1810NX
justin@sr1810nx:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	terps

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
justin@sr1810nx:~$

---

### Post by capscrew on 2011-11-10
> **crutch145 said:**
> For the second output, I see that it says terps for 127.0.1.1 instead of sr1810nx (which is the name I changed this computer to around the same time that I upgraded to 11.10).  Could that be the problem?  

justin@sr1810nx:~$ testparm --parameter-name netbiosname
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[PSC-1500-series]"
Processing section "[dv4-1125nr]"
Processing section "[sambashare]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Press enter to see a dump of your service definitions

SR1810NX
justin@sr1810nx:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	terps

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
justin@sr1810nx:~$

Where did you change the hostname to terps?  The prompt shows ```
justin@sr1810nx:~$
```

What is the output of this```
hostname
```

And what output do you get with this```
testparm --parameter-name nameresolveorder
```

---

### Post by blueridgedog on 2011-11-10
What happens when you try \\IPADDRESS from the windows side?

(where IPADDRESS is the ip address of the Linux system)

---

### Post by crutch145 on 2011-11-10
I see the hostname is sr1810nx, but I what I am wondering is why it still says terps next to the 127.0.1.1?  That used to be my old hostname, before I changed it to sr1810nx.  The outputs for your two requests are below.  Thanks!

justin@sr1810nx:~$ hostname
sr1810nx
justin@sr1810nx:~$ testparm --parameter-name nameresolveorder
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[PSC-1500-series]"
Processing section "[dv4-1125nr]"
Processing section "[sambashare]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Press enter to see a dump of your service definitions

---

### Post by capscrew on 2011-11-10
> **crutch145 said:**
> ...
Press enter to see a dump of your service definitions

I need the part AFTER you press enter.  If you did press enter and got nothing this can be part of the problem.

Edit: Mine looks like this:```
lmhosts wins host bcast
```

---

### Post by crutch145 on 2011-11-10
lmhosts wins host bcast

---

### Post by capscrew on 2011-11-10
Lets see the output of smbtreee.  This will be pretty big so let's put it in a file and attach it to the response with this command```
smbtree -d3 >smbtree.txt
```

The file smbtree.txt will be in your home directory.

---

### Post by capscrew on 2011-11-10
Actually you can see it for yourself.  Post the output for this ```
smbtree -d3 | grep Attempting
```

This should show what name(s) Samba is searching for.

---

### Post by blueridgedog on 2011-11-10
The OP is trying to "access my samba shares from my Windows 7 laptop" and the Windows 7 system can't resolve the name of the Linux system or the Linux system is not running a Samba server, or the Linux system has a firewall that is blocking the access.  I would do my trouble shooting from the viewpoint of the Windows system.

---

### Post by capscrew on 2011-11-10
> **blueridgedog said:**
> The OP is trying to "access my samba shares from my Windows 7 laptop" and the Windows 7 system can't resolve the name of the Linux system or the Linux system is not running a Samba server, or the Linux system has a firewall that is blocking the access.  I would do my trouble shooting from the viewpoint of the Windows system.

It is functioning as a server; a Samba server.  The OP said so e.g "I can no longer access my samba shares".

---

### Post by crutch145 on 2011-11-10
I have attached the smbtree.txt file.  Why would Samba be looking for a name?  Isn't the Windows 7 laptop the one doing the searching?

---

### Post by capscrew on 2011-11-11
> **crutch145 said:**
> I have attached the smbtree.txt file.  Why would Samba be looking for a name?  Isn't the Windows 7 laptop the one doing the searching?

If windows is looking for shares on the Ubuntu host then they must be available for the Ubuntu host to view also.  You can attempt the same browse from the Ubuntu command line using the command ***smbtree***.  In essence you are asking the Samba server to display all its shares.  

Here is what my one of my Samba servers shows```
BEACH
	\\MALIBU         		malibu
		\\MALIBU\IPC$           	IPC Service (malibu)
		\\MALIBU\Backup         	Backup Data Share
		\\MALIBU\ISO            	Ubuntu ISO's
		\\MALIBU\Public         	Public Share

```
[LIST]
[*]The workgroup is: BEACH
[*]The NETBIOS NAME is: MALIBU
[*]The shares are: Backup, ISO and Public
[/LIST]
---
Your smbtree shows  very little.  What is shoes are errors from the very beginning. 

What I do see is this:
[LIST]
[*]The IP address of the host is: 192.168.51.56
[*] There is a workgroup: FOUNTAINHEAD
[/LIST]

The system can't find the Local Master Browse list.  In fact it can't determine what host is the Local Master Browser (LMB)

Samba relies (as does Windows) on the LMB to provide the mapping between the IP address and its NETBIOS name.  Samba can convert the hostname (from /etc/hosts) to the NETBIOS name.  Your host does not have a hostname defined for the IP address 192.168.51.56.

To be sure, post the output of ```
ipconfig
```.

How is the IP address configured?  Is it static or dynamic (via DHCP).  
Please provide the output of```
net usershare info --long
```

And attach the /etc/samba/smb.conf file.

---

### Post by crutch145 on 2011-11-11
The ip address is configured via DHCP.  Below are the outputs of the two commands.  I attached the smb.conf in .odt format. 


justin@sr1810nx:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:db:83:45:be  
          inet addr:192.168.51.56  Bcast:192.168.51.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fe83:45be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:230809 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:265945693 (265.9 MB)  TX bytes:19528006 (19.5 MB)
          Interrupt:20 Base address:0xdd00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18544 (18.5 KB)  TX bytes:18544 (18.5 KB)


justin@sr1810nx:~$ net usershare info --long
[sambashare]
path=/home/justin/sambashare
comment=
usershare_acl=Everyone:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/testshare is not a well formed usershare file.
info_fn: Error was Path is not a directory.

---

### Post by capscrew on 2011-11-11
From what I can see it looks like Samba just needs to be configured.

I would add these lines to the [global] section of your smb.conf file (substitute whatever you have decided is the hostname (maybe sr1810nx) ```
netbios name = <hostname>
name resolve order = bcast host
```

This does 2 things.  I provides Samba with a name to IP mapping without the need to configure /etc/hosts when using DHCP to supply an IP address that may not be the same every time.

As you are not using the /etc/hosts file to configure Samba anymore, you may change the entry with "terps" to reflect your current hostname (sr1810nx).


Rebooting the system should now allow you to see the host and its shares.  I would check to see that Samba is running correctly with this command```
pgrep -l mbd
``` This should show 2 **smbd** and 1 **nmbd** processes running.

You have a malformed usershare (var/lib/samba/usershares/testshare is not a well formed usershare file.).  You need to remove it.  In addition you have duplicated a share in the smb.conf file with one as a usershare.  I would remove one or the other.  I think you are better off not having redundant shares.

---

### Post by crutch145 on 2011-11-11
Thanks.  Should those two lines of code have a # sign before them?  Should they be placed at the very end of the global settings section?  Also, I see that there is already a line that says "name resolve order = lmhosts host wins bcast."  Should I just replace the "lmhosts host wins bcast" part w/ "bcast host"?  If so, should the "netbios name = sr1810nx" go on the line before or after that line?  Am I correct to assume that the characters < and > should not be included?  Sorry so many questions, lol... newbie here.  I can't thank you enough for this help.

---

### Post by capscrew on 2011-11-11
> **crutch145 said:**
> Thanks.  

Should those two lines of code have a # sign before them?  
No.  The # sign means to ignore it (it becomes only a comment).> 
Should they be placed at the very end of the global settings section?
The 2 lines can be anywhere in the [global] section.> 
Also, I see that there is already a line that says "name resolve order = lmhosts host wins bcast."  Should I just replace the "lmhosts host wins bcast" part w/ "bcast host"?  If so, should the "netbios name = sr1810nx" go on the line before or after that line?  
You can take the ; from in front of the* name resolve order *line and leave only the *bcast host *parameters.  [COLOR="Red"]**Note: **The order is important.  Make sure bcast is first.[/COLOR].  You can put the *netbios name = sr1810nx* on the next line.> 
Am I correct to assume that the characters < and > should not be included?  Sorry so many questions, lol... newbie here.  I can't thank you enough for this help.
Nope, you don't need the < >.  They we so you didn't take the name literally.  ;-)

---

### Post by crutch145 on 2011-11-12
capscrew - I can't thank you enough for the time you took to help me through this.  Unfortunately this still did not resolve the problem.  I have decided to reinstall Ubuntu anyway, as I would like to make better use of my hard drive partitions (dual boot system).  Thanks again!  The Ubuntu community never ceases to amaze me! 

Justin

---

