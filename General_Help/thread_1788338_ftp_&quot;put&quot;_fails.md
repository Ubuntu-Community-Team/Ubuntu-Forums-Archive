---
title: "ftp &quot;put&quot; fails"
date: 2011-06-22
forum: General Help
---

### Post by ldt on 2011-06-22
I'm having an Ubuntu “upload” problem. By upload I mean, a)terminal ftp put, b)Filezilla upload, c) HTML textfield send, d) Wikipedia page edit save. This includes sending email from my webmail client and posting this message to the Ubuntu forum.  The testing seems to eliminate the network and the hardware, leaving me suspicious of Ubuntu in all flavors. 

I have five computers on my home LAN. They are all connected to a cable modem through a Linksys Wireless-N router. The five computers and there connection configuration is:

1) router ->(wire) -> hub -> System 76 panp6 running Ubuntu 11.04 (was 9.10)
1.5) router ->(wireless) -> System 76 panp6 running Ubuntu 11.04 (was 9.10)
2) router ->(wire) -> hub -> Old (11+yr Pentium) running Ubuntu 9.04
3) router ->(wire) -> hub -> Dell Windows XP 4) router ->(wire) -> Dell Windows 7
5) router ->(wireless) -> HP Laptop Windows 7

The upload problem is that the attempt just hangs forever until I manually kill it. The ftp upload attempts leave behind a file created on the remote machine with the correct file name but with zero bytes of data. I can do an ftp connect, delete files and download files, but upload fails.

Ftp upload works on every machine and configuration except the two that are running Ubuntu. Old machine, new machine, wired, wireless, 9.04, 9.10, 11.04 – makes no difference. All Ubuntus fail.

I'm stumped. Any suggestions what might be going on here?

---

### Post by psusi on 2011-06-22
Ping the server with -M do -s 1472.

---

### Post by ldt on 2011-06-22
ping domain.name.com works fine
ping -M do -s 1472 domain.name.com hangs and hangs

I'm not familiar with the ping options. Does this result mean anything to you?

---

### Post by psusi on 2011-06-22
You mean you never get a reply?  When you hit ctrl-c, it should say how many packets it sent.  Does it show it sent a bunch and 100% were lost?

The -s specifies the size of the packet to send.  Try lowering it to 1464 and see if you get responses.  Also try running tracepath to the server.

Have you mucked around with any kind of firewall?

---

### Post by ldt on 2011-06-22
ping domain.name.com - reply every ~80ms
ping -M do -s 1464 domain.name.com - reply every ~80ms (says 1472 bytes sent)
ping -M do -s 1472 domain.name.com - no replies, ctrl+c says 43 packets sent, 0 replies 100% loss.

tracepath domain.name.com - 3 local responses then an endless string of "no reply"
tracepath address of one of the other computers on the LAN - 3 local replys and
"Resume: pmtn 1500 hops 1 back 64"

I haven't done anything with any firewalls. It is just whatever you get with a clean Ubuntu 11.04 install and the standard router set up.

---

### Post by ldt on 2011-06-22
Correction on the tracepath info.
tracepath domain.name.com
1. this.local       .14ms ptmu 1500
1. 192.168.1.1   10ms
1. 192.168.1.1.  10ms
2. no reply
3. no reply
...

For the other local machine
tracepath other
1. this.local    .14 pthm 1500
1. other.local  10ms
1. other.local  .5ms
Resume: ptmu 1500 hops 1 back 64

That's not quite the way I interpreted it at first.

---

### Post by psusi on 2011-06-22
It looks like you have a broken router that is not passing back ICMP packets and has a reduced MTU.  This is probably because your ISP uses the terrible, horrible no good very bad protocol known as PPPoE, and the router they supply you with is not configured properly to inform your computer of the reduced MTU, and also is unable to pass back the ICMP messages telling it that it needs to reduce the size of the packets it is sending.

Try running this and it should fix it:

sudo ifconfig eth0 mtu 1492

---

### Post by ldt on 2011-06-23
You are a true genius. Thank you very much. It worked. I tried "ftp put" just before, then executed your suggested command, then retried the same "ftp put" on the same file. It hung the first time as usual and the second time it completed instantly with "3456 bytes sent in 0.00 sec (14610.4 kB/s)". I can also now send email from my webmail client which I couldn't do before.

I haven't checked but you are probably right about the ISP. Unfortunately, it is my only choice here besides DSL. Sidebar issue with the ISP: the connection is rated and 12 Mbits/sec but the CNET bandwidth meter often reads 500 kB or less. I called them once and they suggested rebooting the modem. I did and sure enough the bandwidth jumped to 11.5 MB. The problem is that it rapidly degrades back down to 500kB within a week or two. I haven't called them to ask why. My suspicion is that the support service won't have any other answer than to reboot.

The problem with rebooting is that it always rearranges the IP addresses on the LAN. That doesn't seem to be a problem for the Windows machines but I have to fix it manually for the two Ubuntu machines. I understand from this forum (some time ago, maybe from you) that there is a fix to this problem but I've never taken the time to do it and by now have forgotten the suggestion. Maybe now while I'm in fix-it mode would be a good time.

Anyway, that's a lot of sidebar issues but just thought I would ask since I have the attention of a great master of the subject like you.

Again, thank you so much for you help.

---

### Post by psusi on 2011-06-23
Your Windows computer doesn't have this problem though?  Very odd.  I wonder why.

---

### Post by ldt on 2011-06-23
Sorry, I overstated the case. The Windows machines are DHCP enabled and always seem to know where the wireless printer is regardless of its IP address. But yes, I do have to change the Windows hosts file manually to hit the Apache servers and version control repository on the Ubuntu machines. But I think I was told there was a way to enable DHCP or something like that on Ubuntu so that I didn't have to manually change the hosts file each time the IP addresses change. Since I use one of the Ubuntu machines as a version control repository I always have to keep the hosts files current to have access to it. I was thinking that the first time I solved that problem (on this forum) that I was told there was a way to avoid having to do this manually each time.

---

### Post by psusi on 2011-06-23
I meant the problem with the MTU.  Ubuntu uses DHCP by default so you shouldn't need to mess with the hosts file.

---

### Post by ldt on 2011-06-24
Well, I didn't even know what mtu was before this discussion, but a little Google searching tells me that the default Windows XP is 1480. Being less than the 1492 that works with Ubuntu I would assume that is why I wasn't having the problem on the Windows machines. Somewhat contradictory however, I also came across this ping mtu test.
 

 ping [www.expedient.net]("http://www.expedient.net/") -f -l 14xx
 

 With this test I found that 1466 was the max that would work. I'm not sure what that means but with mtu of 1480 on Windows and 1492 on Ubuntu the "upload" problem seems to be solved.
 

 Again, thanks so much for your help.

---

