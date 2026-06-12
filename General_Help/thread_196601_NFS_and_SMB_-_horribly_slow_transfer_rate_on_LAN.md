---
title: "NFS and SMB - horribly slow transfer rate on LAN"
date: 2006-06-14
forum: General Help
---

### Post by Mr.Auer on 2006-06-14
2 Desktop PCs, linux compatible LAN cards on both, Dapper Drake LTS on both. Ive tried searching for an answer, but they were of no help. Also, this was working well on my boxes when I had Breezy on one and Hoary on the other..Now this problem persists with Windows/Apple - Dapper too, and this also used to work with full speed on Hoary..

At first I thought this was a problem only with Samba: Data moves on 100 mbps LAN at around 400-900 kilos per second, when it should be closer to 10 megabytes..If I move data from Box 1 to Box 2, its slow. When moving from Box 2 to Box 1, speed is a little better for some reason, around 2 megs.

I decided to install NFS too..And surprise, NFS works at around 300-700 kilos also..Very very bad speed. So theres something fishy in both SMB and NFS.

I tried moving stuff across LAN by HTTP protocol, I have dhttp-daemon installed on both boxes, and when using this protocol, speed is around 9 megabytes per second, as it should be. 

Ask for more details as needed..All help very welcome as I really need a well working LAN, and http daemon isnt the answer ;)

---

### Post by calandryll on 2006-06-14
I am also having the same problem with my samba mounts.  Almost exactly as you describe it, I have not tried NFS.  It has been this way ever since I upgraded.  I have also noticed that ssh logins take much longer to respond also since upgrading.

---

### Post by Mr.Auer on 2006-06-15
I forgot to say that both my installs are clean installs from the official release. This same problem also appeared on a laptop (old Thinkpad with a LAN card) after updating to Dapper..It worked perfectly well when it was running Hoary, worked both with my other Linux boxes and win/mac ones. Now its also slow as hell..So what have we here, 3 different machines, all with the same issue? This must be quite common..And it cannot be a hardware issue since http protocol works at full speed..

This is a pretty serious issue, and Ive also heard some other people have this. I thought it would be fixed for the final release, but no luck there. Ill have to see if a bug report has been filed after I get some sleep..

---

### Post by Mr.Auer on 2006-06-15
I filed a bug report of this now. Any info/fixes/additional reports of this same problem would still be greatly appreciated :)

---

### Post by scxtt on 2006-06-15
have you installed "nfs-common"?

> **NFS support files common to client and server**

[indent]Use this package on any machine that does NFS either as client or
server.  Programs included: lockd, statd, showmount, and nfsstat.

Upstream: SourceForge project "nfs", CVS module nfs-utils.[/indent]i used to boot some nfs shares to my main box from my "server" and it was ssslllooowww til i installed a package similar to this - i think it was statd that really resolved the issue ...

---

### Post by Mr.Auer on 2006-06-15
I installed NFS according to this how-to:
[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

The packages I have installed are:
nfs-common 1:1.0.7-3ubuntu2
nfs-kernel-server 1:1.0.7-3ubuntu2
portmap 5-16ubuntu2
libnfsidmap1 0.8-1

Samba ones:

libsmbclient 3.0.22-1ubuntu3
samba 3.0.22-1ubuntu3
samba-common 3.0.22-1ubuntu3
smbclient 3.0.22-1ubuntu3
smbfs 3.0.22-1ubuntu3
Configured the same way it was before when it was working, nothing special done to conf files (afaik)

Just at the moment im lookin at Samba push data to my other box at a great, level 166 kilos/sec...wooowww :o

---

### Post by Mr.Auer on 2006-06-30
Hmm no solution so far. :( hope lives on :)

---

### Post by nix4me on 2006-06-30
what are you using to measure the speed?

nix4me

---

### Post by nix4me on 2006-07-01
I have done some testing and I have to agree that something is amiss with NFS transfer speed.  I am getting 380K with NFS and 10Mb with a TCP download from my own webserver.

Something is indeed wrong.

nix4me

---

### Post by Mr.Auer on 2006-07-01
I checked the speed using GKrellMonitors display, and also with Firestarters info display, and the rate at which the harddrives are reading/writing. Speeds using NFS are around 2-300 kilos, TCP is around 9000 kilos. SMB is the same other way, but when used from box 2 downloading files from box 1, sometimes speed goes up to 2700 kilos. Never more.

I cant find my entry in bug reports anymore? hmm...

---

### Post by nix4me on 2006-07-01
[https://launchpad.net/distros/ubuntu/+bug/49819](https://launchpad.net/distros/ubuntu/+bug/49819)

I have added a comment to that bug report.

nix4me

---

### Post by snowx1000 on 2006-07-01
nix4me.

Could you post the output of "sudo ethtool eth0"(or whichever interface you are using)? 

Thanks

---

### Post by nix4me on 2006-07-01
Here it is:

```
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes
```

nix4me

---

### Post by dcstar on 2006-07-02
I suggest anyone with Samba performance issues does a search for the CIFS vs SMBFS posts.

I don't know what Dapper defaults to, but I'd suggest that experimenting with CIFS would be worth pursuing.

On general network performance, I'd look at the default Ethernet settings the Linux drivers set, like Flow Control/duplex etc., there could be one or two things to tweak that may make a big difference.

---

### Post by puelocesar on 2006-07-02
Try putting this configs on your client's fstab:

10.85.7.4:/home1   /home1   nfs   rw,hard,rsize=8192,wsize=8192,timeo=14,intr 0 0

---

### Post by nix4me on 2006-07-02
Actually I have figured out what my problem was.  I was using my firewall network monitor to try and get the speeds.

If I fire up gnome monitor and do transfers with both samba and nfs, I am getting ~10 Meg transfer rates.  This is the same as my tcp transfer rates.

So, it seems I have no problem at all.

nix4me

---

### Post by Mr.Auer on 2006-07-05
Well..Im NOT getting those speeds :) I will try the pueloescars advice shortly..And tomorrow ill reinstall Samba and wade thru the man pages and see if theres anything configured incorrectly..
Just today i was transferring stuff across LAN...Again, speed when taking files from box 2 on box 1 was 3 megs, but when taking files from box 1 on box 2, speed goes down to 300 kilos. NFS never goes over that.

But ill see, tomorrow ill try reinstalls of both and do some reading..Hopefully i dont have to resort to putting up a FTP server ;) That would do it I bet...

---

### Post by Mr.Auer on 2006-07-06
Hmm..This gets weirder..
Today I installed ssh server on both boxes..tried transfering stuff by ssh on lan..And again, the speed is around 300 kilos! What might be causing this..http seems to be the only protocol working at normal speed, nfs, ssh, smb all work way too slow. I also tried disabling ipv6 on both boxes, no effect.I got no more ideas on what to try, except ill maybe install som other distro on one spare partition in this box and see if the problem persists between distro X and Dapper boxes..Any ideas appreciated! :)

---

### Post by Mr.Auer on 2006-07-08
More fiddling---tried installing SUSE 10 on this older box, but its way too slow to use (Yast is killing me! Its so SLOW! Give me synaptic!)..Im now donwloading Fedora, will install that on this box as second OS and then test transfers on LAN..Ive had Fedora on this box before so I know it works well with this hardware at least.

Had a friend come over too to see if he would come up with some idea about whats messing up the LAN..He didnt :)

Heres my eth info:

Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes


If any OPs read this, please change the topic title to something like "SMB,NFS,SSH work slow across LAN" since it better describes my problem?
I added a comment on the bug report too, since this must be about something that affects all network use..

---

### Post by fimbulvetr on 2006-07-08
What mount options are you using for nfs?

Try these, I get 80Mbps on my lan with them:

```
rw,rsize=32768,wsize=32768,hard,intr,nfsvers=3,tcp,noatime,nodev,async,lock
```

---

### Post by puelocesar on 2006-07-08
> What mount options are you using for nfs?

Try these, I get 80Mbps on my lan with them:

Code:

rw,rsize=32768,wsize=32768,hard,intr,nfsvers=3,tcp,noatime,nodev,async,lock



wow, nice one, I'll try it at our university lab... I'm already using half of these options, and it speed up dramatically nfs performance

---

### Post by eagle101 on 2006-07-09
Was replying to main thread, sorry.

I get 2-3MB/sec @ 100Mb NFS transfers to a FreeBSD server.

---

### Post by Mr.Auer on 2006-07-09
I removed NFS yesterday, will have to reinstall it today or tomorrow and test it with those mount options..Before I simply mounted them with something like "mount -t nfs 10.10.10.20 /media/hd" or so..with no other options..I didnt have them in my fstab. 

At the moment SSH transfers (using scp at terminal or Nautilus) go at about 1 megabyte/second, Samba is slower still. 

Tried to install SUSE and Fedora yesterday, but Fedora crashed during install once and then wouldnt update or connect to repos :) And had probs with SUSE too..And they felt so ... lacking after Ubuntu :P So I will have to test speeds with some live distro yet to see if it makes any difference..Have Damn Small Linux and Slax waiting to do that..Will report back then.

On second thought...Heres my exact machine specs too...
Box 1.
Intel P4 2.6 Ghz
768 MB mem
Asus P4P800-E Deluxe mobo, chipset Intel 865PE, Intel ICH5R
Onboard LAN
NVidia FX 5200 128 MB
plus one additional generic Ethernet card, box says it supports Linux

Box 2.
Intel P4 1.6 Ghz
768 MB mem
ASRock P4VT8+ mobo, chipset VIA PT800, VIA VT8237
Onboard LAN
NVIdia FX 5200 128 MB
and also one additional generic LAN card from Intel, says it supports Linux

Ive also tried switching the network interfaces so Ive tried both onboard and card ethernet on LAN. No difference. At the moment the boxes are connected from ethernet cards with a crossover cable, and the onboard ethernets connect to the internet on both boxes, and both are firewalles, allowing free LAN traffic. The cable modem is connected to a switch, and both boxes also connect to this switch.

---

### Post by Mr.Auer on 2006-07-12
Hehe seems that Ive got it working better now, with nothing more than a little evovled ligh treatment... Now I get speeds of around 5 megs/second with SSH and 3-5 with Samba..What I did to get this improvement is quite laughable after all the trouble ;) - I simply swapped the LAN and Internet cards on both boxes so the cards that used to connect to Net now connects the LAN and vice versa..And now it works..I had previously tried swapping the interfaces on only the other box, now I swapped them on both ones. The speed is now constant and the connection works reliably..Also previously, no netware errors were in dmesg at least..

There must be something in those net cards/their drivers, cant explain it otherwise..They still seem to work ok with my net connection, there are no errors and speed is what it should be on my cable modem..A weird probelm..Lets hope it stays away :p

---

### Post by danbaatar on 2006-09-25
I'm having a really similar problem.  My NFS server is the latest Dapper release NFS and my client is an iMac running os x 10.4.7.  My transfers to the nfs server max out at a little less than 2 mB/s, as measured by the os x system monitor.  Anyone figure out what the problem is?

---

### Post by dcstar on 2006-09-25
> **danbaatar said:**
> I'm having a really similar problem.  My NFS server is the latest Dapper release NFS and my client is an iMac running os x 10.4.7.  My transfers to the nfs server max out at a little less than 2 mB/s, as measured by the os x system monitor.  Anyone figure out what the problem is?
I assume people have their Ethernet flow control settings working ok?

Sometime auto-negotiate can give you connectivity, but with enough packet loss to cripple throughput.

---

### Post by Ramesis on 2006-11-25
Hi I am also getting really slow transfer speeds. I have two Network cards in my computer, on is a 100Mbit card that is on the Motherboard, which is not in use. The second is a Gigabit card which i am using. To copy a 600Meg Iso accross my network is taking about 1.2 hours. This is acually much slower then 100Mbit. Here is the output from EthTool:

Settings for eth1:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000033 (51)
	Link detected: yes

Appreciate any help...

---

### Post by syadnom on 2006-11-25
what are the chances....

did you guys run hdparm on your hard disk?  maybe its a slow hard disk access issue...

just a thought. i run the default setup and i get at least 5 or 6mb/sec with samba to an xp pro or nfs to a osx10.4.8 machine.

---

### Post by Mr.Auer on 2008-01-14
I never did find out what caused this problem..
In Edgy, Feisty and Gutsy my ethernet interfaces have worked with the expected speed.
May have been a driver issue on one of my cards that got fixed in a later kernel..Who knows :)

Wasnt my harddrives either, they worked fine and at normal speed back then. 

"I assume people have their Ethernet flow control settings working ok?

Sometime auto-negotiate can give you connectivity, but with enough packet loss to cripple throughput."

That may be...

---

### Post by larytet on 2008-01-19
confirmed in Ubuntu 7.10 - the Gutsy Gibbon - released in October 2007

NFS fails to utilize the link (54Mbits/s WiFi in my case), while FTP/SFTP work fine.

---

### Post by larytet on 2008-01-19
i found this 
[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#PERFORMANCE](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#PERFORMANCE)

---

### Post by moonlightcheese on 2008-02-15
[http://www.hep.ucl.ac.uk/~ytl/tcpip/linux/txqueuelen/datatag-tcp/](http://www.hep.ucl.ac.uk/~ytl/tcpip/linux/txqueuelen/datatag-tcp/)

---

