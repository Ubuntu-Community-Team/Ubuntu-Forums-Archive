---
title: "I might as well go back to windows! A little help please! A system gone wrong!"
date: 2010-03-11
forum: General Help
---

### Post by Elludium_Q-36 on 2010-03-11
It's really sad when I think I'd be better off with a windows box.
I've had good ubuntu boxes before but things happen.

I bought this box from an electronics reclaimer with 8.04 installed from their download.
It's been pretty wonky/screwy and the CPU is often at 100% from some mystery process.
System Monitor shows the 100% CPU usage but does not list processes that total 100%
I've seen an unknown/un-named process from user "root -1" but it's usually there very briefly and CPU usage is listed as "Unknown".

I've tried to implement das_watchdog

```
kubuntu@kubuntu:~$ test_rt

das_watchdog: Unable to set SCHED_FIFO realtime priority for the watchdog thread. Exiting.

kubuntu@kubuntu:~$ das_watchdog -h

Usage: das_watchdog [--force] [--verbose] [--checkirq] [--increasetime n] [--checktime n] [--waittime n]

[ -f] [ -v] [ -c] [ -it n] [ -ct n] [ -wt n]

Additional arguments:

[--version] or [-ve] -> Prints out version.

[--test] or [-te] -> Run a test to see if xmessage is working.

kubuntu@kubuntu:~$ das_watchdog --test

Das_Watchdog:

Warning. The priority of the "ksoftirqd/0" process is only 0, and not 99. Unless you are using the High Res Timer,

the watchdog will probably not work. If you are using the High Res Timer, please continue doing so and ignore this message.

Das_Watchdog:

Warning The "ksoftirqd/0" process is running SCHED_OTHER. Unless you are using the High Res Timer,

the watchdog will probably not work, and the timing on your machine is probably horrible.

Das_Watchdog: Warning, you are not running as root. das_watchdog should be run as an init-script at startup, and not as a normal user.

Das_Watchdog: Unable to set SCHED_FIFO realtime priority for 0 ("Das Gewinde nach der Uhr Hund"). (Operation not permitted). Exiting.

kubuntu@kubuntu:~$ das_watchdog --version

Das Version der Uhr Hund 0.3.1 nach sein bist.
```

Plenty of apps crash for no reason, opera, firefox & other mozilla gecko browsers, kompozer.
App installation scripts don't add to the menu and the menu editor often won't save but sure will delete!

I'm sure I have malicious or bad code, why else would ports 1524, 6667 & 31337 be active?

I have attached the results of chkrootkit as chkroot.txt

I ran rkhunter and attached the results as rkhunter_run.txt

If helpful, I can attach the output to /var/log/rkhunter.log but must break it up to attach to this forum

I figured my package state might be helpful: package_state.odt

Some have suggested that graphics can be an issue.
I've read that X.org and KDE can be resource hungry but it shouldn't bee this bad.  My motherboard has the slot for an agp card

From other posted info, I ran lspci:
```

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge

00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

```

And also, lshw -C Display
```


WARNING: you should run this program as super-user.
  *-display UNCLAIMED
       description: VGA compatible controller
       product: KM400/KN400/P4M800 [S3 UniChrome]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 mingnt=2

```

I pulled system info from hardinfo and converted the .html report to text, attached as hardinfo_report.txt:

I have already attached the maximum 5 files per post but have the results of guarddog_config_test.txt and I ran netstat -a but am reluctant to post the full output online if there are vulnerabilities :-|  Would you give out your IP address and firewall configuration if you knew your system was vunerable?

Often a sign of trouble is to hear the hard drive grinding away.  Either that or the gui hangs...

Some say firefox it often the culprit but Opera seems not much better.  I generally block javascript with noscript, have redirect remover, ghostery, greasemonkey, greasefire...

I could have been prompted to run malicious code from the forums.
A corrupted package is more likely.  I now have gtkhash to check files if the checksums are posted.

I would have thrown out the baby with the bathwater and recompied Kubuntu/Ubuntu but I have a VERY slow iDEN modem connection over KPPP and see 2kb/sec often. I should back-up all data and the /home/ directory as I may have to bite the bullet and reinstall, unless someone can help.

Thanks for reading.

---

### Post by mikewhatever on 2010-03-11
Let's see, used hardware, programs malfunctioning, suspected malware, gui freezes. What kind of help are you looking for? Why not just reinstall? I mean, you'll probably be up in an hour, all updated and favorite programs installed.

---

### Post by jamesbarnhill on 2010-03-11
> **mikewhatever said:**
> Let's see, used hardware, programs malfunctioning, suspected malware, gui freezes. What kind of help are you looking for? Why not just reinstall? I mean, you'll probably be up in an hour, all updated and favorite programs installed.
Same here, if it's going that bad just re-install, ;) Anything is better than windows.

---

### Post by Elludium_Q-36 on 2010-03-11
I guess your eyes glazed over on the part about the iDEN modem which generally has speeds of 2kb/sec.  That's a Motorola iDEN cell phone, tethered.  Theoretically it can do 25 K, if I recall correctly but never does.  What was that commercial with the tag-line, "Not going anywhere for a while?"

I downloaded the updates from 8.04 to 9.04 and the roughly 1.5G took about a WEEK to download.

Assuming I find the CD provided AND assuming the checksum checks out, Ubuntu needs to download packages.  Then there are the ones I added...  I've been told that putting an old /home/ dir where associated packages not installed is not a good idea.

If I were a Yuppie with wads of cash, I might have been on a Mac and not even heard of Ubuntu.

---

### Post by oldsoundguy on 2010-03-11
Another vote for a re-install.  Since there is nothing important on the computer at present, nothing will be lost.(if you have not done any work on the box, even saving the ~/home is not needed.)

And using a cell phone for internet is a total exercise in futility.  They are sometimes even slower than dial up unless your are 3G-4G and even then 4gb is still SLOW compared to even slow DSL.

---

### Post by cdenley on 2010-03-11
Regardless of OS, you should never trust the software on a used computer. You're sure to get a physical copy of ubuntu much cheaper than a copy of windows.
[http://shop.canonical.com/index.php?cPath=17](http://shop.canonical.com/index.php?cPath=17)
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)
[http://www.amazon.com/Introduction-video-DVD-Training-Reference-commands/dp/B0018KUB6Y/ref=sr_1_1?ie=UTF8&s=software&qid=1268332157&sr=1-1](http://www.amazon.com/Introduction-video-DVD-Training-Reference-commands/dp/B0018KUB6Y/ref=sr_1_1?ie=UTF8&s=software&qid=1268332157&sr=1-1)

By ports 1524, 6667, and 31337 being "active", do you mean there is a process listening on those TCP ports?
```

sudo netstat -tlnp

```

For identifying any process that is hogging the CPU:
```

top -n 1

```

If you're experiencing random crashes, you might want to ensure the hardware is working properly.

---

### Post by Elludium_Q-36 on 2010-03-11
I've had this box for a couple years and there's data, which should fit on a flash drive.  There's my time configuring everything and of course the time to re-download packages, albiet from a better advised list.

I've been putting up with this for a while.  But it's frustrating when, at random, I can't use my system for no apparent reason.  I thought the bot-nets concentrated on Windows.

I certainly know how slow my connection happens to be.  Forget Youtube...
Forget anything with flash.  The problem is that it's often not the data connection which causes a delay but ordinary processes on the box.  Seems some would advise buying a winning lottery ticket.  Then I could get satellite service or private terrestrial microwave link/feed, long range WiFi or a private 4G connection in the unlicensed spectrum.

I wouldn't have needed to post for the votes.  I thought someone might pick out an answer from the files I attached in the Original Post or ask for more info.

I have seen other people post, looking for help and they are either unwilling or unable to post any info.  I think I've provided a good amount.

I would appreciate any helpful advice.  I can GO to an internet cafe' and use a public computer, carrying back files on a flash-drive.  Hopefully I wouldn't bring back anything nasty from their wide-open windows box.  I've tried to generate a package download script from synaptic and found what seemed like simple instructions to make the script work on a garden variety windows box but it did not work.  I'd still have to be able to find the hash/checksums...

Some helpful commands, remove/install this or that package, run a command (not malicious :o/ ), a little advice on how to save and replace my data & settings files if I have to take the install "out back" like "Old Yeller" (a 1957 Walt Disney classic film).

I realize that Ubuntu has paid full support but so does Windows...

*****

Thank you Cdenley!

I've looked at top before and it seems to give a snapshot while System Monitor seems "realtime", yet there are hidden processes.  I have tried ```
unhide
``` before, with a flag/switch, but didn't find anything.

Here is the results from top:
```

kubuntu@kubuntu:~$ top -n 1                                                                                                                                
top - 13:50:17 up 3 days, 16:43,  1 user,  load average: 0.68, 0.42, 0.27
Tasks: 212 total,   1 running, 211 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.1%us,  3.4%sy, 20.6%ni, 58.4%id,  8.4%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:    703232k total,   688748k used,    14484k free,     5684k buffers
Swap:  2129912k total,   594008k used,  1535904k free,    82696k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6492 kubuntu   24   4  154m 9.8m 6540 S  1.9  1.4  18:17.39 ksysguard
13179 kubuntu   20   0  2572 1148  828 R  1.9  0.2   0:00.02 top
    1 root      20   0  3084  516  468 S  0.0  0.1   0:01.32 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.05 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S  0.0  0.0   0:14.78 ksoftirqd/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    6 root      15  -5     0    0    0 S  0.0  0.0   0:05.08 events/0
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0
   10 root      15  -5     0    0    0 S  0.0  0.0   0:11.18 kblockd/0
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.97 kacpid
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue
   14 root      15  -5     0    0    0 S  0.0  0.0   0:26.19 ata/0
   15 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux
   16 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd
   17 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
   18 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
   19 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd
   20 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn
   21 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn
   24 root      15  -5     0    0    0 S  0.0  0.0   1:59.55 kswapd0
   25 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
   26 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea
   29 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
   30 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
   31 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2
   32 root      15  -5     0    0    0 S  0.0  0.0   1:04.27 scsi_eh_3
   33 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kstriped
   34 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmpathd/0
   35 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmpath_handlerd
   36 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksnapd
   37 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0
   38 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd
kubuntu@kubuntu:~$

```

Thank you for that netstat flag/switch!
```

kubuntu@kubuntu:~$ sudo netstat -tnlp                                                                
[sudo] password for kubuntu:                                                                         
Active Internet connections (only servers)                                                           
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name     
tcp        0      0 0.0.0.0:1               0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:20034           0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:32771           0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:2659            0.0.0.0:*               LISTEN      5058/rpc.mountd
tcp        0      0 0.0.0.0:32772           0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:40421           0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:32773           0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:32774           0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:31337           0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:5481            0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:5929            0.0.0.0:*               LISTEN      3185/rpc.statd
tcp        0      0 127.0.0.1:10026         0.0.0.0:*               LISTEN      4548/clamsmtpd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4077/mysqld
tcp        0      0 0.0.0.0:6667            0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:11              0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:5742            0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:79              0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:15              0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      3163/portmap
tcp        0      0 0.0.0.0:54320           0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:2000            0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      4911/havp
tcp        0      0 0.0.0.0:27665           0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:1524            0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      3943/sshd
tcp        0      0 0.0.0.0:119             0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5796/cupsd
tcp        0      0 0.0.0.0:1080            0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 127.0.0.1:7000          0.0.0.0:*               LISTEN      5927/gnugk
tcp        0      0 0.0.0.0:3128            0.0.0.0:*               LISTEN      5703/(squid)
tcp        0      0 0.0.0.0:12345           0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 127.0.0.1:1721          0.0.0.0:*               LISTEN      5927/gnugk
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      4853/exim4
tcp        0      0 0.0.0.0:12346           0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:635             0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:1723            0.0.0.0:*               LISTEN      5136/pptpd
tcp        0      0 0.0.0.0:49724           0.0.0.0:*               LISTEN      6823/portsentry
tcp        0      0 0.0.0.0:540             0.0.0.0:*               LISTEN      6823/portsentry
tcp6       0      0 :::80                   :::*                    LISTEN      5950/apache2
tcp6       0      0 :::22                   :::*                    LISTEN      3943/sshd
kubuntu@kubuntu:~$

```

I wonder about that "root -1" user process that I see occasionally...

As for hardware, I took the box back to the "vendor" and they blamed the power supply, claiming that it didn't have the -5 volt supply.  They replaced that and I still reinstalled, from the 8.04 CD they provided.  I need to dig that up and check the checksum/hash with GtkHash...

I was waiting for the latest stable but will have to get onto launchpad and wait the 6-10 weeks...  Either that or go someplace with a CD burner...  I only upgraded to 9.04 for package Barry, which does not work.  I've read in these forums where people claim that downloading Jaunty upgrades have caused problems.

---

### Post by doas777 on 2010-03-11
> **Elludium_Q-36 said:**
> I guess your eyes glazed over on the part about the iDEN modem which generally has speeds of 2kb/sec.  That's a Motorola iDEN cell phone, tethered.  Theoretically it can do 25 K, if I recall correctly but never does.  What was that commercial with the tag-line, "Not going anywhere for a while?"

I downloaded the updates from 8.04 to 9.04 and the roughly 1.5G took about a WEEK to download.

Assuming I find the CD provided AND assuming the checksum checks out, Ubuntu needs to download packages.  Then there are the ones I added...  I've been told that putting an old /home/ dir where associated packages not installed is not a good idea.

If I were a Yuppie with wads of cash, I might have been on a Mac and not even heard of Ubuntu.
be carefull about the casing of your 'b' in kb. 25Kb is a little more than 3KB.

---

### Post by Elludium_Q-36 on 2010-03-11
To clarify, I'm using Jaunty 9.04 and have used package guarddog to block ports including but not limited to: 1524, 6667 & 31337.

---

### Post by cdenley on 2010-03-11
The top command is also realtime, but the command I gave you quits after 1 iteration. I don't see anything hogging your CPU in the output you posted.

Removing portsentry might make it easier to determine if there are any listening services which should not be there. That application basically opens up all commonly used ports to trick people into connecting to it as a sort of intrusion detection.
```

sudo apt-get remove portsentry

```

Are your web, mail, and ssh servers publicly accessible? If so, I hope you install security updates. A DOS attack might explain your problems.

Botnets do mostly target windows, but there is no shortage of script kiddies looking for linux users stupid enough to allow a root password for ssh servers or enabling VNC. There can occasionally be malware, which is why you should stick to the ubuntu repos.

---

### Post by Elludium_Q-36 on 2010-03-11
True, doas777 bits and bytes... 1024...

KPPP has a line graph "plotter" and at the top it gives a weighted instantaneous connection speed and a "Maximum" and the height of all "plots" deminish if there is a spike.  it often reads, "2.0 (max 12.0) kb/sec".

I assume the convention is Kb = Kilobit, while KB = Kilobyte but the convention is not always followed. The information is often not out there but misinformation surly abounds :(

Regardless, this connection is excruciatingly slow.

I never thought I would miss and long for a dial-up connection.

****

Thank you cdenley.

I need to capture the state when it's running amuck...  It can be 100% CPU and I will kill firefox, opera, etc. processes assumed to be resource hogs and it will still grind away at 100% but not on processes that are shown.

Aside from the learning experience, I only dabbled because the box was a bit screwy anyway.  Medibuntu and others I proudly say I use web-based e-mail, as any smart end user or intermediate should.  Servers were installed with packages that seemed to proffer system hardening...

If I were to operate a honeypot, there is a package that emulates windows vunlerabilities and I'd put that in a DMZ.  For now, I'm just running a standalone workstation. I would love to set up LinuxMCE on a dedicated box, mainly for Asterisk and the security system.

No, I have no intention of running traditional servers from this box.  It's too early on my learning curve.  This should be a client only box, unless certain applications need a process server...

On ever boot, I kill nepomukserver and bonobo-activation-server.  I'm not sure about console-kit-daemon but it persists if killed.
Before posting, I removed: atd, avahi, nepomuckserver, miredo and inetd.

I removed portsentry, without rebooting or issuing a process restart command and attached the outputs in ODF/text (.odt) format, due to a shorter limit on .txt file upload here...

I'll have to find some decent unix/linux/ubuntu help/tutorial files as what is packaged lists the commands & flags/switches but little more.

I had Barry working before, from Debian repos but yes, it's better to stick to Ubunty repositories.  With the repos, you can learn of update releases...

I'm no fan of VNC and am wary of remote desktop apps but rlogin can make the life of an admin easier.  I've ran SOHO LANs, for lack of more qualified personell and considered setting up thin-clients/network boot because the end users would "play".

Aren't we all end-users and beta testers when you think about things?

---

### Post by cdenley on 2010-03-11
> **Elludium_Q-36 said:**
> 
No, I have no intention of running traditional servers from this box.  It's too early on my learning curve.  This should be a client only box, unless certain applications need a process server...


Well you appear to be running apache, sshd, pptpd, and havp. If any of these services aren't secured properly and were accessible from the internet, I wouldn't be surprised if your system was compromised.

---

### Post by OpSecShellshock on 2010-03-11
Yeah, just looking at the netstat output it seems this machine is running as a web server (apache listening on port 80), it's listening on port 22 for sshd, a squid proxy on 3128, and a SQL server on 3306. Might be remnants from the previous owner, though I don't know why the folks you got it from wouldn't sanitize it prior to reselling. I'd suggest killing those processes and then removing the packages, as they don't seem to be in line with your intentions for the box.

---

### Post by Elludium_Q-36 on 2010-03-11
From the package description, it looks like havp was added with ClamAV to retrieve virus definitions but that doesn't seem to be working properly anyway,  There are few anti-virus/anti-malware applications in the repos...  I wouldn't have knowingly added apache.  Might have been a residual config...  

I killed apache, sshd, pptpd, and havp but received no error messages.

Package: apache2-mpm-prefork seems to have been the apache server. Package: openssh-server provided the sshd server. pptpd is the named package and ships with bcrelay "Broadcast relay daemon".  Package havp, "HAVP (HTTP Antivirus Proxy) is a proxy with a ClamAV anti-virus scanner. The main aims are continuous, non-blocking downloads and smooth scanning of dynamic and password protected HTTP traffic. Havp antivirus proxy has a
parent and transparent proxy mode. It can be used with squid or standalone."

I have all of them marked for removal.

Apache seems to have been installed by zoneminder but I won't be using that on this box and will go with a packaged implementation of LinuxMCE on a dedicated box for what zoneminder does (it is a security camera program).  I had Asterisk downloaded but only need client/sip/softphone on this box and can use AsteriskNOW or learn on LinuxMCE.

sshd affected ssh, which the description said can be safely removed with nothing dependin on that...  But sshd affects scponly..."scponly is an alternative 'shell' (of sorts) for system
administrators who would like to provide access to remote users to
both read and write local files without providing any remote
execution priviledges.  Functionally, it is best described as a
wrapper to the mostly trusted suite of ssh applications."  That's interesting...  Remote users reading and writing...

I've already noticed the memory and swap drop and the CPU useage does spike but doesn't seem to be hanging around 100%
I'm sure there are other packages/processes that should go.
Any further hints/advice would be appreciated.
Thanks Cdenley!

---

### Post by Elludium_Q-36 on 2010-03-11
Hello OpSecShellshock,

I killed squid and SQL as well.
I didn't notice an appreciable reduction of drain on system resources, mem/swap mem/cpu but those are two fewer processes that would have jumped-in at some point.

Squid is now marked for removal.

It looks like package mysql-server-core-5.0 may have been associated with package: Akonadi which seems to have once been installed.  mysql-server-core-5.0 seems inter-related with: mysql-server-5.0   and both are marked for removal.
I left package: mysql-client-5.0 to remain.

Thanks OpSecShellshock!

---

### Post by Elludium_Q-36 on 2010-03-11
Does anyone know about:

nepomukserver

or

bonobo-activation-server

I usually kill them both on every boot but don't know the source package...

rkhunter no longer warns about ports: 1524, 6667, and 31337 but still reports: 2001 & 7000 though I do have them blocked using guarddog.

rkhunter reports "Checking if SSH root access is allowed   [ Warning ]"
That's a little unsettling...
There were a few other warnings that are probably the same as in the files I attached earlier in this thread.  

I also ran chkrootkit again which reported an anomaly, suspicious files and a possible scalper worm...

---

### Post by ApEkV2 on 2010-03-11
> I wouldn't have knowingly added apache. Might have been a residual config...
Then kind sir, if you are not in control of your computer, somebody else will gladly take it from you.

From the previous posts, it seems you truly don't know what is installed and running on your comp.
The only solution to your problem of not knowing what programs were installed and running is to reinstall ubuntu.

---

### Post by tekkidd on 2010-03-11
Hey in my opinion i would do a wipe on a computer acting this screwy.

---

### Post by yomuffin11 on 2010-03-11
Must of been a faulty installation. The installation could have been a bit buggy as sometimes this will happen. I tried installing Ubuntu 9.10 4 times, never worked (well) for me, neither did 8.04. I ended up using Ubuntu 9.04 which worked the best for me and have only seen slight, useless problems! :)

But whatever you do, please do me a favor and do not go to Microsoft Windows XDD it is just not right...

---

### Post by Elludium_Q-36 on 2010-03-12
What many don't realize is that in Unix/Linux/*nix/Ubuntu, etc, pretty much everything is treated as a file, including devices.  You can overwrite or delete the offending file(s), reboot or ```
*/init.d/* restart 
``` and be good as new.

I removed some packages (current markings attached) and right now, it only has cupsd listening on port 631 (IPP/Internet Printing Protocol) and exim4 SMTP on port 25 (SMTP/Simple Mail Transfer Protocol).  For a while netstat didn't answer with the processes listening but they are there.  I don't need either as I don't even have a printer configured (subject for another thread) and blocked them via guarddog for now.  I use web-based e-mail and I think that's highly advisable.  Outlook is for spawning virus and spam.  I wish I knew which one opened port 31337, ELEET?LEET!  That seems to have been opened from a package!!!

In windows, I'd be looking for uninstall .exe programs, registries... I don't even want to think about all that.  Windows is great for people who want to be in a full service computer business because it breeds the need for customer support while the one holding the hand of the customer/end user probably needs tech support.

I should get an AGP (accelerated graphics) card for this motherboard as KDE is said to grab resources.

This box has other issues but it's much closer to the hurd now :)
I only did an online version upgrade to get package(s) Barry but something depended upon must be screwy (I'll go to another thread to address that).  I see in other threads that people have claimed trouble from online upgrades from 8.04 to 9.04 but this box seemed to have had some residual configurations that were less than ideal.

Thanks to whomever released the latest version of KPPP [now 4:4.2.4-0ubuntu1~jaunty2 (jaunty-backports) ] can now have an unexpected disconnect and restart KPPP from the front-end without rebooting, once I verify that it points to how the hot-plugged device is referenced.  It still won't work with ethernet connected (again, I will address that in another thread but Under Gateway options of the account, the configuration radio button is on Default gateway as opposed to static and option "Assign the default route to this gateway" is checked).

It seems all but solved.  It would be nice if package maintainers spent a little more time in writing descriptions/read-me and read-before-installing files...  I'll just open a couple hundred firefox tabs and see if it acts goofy again ;-? .  It seems to be relatively stable now, much more than your garden variety unadministered windows box.

I wasn't serious about going back to a windows box but it was that frustrating!  I went and grabbed live & alt .iso files of 9.10 "Karmic Koala" but I might as well wait about a month for 10.04 LTS "Lucid Lynx".  9.10 "expires" in about a year while with 10.04 LTS, the desktop is planned to be supported 'till April 2013 and the server 'till April 2015. Thanks for all the "votes" and good advice.  I've closed my ports but will "listen" for any additional good advice via this thread.

---

### Post by OldMerovingian on 2010-03-12
He said he cannot do a fresh install due to a really slow data connection.  

However, isnt there a place you can go and log on to a high speed connection just to get your system installed and up to date?  You don't have friends, parents, aunts, uncles, brothers, or libraries where you can go to take advantage of a decent connection?  Barnes and Noble or Boarders even?

Just go to a college around where you live, stroll into the library and connect.  My campus lets anyone who is anyone stroll in and use their connection.  

Just my two cents.

EDIT:  I am assuming you are using a laptop, and if not, I retract all of the previous statement.  :-)

---

### Post by viper250 on 2010-03-12
on a used system the first thing I do is to remove any and all dust from  fans , cooling fins, power supply, etc.
ridding possible heat problems is half your battle.
2nd using software already on a used system is risky because you never know where it has been (on the web)  this alone prompts me to wipe all drives and reinstall
I am an electronics reclaimer and I protect clients by wiping the systems before reinstallation of any os.

---

### Post by magian on 2010-03-13
Blah blah blah...just wipe the damn thing and reinstall and stop whining.

---

### Post by Elludium_Q-36 on 2010-03-13
Yes, OldMerovingian read the thread and it's a VERY slow connection but also a desktop.  I have a folding hand-truck that resembles the full size ones you see truck drivers using to cart cases of soda pop / beverages into stores and wondered how silly I'd look crashing my box up the cement steps of the local internet cafe'.  I'd have to bring a monitor too and if I had a flat-screen I might have been tempted as a keyboard and mouse could easily be stffed into a backpack.  A CRT/Tube monitor makes the notion even more silly.

*****

viper250, a little bit of air-conditioner filter material on the power-supply fan inlet may be a good idea in an environment with dust/pollen/pet dander, etc.  I had another box with Ubuntu Fiesty Fawn that I installed myself and it worked flawlessly. This is Kubuntu and the reclaimer said KDE3/KDE4 was unstable but sent it out the door.  When I had called, they blamed the power supply and claimed it was probably the -5 Volt circuit.  When they plugged in the tester, that of course is what they said was the trouble :-P

I moved and had to leave the other Ubuntu Feisty (7.04) box.  I was in a hurry to get a new machine and found the reclaimer.  I asked if they had any AMD machines and was told they had one with Kubuntu...  They sell cracked windows with forged/copied, etc. product keys.  A lesson learned...  In the time I'm waiting for 10.04 LTS "Lucid Lynx" to come out and get through the first bit of growing pains (bugs), I can back up my data, configuration files and make a package list.

*****

I just ran GtkHash, simultaneously checking 2 ~700M files and it was using about 85% cpu, with a niceness of 8.  I navigated desktops and worked in other apps, NO PROBLEM!  Getting rid of other DAEMONs did the trick methinks.  "Thanks" for all the votes from the troll poll but again, in *nix/ubuntu most everything is a file.  Y'all can throw your babies out with the bathwater but I'd rather actually LEARN something.  Y'all spent too much time in the windows world with your rebooting and reinstalling!  Editing or overwriting a file, then doing an /init.d/ restart takes a few more synapses.

Once again for the cheap seats...  I currently have  "Jaunty Jackalope" 9.04, released on April 23, 2009, which is only supported until October 2010.  I should waste my time because you say so?   "Karmic Koala" 9.10 was released on October 29, 2009 and is only supported until April 2011.

Do you understand what the "LTS" after the version number means?  From packages.ubuntu.com , I recently got KPPP for an Ubuntu 6.06 LTS "Dapper Drake" box.  TRY THAT WITH: Edgy (6.10), Feisty (7.04) or Gutsy (7.10); NOT HAPPENING!  I'd have been dead in the water with my old Feisty (7.04).  I'm waiting for the planned April release of "Lucid Lynx" 10.04 LTS which will be supported until April 2013 (Desktop) or Supported until April 2015 (Server)!!!  

You sure won't win over people to Linux if you talk them into installing over their windows data and configurations, then keep wiping thier data/configs and reinstalling at the first sign of trouble.  Go away evil trolls, you have no power here!

---

### Post by Elludium_Q-36 on 2010-03-16
Upon further analysis, it seems I am beleaguered by the all too common problem of Firefox & X.org sucking the cpu into a quantum singularity (I'd call it a hole but John Wiley Price may be reading, so I won't mention cake either!).  It seems Opera is involved in this brouhaha and browsers using the Mozilla gecko may not be innocent either.

I think package upgrades did not help.  One bug in 10.04 mentions that if you copy, close that window before pasting, your item will not be available to paste from the clipboard.  I have that issue and am in 9.04!!!!

My network manager has gone south too.  Before I could not have ethernet attached AND be logged into KPPP as Ethernet would take presidence but now ethernet won't work, regardless of the state of KPPP or modem attachment.

I will seek and post elsewhere but will be happy if these issues can be solved here as the title of the original thread is pretty nondescript.

---

### Post by Elludium_Q-36 on 2010-03-17
The real trouble with this system came when I upgraded from 8.04 to 9.04.

I only upgraded to try and get Barry (Blackberry utilities) working, since Barry is packaged in Jaunty 9.04 but Jaunty doesn't work on this box.  There's probably a library or other dependency that's screwed.  

So why would I want to reinstall 9.04?  Others have written that 9.04 is to blame for many an Ubuntu ailment.  9.10 will be short lived but I'm hoping 10.04 will not be too buggy.

***Edit: Barry doesn't work on this box.  Jaunty "works" but not ideally.

---

### Post by hansdown on 2010-03-17
Hi Elludium_Q-36.

You may wish to look into the AMD connection, if reinstalling is not a preferred option.

---

### Post by Chronon on 2010-03-17
Maybe you can use the "sneaker net" approach described here: 
[http://www.fifi.org/doc/apt/offline.html/index.html](http://www.fifi.org/doc/apt/offline.html/index.html)

---

### Post by adamkleiner on 2010-03-17
You *do* realize that Canonical will ship Karmic Koala to you on CD for free (yes, that's $0.00, and they (presumably) pay for postage), right?
 
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by Elludium_Q-36 on 2010-03-18
Thanks for the input adamkleiner.  I'm sure you had helpful intentions but I addressed what you mention earlier in the thread.  If I ordered a free press CD now, I might as well wait for 10.04.  It now can take TEN WEEKS FOR A CD TO ARRIVE.  I trekked to an internet cafe' and got Kubuntu 9.10 in a live cd .iso plus an alt .iso and both checked out via MD5 using GtkHash.  However, if I burned a CD and installed either I would still have a signifigant download on my 2K connection.  Then I probably lose my elective packages, data and configurations.

The download to transition from 8.04 to 9.04 was over 1Gig and took EIGHT DAYS.  When you install from a CD, many files are required to be downloaded.

I only made the upgrade to have upstream Barry but Barry does NOT work with this implementation.  I don't know how 9.10 will perform in comparison to 9.04 but I would be inclined to revert to 8.04.4
[https://lists.ubuntu.com/archives/ubuntu-announce/2010-January/000128.html](https://lists.ubuntu.com/archives/ubuntu-announce/2010-January/000128.html)

Here's the thing AND I HAVE ADDRESSED THIS EARLIER IN THIS THREAD, the support for both 8.04 AND 9.10 expire next year.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
I'd like to get a LTS desktop stabilized on this box and move on to getting a LTS SERVER stabilized on my other box.  Actually, I'm waiting for the lastest LinuxMCE but might put AsteriskNOW on there in the interim. 

******

hansdown, "AMD connection"???  I tried Google and searched the forum but I'm stumped.  Do you have a link.

******

"Chronon", thank you for the link!  I glanced at the content but unfortunately it looks like the other machine needs to be a linux box too and any machine in reach is courtesy of the legacy of Bill Gates.  I have read posts that offered a simple method of modifying the download script generated by synaptic, to work on Windows but it did not work.

I will study the link for future reference.  Do you have info on how to modify the synaptic download script for a windows box?
*******

By the way, I have not allowed ANY outside JavaScript on Firefox and it has not gone into CPU latchup for a couple days but has crashed.  Seems xorg & 9.04 are my troubles.
****

I'm not sure if I should wait for 10.04, run 9.10 or get 8.04.4 as the latter two both expire in a year.  The release page for 8.04.4 states, "In all, some 70 updates have been integrated, and updated installation
media has been provided so that fewer updates will need to be downloaded
after installation."  [https://lists.ubuntu.com/archives/ubuntu-announce/2010-January/000128.html](https://lists.ubuntu.com/archives/ubuntu-announce/2010-January/000128.html)

If I stay with this plaged version, I could really use help with my networking and have started this thread:  [http://ubuntuforums.org/showthread.php?t=1431461](http://ubuntuforums.org/showthread.php?t=1431461)

Thanks to all who try to offer help.

---

### Post by ApEkV2 on 2010-03-18
> **adamkleiner said:**
> You *do* realize that Canonical will ship Karmic Koala to you on CD for free (yes, that's $0.00, and they (presumably) pay for postage), right?
 
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

more people need to read the whole thread before posting.
I wouldn't be able to fathom dial up with updates

---

### Post by Elludium_Q-36 on 2010-03-19
I think dial-up is generally faster than iDEN.

Though KPPP uses lower case k and lower case b, I think it's actually KiloBytes and the graph generally hovers aroud 2 when I'm loading/downloading.  I did a speed test and it reported a whopping 20Kb/sec Kilobit.  This is a Motorola iDEN phone on Boost Mobile via Nextel, owned by Sprint.

Dial-up, in theory gets 56Kb and can be slower depending on connection and theoretically faster with compression.

Boost Mobile now offers phones on Sprint's 3G CDMA network.

I think if I do NOT allow ANY JavaScript in Firefox, and get my networking figured out:  [http://ubuntuforums.org/showthread.php?t=1431461](http://ubuntuforums.org/showthread.php?t=1431461)  I may have a livable system untill 10.04 gets worked out.  I'll try another browser if I need a site with JavaScript.  Maybe I'll go to 8.04.4 but I'm not inclined to try 9.10

---

