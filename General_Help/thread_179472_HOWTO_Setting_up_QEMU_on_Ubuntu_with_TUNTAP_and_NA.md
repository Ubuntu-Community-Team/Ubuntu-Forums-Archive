---
title: "HOWTO: Setting up QEMU on Ubuntu with TUN/TAP and NAT"
date: 2006-05-19
forum: General Help
---

### Post by fateinabox on 2006-05-19
**Step By Step Howto Qemu on Breezy Badger**

[COLOR="Red"]**note: KQEMU is the QEMU Accelorator*[/COLOR]
REMEMBER: If it's not covered here RTFM....

Step 1) Compile and setup of Qemu and KQemu
Step 2) Installation of GuestOS [ Windows 98se in this example ]
Step 3) Setup of Tun/Tap network interface on host and guest OS.
Step 4) NAT setup to allow guestOS access to the internet.

Brief Description:
	QEMU is an Open-Source Emulator that emulates x86 arch as well as several others.... allowing for guestOS's to be installed inside the host OS.
	QEMU is available for Linux, Mac, and Windows. We'll be covering the Linux Package in this HowTo.
	For more information on QEMU visit the projectpage @ [http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)

What you'll need:
+	QEMU source tarball from [http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)
+	KQEMU binary tarball from [http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)
+	linux-headers package
+	IPTables ( should already be installed ) package
+	libsdl1.2-dev package
+	Tun/Tap package
+	uml-utilities package
+	windows98 install cd and valid windows98 serial.
+	GCC-3.4 package

Ok, so this is the first HowTo i've wrote in quite a long time. First for ubuntu, and Qemu..


################################################################
[ Step 1 ] - Compilation and Installation of KQEMU and QEMU

 	Outlined here is the steps taken to compile and setup Qemu and Kernel Module KQemu
	
	A) Download the latest source tarball of QEMU from [http://fabrice.bellard.free.fr/qemu/download.html](http://fabrice.bellard.free.fr/qemu/download.html) current version is 0.8.1
	B) Download the latest binary of KQEMU from [http://fabrice.bellard.free.fr/qemu/qemu-accel.html](http://fabrice.bellard.free.fr/qemu/qemu-accel.html)
	
	C) Move the tarballs to your /usr/local/src directory and deflate
			#> sudo mv qemu-version.tar.gz /usr/local/src/
			#> sudo mv kqemu-version.tar.gz /usr/local/src/
		
		deflate...
			#> sudo gunzip qemu-version.tar.gz; sudo tar -xvf qemu-version.tar
			#> sudo gunzip kqemu-version.tar.gz; sudo tar -xvf kqemu-version.tar
	
	D) Install linux-headers for your current kernel version.
	     If you don't know your current kernel version you can do `uname -r` at the shell to find out...
	     
		#> sudo apt-get install linux-headers-`uname -r`

	E) Install GCC-3.4 [ qemu complains on GCC-4 ] and libsdl1.2-dev
		
			#> sudo apt-get install gcc-3.4 libsdl1.2-dev
		
		locate the installed gcc-3.4 binary using whereis
			#> whereis gcc-3.4
		
		it should be located in /usr/bin/ if not found at all installation failed. repeat step E.
		make a note of it's location. you're going to need it in step F

	F) Configure and Compile QEMU and KQEMU
		
		change directories to your qemu-source you deflated in step C
			#> cd /usr/local/src/qemu-version
			#> sudo ./configure --cc=/usr/bin/gcc-3.4 [ remember the location of it from step E? ]
		
		once configuration is completed run make and make install to compile and install... do so as follows

			#> sudo make
			#> sudo make install
		
		verify that QEMU installed correctly...
			#> whereis qemu	

		change directories to your kqemu-source you deflated in step C, and configure make and make install
	
			#> cd /usr/local/src/kqemu-version
			#> sudo ./configure
			#> sudo make
			#> sudo make install
		
		verify that device node /dev/kqemu exists
		if not...execute following commands
		
			#> sudo mknod /dev/kqemu c 250 0
			#> sudo chmod 666 /dev/kqemu

		Active module KQEMU
			#> sudo modprobe kqemu
		Verify that it loaded properly
			#> lsmod | grep kqemu
		If it failed to show up. issue a dmesg | tail to see what the error was
			#> dmesg | tail
		Anyway... continuing...

[ Step 1 Completed ]
##################################################################


[ Step 2 ] Installing Guest OS
	[COLOR="Red"][I]*notes: 		you can use either the actual install CD or an ISO made from the original install disk, I used an iso.
		     		you can also use the dd command with the seek option to create your hard disk image file, in place of qemu-img create	
		     		for convenience we're going to use the qemu-img binary installed with QEMU[/I][/COLOR]

	*help:		Run qemu/qemu-img without any arguements to view it's help 

	A) Create the Hard Drive Image File to use as HDA
		choose the directory you wish to store your disk images you can use mkdir to create a new one. I use ~/qemu
			#> cd ~/qemu
		A brief rundown of what we're executing here....
		qemu-img create [filename] [-f format( raw, vvfat, cloop,... )] [size G(gigs), M(megs) ]
			#> qemu-img create win98.img -f raw 2G
		Ok, we've created the 2G image file to install windows98se into....now we load QEMU to boot from the cdrom/iso file specified to start installation
	
			#> qemu -hda win98.img -cdrom /dev/cdrom -boot d -localtime -net nic -net tap 
		Now QEMU should boot from CD, just follow the steps to complete the installation...

		Once installation has completed now we can move onto Step 3
[ Step 2 Complete ]
##################################################################

[ Step 3 ] Setting up TUN/TAP network interface on HostOS and GuestOS

	A) Install uml-utilities via apt
		#> sudo apt-get install uml-utilities
	B) Load kernel module tun
		#> sudo modprobe tun66.202.65.50
	C) Create the /dev/net/tun device node
		#> mkdir /dev/net
 		#> mknod /dev/net/tun c 10 200
	D) Setup the tap0 interface, with an ip address i use 192.168.100.1 for this.
		Create the tap0 interface using tunctl
		#> sudo tunctl
		 
		Give it an IP-Address
		#> sudo ifconfig tap0 192.168.100.1 up
		Make sure it was configured properly...
		#> ifconfig

		You should see tap0 with an inet addr: 192.168.100.1 and a Mask: 255.255.255.0
		If there is no mask set...sometimes this happens don't know why but it's happend....do this
		#> sudo ifconfig tap0 192.168.100.1 netmask 255.255.255.0 up
		

		Ok, we're done with the HOST side of this

	E) Setting up the GuestOS's network configuration
		
		If you don't have QEMU booted into windows already then do so by this command...
			#> qemu -hda win98.img -boot c -net nic -net tap &
		
		Once windows has loaded goto your Control panel and open Network Settings
		At the configuration tab Select TCP/IP and click properties

		In the Properties window
		- Select the IP Address Tab
			select specify an IP address
			enter 192.168.100.2 as your ip address
			enter 255.255.255.0 as your subnet mask
		- Select the Gateway Tab
			add a new gateway as 192.168.100.1
		- Select Ok
		Select Ok
		Now you will be promted for a restart....restart and you should be able to ping the guestOS from the hostOS

	F) Testing the network connection
		from a terminal
		#> ping 192.168.100.2 -c 4
		You should reach 192.168.100.2 if not, verify you followed every step.
		
		Make sure you can Ping the Host from the guest

		on Windows from a dosprmpt
		#> ping 192.168.100.1 -n 4
		You should reach 192.168.100.1 if not, verify you followed every step correctly.

[ Step 3 Complete ]
#################################################################

[ Step 4 Setting up NAT to allow GuestOS access to the internet ]
	[COLOR="Red"]**note:	i'm going to go ahead and assume you have iptables already installed.*[/COLOR]

	A) Load Required Kernel Modules
		#> sudo modprobe ip_tables
		#> sudo modprobe iptable_nat
		#> sudo modprobe ip_nat_ftp
		#> sudo modprobe ip_nat_irc

	B) Enable IP-Forwarding
		as root run
		#> echo "1" > /proc/sys/net/ipv4/ip_forward
		
		If you get your IP Address Dynamically e.g. PPP0 (Dial-up)
		as root run
		#> echo "1" > /proc/sys/net/ipv4/ip_dynaddr

		Enable SNAT (MASQUERADE) functionality on eth0/ppp0
		*note: replace eth0 with ppp0 for dialup

		#> sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
		
	C) Setup DNS on guestOS
		[COLOR="Red"]**note: this is for windows98se, methods aren't listed for other OS's*[/COLOR]
		
		You can retrieve your DNS Server Ip's from your /etc/resolv.conf file after connected to the internet.

			#> sudo cat /etc/resolv.conf
			
		In windows, goto control panel -> networking -> TCP/IP Properties -> DNS Configuration
		Select Enable DNS 
		
		Set Host to your gateway address, i set mine to 192.168.100.1 for my gateway
		Set Domain to your Domain i just set it to one of the DNS servers IP Address's
		Add your ISP DNS Servers to the DNS List..

		Ok, reboot! everything should work fine now..
[ Step 4 Complete ]

After following these steps you should have a working Qemu using the KQEMU accelerator as well as Tun/Tap Virtual Network forwarding Requests from the guest to the internet.
	If something isn't working, double check to make sure you set it up correctly.

---

### Post by DannyW on 2007-04-15
I'm using feisty and I'm trying to set the networking part up on qemu with windows xp professional.

Went through it all (dev/net/tun already existed).

When I ran qemu-system-x86_64 with -net nic -net tap it created another tap on ubuntu, so I had tap0 and tap1:

```
tap0      Link encap:Ethernet  HWaddr 52:02:E2:5F:0E:D4  
          inet addr:192.168.100.1  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::5002:e2ff:fe5f:ed4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:54 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tap1      Link encap:Ethernet  HWaddr 4E:CF:2C:40:4E:FD  
          inet addr:172.20.0.1  Bcast:172.20.255.255  Mask:255.255.0.0
          inet6 addr: fe80::4ccf:2cff:fe40:4efd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:9333 (9.1 KiB)  TX bytes:10519 (10.2 KiB)
```

And so I deleted tap1 and this time ran it with -net nic -net tap,fd=tap0 - This uses my existing tap0.

```
danny@danny-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:C6:3A:44  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fec6:3a44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2334882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2140338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1590355393 (1.4 GiB)  TX bytes:778558874 (742.4 MiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:344954 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:128752549 (122.7 MiB)  TX bytes:128752549 (122.7 MiB)

tap0      Link encap:Ethernet  HWaddr 52:02:E2:5F:0E:D4  
          inet addr:192.168.100.1  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::5002:e2ff:fe5f:ed4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:64 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

danny@danny-desktop:~$ ping 192.168.100.2 -c 4
PING 192.168.100.2 (192.168.100.2) 56(84) bytes of data.
From 192.168.100.1 icmp_seq=2 Destination Host Unreachable
From 192.168.100.1 icmp_seq=3 Destination Host Unreachable
From 192.168.100.1 icmp_seq=4 Destination Host Unreachable

```

I have set the settings as follows in windows xp (guest os).

```
Ethernet adapter Local Area Connection:
Connection-specific DNS Suffix:
IP Address: 192.168.100.2
Subnet Mark: 255.255.255.0
Default Gateway 192.168.100.1
```

Yet I cannot ping 192.168.100.1 from WinXP or ping 192.168.100.2 from Ubuntu.

Heres the command I'm using to start qemu:
sudo qemu-system-x86_64 -m 1024 -hda /home/danny/winxp.img -boot c -net nic -net tap,fd=tap0 &

I'm getting a lot of garbage scrolling down my terminal I opened qemu from. A snippet of this is:

```
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;RT4E`4&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;d&#65533;&#65533;&#65533;Li&#65533;&#65533;) ABACFPFPENFDECFCEPFHFDEFFPFPACAB &#65533;
                                                                         &#65533;&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;RT4E`5&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;d&#65533;&#65533;&#65533;Li&#65533;&#65533;) ABACFPFPENFDECFCEPFHFDEFFPFPACAB &#65533;
                                                                           &#65533;&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;RT4E`6&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;d&#65533;&#65533;&#65533;Li&#65533;&#65533;) ABACFPFPENFDECFCEPFHFDEFFPFPACAB &#65533;
                                                                              &#65533;&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;RT4E`7&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;d&#65533;&#65533;&#65533;Lj&#65533;&#65533;( ABACFPFPENFDECFCEPFHFDEFFPFPACAB &#65533;
 &#65533;&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;RT4E&#65533;8&#65533;&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;d&#65533;&#65533;&#65533;&#65533;l&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533; EEEBEOEOFJCNFBEFENFFCACACACAV\MAILSLOT\BROWSEDANNY-QEMU&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;RT4E&#65533;9&#65533;&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;d&#65533;&#65533;&#65533;&#65533;8&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533; EEEBEOV\MAILSLOT\BROWSEDANNY-QEMU&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;RT4E&#65533;:&#65533;&#65533;q&#65533;&#65533;d&#65533;&#65533;d&#65533;&#65533;&#65533;&#65533;Hi&#65533;&#65533;&#65533;d&#65533;&#65533; EEEBEOEOFJCNFBEFENFFCACACACACAAA ABACFPFPENFDECFCEPFHFDEFFPFPACAB&#65533;SMB%+&#65533;+V<\MAILSLOT\BROWSE
           `&#65533;WORKGROUP  Ð
  € ÐøDANNY-QEMU ÿÿÿÿÿÿRT 4   RT 4VÀ¨&#9229;      À¨&#9229;                  ÿÿÿÿÿÿRT 4 E  å ?  €ï&#9524;À¨&#9229;À¨&#9229;ÿ Š Š Ñ£€À¨&#9229; Š »   EEEBEOEOFJCNFBEFENFFCACACACACACA  FHEPFCELEHFCEPFFFACACACACACACABO ÿSMB%                             !  è        ! V      2 \MAILSLOT\BROWSE &#65533;&#65533;DANNY-QEMUU&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;RT4RT4V&#65533;&#65533;d&#65533;&#65533;d                  &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;RT4E&#65533;A&#65533;&#65533;j&#65533;&#65533;d&#65533;&#65533;d&#65533;&#65533;&#65533;&#65533;J&#65533;&#65533;&#65533;d&#65533;&#65533; EEEBEOEOFJCNFBEFENFFCACACACACAAA ABACFPFPENFD
```
etc etc..

Any ideas?

Thanks,
Danny.

---

### Post by DannyW on 2007-04-16
Update: Removing tap0 (sudo tunctl -d tap0) and letting qemu create it (-net nic -net tap), remembering then to change the TCP/IP settings on the guest OS (using info from ifconfig), seems to fix this problem.

---

### Post by fateinabox on 2007-04-16
glad you got it working, it's been over a year since i posted this TUT, and i'm sure alot of things have changed in the relationship between Qemu and Ubuntu, the version of Qemu i used and the Ubuntu Release i had used added some difficulties to the mix, Qemu wouldnt' automatically create the Tap interface and the tun/tap packages weren't installed by default, if those packages are installed with the current releases of ubuntu then the steps to install the tun package and setup a tap interface could be skipped as you did to solve the problem. Thanks for the reply and letting me know of the difference, so that future readers will know as well. -- Catch you on the flipside.

---

### Post by SeanLiebhard on 2007-04-23
I am installing XP media center under feisty.  After configuring tap0 and trying to boot the image I get the error:

```
[1] 6401
warning: could not configure /dev/net/tun: no virtual network emulation
Could not initialize device 'tap'

```

I've double checked all of my steps and I can't seem to find the issue.

Any suggestions?

---

### Post by amiga_os on 2007-04-30
+1 for that problem in Feisty... Installing XP was fine, but networking has been impossible to set up, I've read everything on this, but nothing seems to have worked... and it's all well to complicated.  Anyone got a simple Feisty/QEMU networking howto?

---

### Post by brian_chat on 2007-05-02
> **SeanLiebhard said:**
> I am installing XP media center under feisty.  After configuring tap0 and trying to boot the image I get the error:

```
[1] 6401
warning: could not configure /dev/net/tun: no virtual network emulation
Could not initialize device 'tap'

```

I've double checked all of my steps and I can't seem to find the issue.

Any suggestions?

> **amiga_os said:**
> +1 for that problem in Feisty... Installing XP was fine, but networking has been impossible to set up, I've read everything on this, but nothing seems to have worked... and it's all well to complicated.  Anyone got a simple Feisty/QEMU networking howto?

You need to run qemu as root for tap network access to work
```

sudo qemu -hda win98.img -boot c -net nic -net tap 

```

---

### Post by RyanBrooks on 2007-05-08
It's a bit of a poor show running QEMU/KVM as root, just to be able to have network access. I'm looking at the problem now - there's got to be a clean way to fix it.

---

### Post by 13u11fr09 on 2007-05-11
**EDIT:**  In order not to confuse people anymore than I might already have, please ignore this post and see the write up linked to in the post below this...

> **RyanBrooks said:**
> It's a bit of a poor show running QEMU/KVM as root, just to be able to have network access. I'm looking at the problem now - there's got to be a clean way to fix it.

Here's a bit of a convoluted work around, although you won't be running qemu as root for net access...

I believe the problem with needing root for net access in qemu comes from the /dev/net/tun device not being accessible to the user.  One solution is to put the following in a script that calls qemu:

```

USERID=`whoami`

sudo chown root:$USERID /dev/net/tun
sudo chmod g+rw /dev/net/tun

```

I used the setup found in this thread and [here]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo") and use this (hacked together) script to run qemu:

```

# Starts up QEmu with various options

# Variables
set -o errexit
SOUND="-soundhw es1370"
MEMORY="-m 256"
TIME="-localtime"
IMGPATH="/mnt/data/virtual/xp"
IMG="$IMGPATH/xp.img"
USERID=`whoami`

# need to make sure we have read/write access to the  device at /dev/net/tun
echo "Using sudo too to setup /dev/net/tun..."
sudo chown root:$USERID /dev/net/tun
sudo chmod g+rw /dev/net/tun                                                    
# now be sure that IP forwarding and masquerading are good to go
echo "Need root password to setup IP forwarding..."
su -c "echo '1' > /proc/sys/net/ipv4/ip_forward"
echo "Done being root..."
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

# Create tap interface so that the script /etc/qemu-ifup can bridge it
# before qemu starts
echo "Using sudo to setup the tap interface..."
IFACE=`sudo tunctl -b -u $USERID`

NET="-net nic,vlan=0 -net tap,vlan=0,ifname=$IFACE,script=/etc/qemu-ifup"

# QEmu start
qemu ${SOUND} ${TIME} ${MEMORY} ${IMG} ${NET}

# QEmu has stopped - no longer using tap interface
sudo tunctl -d $IFACE &> /dev/null 

# user no longer needs read/write on /dev/net/tun
sudo chown root:root /dev/net/tun


```

You do need the root password for this script to setup ip_forwarding... 

I hope this helps...

---

### Post by daigidan on 2007-05-22
A few pointers for those struggling to get this working.

The wiki has more [up-to-date instructions on building QEMU ]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")using module-assistant.

To get TAP working I highly recommend [Dan Walrond's write-up]("http://compsoc.dur.ac.uk/~djw/qemu.html").The instructions are for Debian, but work just fine for Ubuntu. The problem mentioned above about requiring root access is handled in this document by setting up a new sudo access.

Hope that helps somewhat. Cheers!

---

### Post by bensexson on 2007-06-07
I've been trying to get this to work with the instructions here: [http://compsoc.dur.ac.uk/~djw/qemu.html](http://compsoc.dur.ac.uk/~djw/qemu.html)
I have been unable to get them to work.  I remove the IP from my interface and create the tap interface and create the bridge and add both of them to the bridge and the get a dhcp IP from my router.  Then I start QEMU with tap.  I am able to ping the IP on the bridge of the host from the guest but am unable toping the guest from the host.  The guest is unable to ping anything else.  Any one else have success?

---

### Post by ruibernardo on 2007-09-21
> **daigidan said:**
> A few pointers for those struggling to get this working.

The wiki has more [up-to-date instructions on building QEMU ]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")using module-assistant.

To get TAP working I highly recommend [Dan Walrond's write-up]("http://compsoc.dur.ac.uk/%7Edjw/qemu.html").The instructions are for Debian, but work just fine for Ubuntu. The problem mentioned above about requiring root access is handled in this document by setting up a new sudo access.

Hope that helps somewhat. Cheers!

Thanks daigidan! They surely helped me. Setting the bridge was a pain on Feisty, but with those clear instructions, it worked perfectly.

---

### Post by ruibernardo on 2007-09-23
Although [Dan Walrond's write-up]("http://compsoc.dur.ac.uk/%7Edjw/qemu.html") did work on a computer connected to a router, it didn't on a computer connected to a modem. I've search a bit more for an alternative to a real bridge and found two links of interest:

[http://alien.slackbook.org/dokuwiki/doku.php?id=slackware:vde](http://alien.slackbook.org/dokuwiki/doku.php?id=slackware:vde)
[KVM - Avanced networking]("https://help.ubuntu.com/community/KVM#head-db5235851cc1b9c712f99a074f02c91e8590c880-2") (the section about VDE) 

This makes an equivalent to the vmnet8 (NAT) interface on vmware and NAT interface on VirtualBox. The QEMU VM have access to the internet, but aren't accessible from it. I've updated the page [up-to-date instructions on building QEMU]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo") to include this (the "VDE and DNSmasq" section).

To make a QEMU VM accessible from the Internet (a virtual server) with VDE network and dnsmasq, just use iptables. With Firehol I did something like this (firehol.conf):

```
modem_interface_ip=`ifconfig | grep -A 1 eth0 | grep "inet addr:" | cut -d ':' -f 2 | cut -d ' ' -f 1`
[B]
nat to-destination 10.111.111.215 proto tcp dport 80 dst $modem_interface_ip[/B]

interface eth0 internet src not "${UNROUTABLE_IPS}"
      protection strong
      server ident reject with tcp-reset
      client accept all

interface qtap0 home
      policy accept

route myrouter inface eth0 outface qtap0
      masquerade reverse
      client all accept

      **route http accept**

```**qemu-launcher** doesn't work with VDE without some tweaking. To make qemu-launcher work with all this, do the following:[INDENT]* Go to the "Launcher settings" tab and replace "/usr/bin/qemu" with "/usr/bin/vdeqemu" and click "Apply/Save";

* Click on the "Configuration" tab, then on the "Network" tab. Put 0 (zero) on "Number of network interface cards:". You will define the network on the "Additional arguments:" later. This is necessary because if you don't, qemu-launcher will paste "-net nic,vlan=0" apart from the "-net vde ..." options, separated with some other options you might choose, and networking might/will not work. Although qemu-launcher will paste "-net none", it will paste the network options in the end of the line (additional arguments) and work :);

* Click on the "Emulator" tab and on "Additional arguments", add the VDE network arguments: ```
-net vde,sock=/var/run/vde.ctl,vlan=0 -net nic,vlan=0
```* cdrom, disk and all others options are used as usual.[/INDENT]In case that some VM doesn't start, try running qemu-launcher from a terminal to verify the error or try running vdeqemu yourself:

```
vdeqemu -net vde,sock=/var/run/vde.ctl,vlan=0 -net nic,vlan=0 -localtime -m 160 -boot c ubuntu-server.img
```And that's it. No more VMware and/or VirtualBox, only completely free and GNU software.:popcorn:

---

### Post by fateinabox on 2008-03-26
It's amazing to see that this little TUT i wrote 2 years ago has grown as much as it has, I apologize to those who had problems with this Setup but congratulations to everyone who managed to get it working and contributed to the topic.

---

### Post by zeezam on 2008-07-24
Just wondering if vnet0 is the network I should change for my guestOS?
Have installed virt-manager and kvm with libvirt and running winxp as guest os but having problem with the network.

---

