---
title: "Bizarre Linux peer-to-peer connection problem"
date: 2012-04-09
forum: General Help
---

### Post by ladasky on 2012-04-09
Hi folks,

I've been trying to get help on this particular issue for a few days in a few different threads.  As I learn more, I post again.  This time I'm posting under a new, more general title.  The previous thread is _[here]("http://ubuntuforums.org/showthread.php?p=11824263")_.

Here is my setup: two computers on my home LAN, fairly new Gigabyte motherboards with AMD 6-core CPU's, both running Ubuntu 11.10 x86/64.  The two machines are not identical, but highly similar.  My router is a Linksys WRT54G with the most recent firmware.

The symptom: peer-to-peer connections between the two machines stall and restart in a semi-regular pattern; about two minutes up, then about two minutes down.  I have a graphic representation of my findings posted _[here]("http://www.flickr.com/photos/15579975@N00/7055314933")_.  I first noticed this when I set up an **ssh** connection between the two machines.  However, even plain-old **ping** times out.  The graphs show the behavior of the pings when I am not logged in using ssh.  

When I do use ssh, and I execute commands, timeouts can be induced to occur more quickly.  Executing a **du** command produces about 10 kB of output from my slave machine.  If I try to execute a du over ssh from my master machine, it will almost certainly hang up somewhere in the middle -- only to resume again, 1-2 minutes later, if I wait.

If I'm logged on to the slave machine from the console when one of these remote timeouts occurs, I can still use the slave machine normally.  The system as a whole is not stalled in the least.  I see no CPU loading, no change in memory use, no network traffic.

The ping timeouts go away if my slave machine is booted into Windows 7.  I can ping it continuously then.  I didn't drop a single ping in over a half-hour.

I tried reversing the master and slave machines.  The same behavior is observed in the reverse direction.

This would suggest that the problem is specific to the Linux implementation, and that the problem is something that my slave machine is doing.  All of my hardware is apparently working.  However, turning off the Linux firewall on the slave machine with a **sudo ufw disable** command does not affect the behavior.

Does anyone have a clue what might be causing this?  Thanks!

---

### Post by dcstar on 2012-04-10
> **ladasky said:**
> 
.........
Does anyone have a clue what might be causing this?  Thanks!

Install the **ethtools** package and turn off Flow Control and perhaps other Auto-negotiated items.

---

### Post by ladasky on 2012-04-23
Hi, I know it has been weeks since I posted this thread.  I got distracted by a massive system crash involving _[a buggy new NVidia GPU driver]("http://ubuntuforums.org/showthread.php?t=1960714")_ that doesn't work with somewhat-older video cards, and/or a _[hardware-based RAID utility found in the AMD 600/700 series South Bridges]("http://ubuntuforums.org/showthread.php?t=1960251")_ which can apparently fail irreversibly.

Once I got everything working again, I returned to this peer-to-peer connection problem.

First, thanks to dcstar:

> **dcstar said:**
> Install the **ethtools** package and turn off Flow Control and perhaps other Auto-negotiated items.

I found the **ethtool** package (note spelling), and did some reading, eventually finding this _[official Ubuntu help page]("https://help.ubuntu.com/community/UbuntuLTSP/FlowControl")_.  But apparently, not all NICs expose flow control and/or auto-negotiation:  attempting **sudo ethtool -A eth0 rx off** returned the error message "Cannot get device pause settings: Operation not supported."

Then I noticed something.  In a _[very early post]("http://ubuntuforums.org/showpost.php?p=11816445&postcount=1")_ on this problem, I stated that web browsing from the slave machine's console appeared to be operating normally.  Well, I was just unlucky with my timing the first time I checked.  It turns out that network functions from the console were also timing out.  If I walked from one room to the next at the wrong moment, I would fail to notice the problem.

And this led me to remember a problem that has been plaguing me for months, one that I'd thought I'd solved: the _[Realtek NIC driver nightmare]("http://ubuntuforums.org/showthread.php?t=1022411")_.

When I upgraded both systems to Oneiric, my older computer, with a Gigabyte GA-MA78-US2H motherboard, worked with the new r8169-series NIC driver right out of the box.  The newer Gigabyte GA-990GXA-UD5 motherboard has the same brand of NIC on it, so I assumed that this computer would also work with the new driver.  NOT SO.  I had to remove and blacklist the r8169-series driver all over again, then reinstall the r8168-series driver.  After allowing ssh through my firewall -- everything is working.

Whew!

---

