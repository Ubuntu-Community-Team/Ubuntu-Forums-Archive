---
title: "ssh problem, LONG pauses"
date: 2012-04-04
forum: General Help
---

### Post by ladasky on 2012-04-04
I posted a similar article to this one about 12 hours ago over in the Security Discussions forum.  Apologies to those of you who have already seen it.  I'm not getting any replies there, though I thought that it would be the best forum to reach people who know about ssh.  I'm casting my net wider.

I am running GROMACS 4.5.4, a package for molecular simulations.  It is one of Ubuntu's supported packages.  I have two nearly-identical computers, AMD six-core machines both running Ubuntu 11.10 x86_64.

GROMACS has a multiprocessing-aware version (also on Ubuntu's supported software list) which uses Open MPI to communicate between CPU's.  I have been using the multi-CPU version of GROMACS on a single machine for a while now.  I'm trying to harness the second machine as well over Ethernet.  In other words, I'm trying to set up a little cluster.

According to the Open MPI documentation, I need a working ssh connection between my master machine and slave machines.  So I have installed the openssh-server package on my slave machine.  I followed the directions _[here]("http://randomusefulnotes.blogspot.com/2010/12/setting-up-mpi-cluster-on-ubuntu.html")_ to set up the public encryption key.  

Once I got everything set up, I tried running GROMACS-mpi once, but it crashed.  So I figured that I should just go back to basics, and simply test whether my ssh connection was working.

I can log in to the slave machine from the shell using ssh, but I see two problems.  Actually, these may just be two manifestations of the same problem.  Both involve random, LONG delays.  

1) After I type a few commands, suddenly the cursor just freezes.  It can do this while I'm in the middle of typing a command.  Alternately, ssh can freeze in the middle of printing a lengthier output, say, the result of a "du" command.  If I'm patient, the text that I typed right as the cursor froze will eventually appear -- but I might have to wait as long as three to five MINUTES.

2) I also receive frequent timeouts when I log off of ssh, and then try to log back in.

I'm doing this at home on my LAN.  Both of my machines are sitting behind a firewall-enabled router.  Local network traffic is absolutely quiet.  All other functions on these two machines, including web browsing, etc. continue to function absolutely normally while these hangups occur.  I have tried using ssh from the master computer, both while logged on locally to the slave computer and while not logged on.  It doesn't seem to make a difference.  None of the directories on either machine are encrypted, which I understand from _[this post]("https://rohieb.wordpress.com/2010/10/09/84/")_ can cause issues when trying to access a public key.

I suspect that one of these long delays probably also occurred when I tried to use GROMACS-mpi, and that it caused my crash.

Any suggestions?  Thanks!  :confused:

---

### Post by bibble235 on 2012-04-04
This is really hard to diagnose but my thoughts are

1/ Check the profile is not trying to mount something not there
2/ Install iftop
3/ Check the NTU

Probably none of these but who knows

---

### Post by ladasky on 2012-04-05
Followup:

My problem is not solved yet, but I did one more experiment.

It doesn't particularly matter to me which of my two computers is the master.  I just chose the one that I sit in front of to be the master.

I tried reversing the roles today.  I set up openssh-server on my original master machine, and logged into it from the original slave.  I tried logging in and I tried various commands.  The symptoms were identical as far as I can tell.  The same long pauses occur.

I've found that a du command produces about 12K of text.  If I execute a du over ssh, it is almost certain that it will hang in the middle somewhere before completing.  Once in a while it completes.

I can type ls and other commands with short responses several times over a minute or two, before a hangup occurs.  This suggests that the hangup occurs faster the more data that I try to send.

When the ssh link is hung, it does not respond to anything, not even ctrl-C.

CPU, memory and network loading are all very light on both machines.  I see no obvious changes in behavior when the hangup occurs.  One thing I CAN see on the System Monitor is that every keystroke I enter to the ssh window issues an outgoing network packet, and that a network packet is promptly returned by the other machine for every packet sent.  This is true even when the system is hung.  It's still responsive on one level.

Does that help anyone to figure out where I should look next?

---

### Post by ladasky on 2012-04-05
> **bibble235 said:**
> This is really hard to diagnose but my thoughts are

1/ Check the profile is not trying to mount something not there
2/ Install iftop
3/ Check the NTU

Probably none of these but who knows

Thanks for the suggestions, I hope you don't mind if I ask a few questions.

1. How do I check for the system trying to mount something that isn't there?  And, does the fact that I got the same results when I tried exchanging the master and slave computers make you think that this might not be the problem?

2. OK, I got iftop.  I'm reading through the docs.  Does iftop tell me anything that the network activity panel of System Monitor won't tell me?

3. I had to look for quite a while to find out that the acronym NTU means Network Termination Unit -- in other words, my cable modem.  Well, the cable modem is on the Internet side of my router (a Linksys WRT54G if it matters).  I haven't touched the settings on the modem in years.  As I recall, I had to plug one computer directly into the modem to set it up, bypassing the router.  Meanwhile, there doesn't seem to be any trouble with any other application I try to run over my network.  I get full bandwidth, zero timeouts.  Does that help you to understand anything?

---

### Post by kevdog on 2012-04-05
This sounds possibly like a network issue than an ssh issue per se -- meaning a network card issue or router issue.  First -- strip down ssh to connect only using passwords and remove the id_rsa keys for now.  Are any firewalls involved here?? Turn them off.  During the stalled transmissions, can you ping the server from the client and vice/versa.

---

### Post by ladasky on 2012-04-06
Hi, Kevdog, thanks for your reply.  Here are the results of my latest experiments.

I disabled password-free logins for now, as you suggested.  I opened one terminal for the ssh, and one running ping.  I induced a hang by trying to do things.  Ping failed immediately when my ssh became unresponsive.  For 90-120 seconds I got "Destination host unreachable" messages from ping.  Then, ping resumed responding.  Ten to 20 seconds later, the ssh terminal was responsive again.

And hey, I just tested the Samba server that I had set up on my slave machine.  It ALSO fails periodically.  Ping becomes unresponsive when I am trying to operate Samba.  During the 90-second down time, however, Samba doesn't just wait around.  It gives me a "connection failed" dialog box.

AND! My slave machine becomes unresponsive to ping when I try to probe it with nmap.

This is new behavior.  I didn't have any problems with Samba under Ubuntu 11.04 or earlier.  This is the first time I've tried ssh.

Curiously, scp always seems to work.  I've only used it to copy small files, though.  Maybe if I used it to copy something large, it would hang too.

So, firewalls.  I wasn't aware that I had a firewall running when my systems are running Ubuntu?  Well, I guess not everyone has a router.  Some people connect directly to the Net.

My router (a Linksys WRT54G) has a firewall, of course, which mediates my connection to the larger Internet.  I don't suppose that it also filters traffic INSIDE my LAN?  There are only two settings I can see for my router's firewall -- "enable" and "disable".  For obvious reasons, I'm reluctant to turn that one off.

I'm off to read up on whatever firewall Ubuntu might have running.  But if you read this, and you know a shortcut to the critical information, I'd be grateful.

---

### Post by Ms. Daisy on 2012-04-07
> **ladasky said:**
> So, firewalls.  I wasn't aware that I had a firewall running when my systems are running Ubuntu?  Well, I guess not everyone has a router.  Some people connect directly to the Net.

My router (a Linksys WRT54G) has a firewall, of course, which mediates my connection to the larger Internet.  I don't suppose that it also filters traffic INSIDE my LAN?  There are only two settings I can see for my router's firewall -- "enable" and "disable".  For obvious reasons, I'm reluctant to turn that one off.

I'm off to read up on whatever firewall Ubuntu might have running.  But if you read this, and you know a shortcut to the critical information, I'd be grateful.
I'm pretty sure kevdog was referring to a firewall on each of the computers, not the router firewall.  The firewall on the router would be irrelevant in this case anyway because both your machines are inside the LAN.  If you're not sure just run 
```
sudo ufw disable
```on each machine to make sure it's off.

Could this be a bandwidth thing?

---

### Post by ladasky on 2012-04-07
Thanks, Ms. Daisy.

I had actually found ufw by the time I saw your post.  I have conducted several more experiments.  Here they are.

First, I let ping run for a long while, 1000 pings at a time, one per second.  I watched ping both when I was logged in to the slave machine using ssh, and when I was not.  As I mentioned before, I could precipitate a hang in pings, and in ssh responsiveness, by asking the remote machine to do things.  Surprisingly, ping ALSO fails intermittently when I was NOT logged in with ssh, and it does so in a very regular, periodic pattern.

[_This graph_]("http://www.flickr.com/photos/15579975@N00/7055314933") shows the results from two separate 1000-second ping runs when I was not logged in to ssh, followed by two histograms showing the length of the uptime and downtime cycles.  As you can see, most of the uptimes cluster in a narrow range of 121-123 seconds, and the downtimes cluster in the 111-118 second range.  Cycles can occasionally be shorter.  If you look carefully at the graphs, you will see that the first uptime/downtime cycles of each ping series tend to be short.  I don't know what that might mean.

I executed *sudo ufw disable* on both the master and slave machines.  This did not affect the result of the ping test.  After the test, I put the firewalls back up.

A Google search on the term "intermittent ping" led me to a page that suggested that I might need to update my router firmware.  I did.  This did not change the result.

But then, I found something that did alter the result: **I booted the slave machine into Windows 7**.  I ran over 2000 pings against the slave machine, and it answered to every single one of them.
 
Conclusions: 

1. This is not a problem with my router.  
2. This doesn't appear to be an ssh-specific problem, though ssh appears to interact with the underlying problem.
3. This IS a Linux-specific problem, and the problem is on the slave machine side.  But it does not appear to be affected by shutting down the Linux firewall.

Any ideas?  I'm baffled!

---

### Post by plazaster on 2012-07-25
Hi ladasky, I can't help with the SSH problem, but I know a bit about GROMACS. For parallel simulations, it relies on very fast interconnects between processors, gigabit connection in much too slow, and it will not scale. Make sure your network hardware is equivalent to an HPC configuration where these simulations are usually done. However, if this is already the case, then good luck!

---

### Post by ladasky on 2012-07-31
Hello plazaster,

Thanks for your reply.  I didn't expect this thread to reappear!  I ended up starting _[another thread]("http://ubuntuforums.org/showthread.php?p=11868067")_ to discuss this problem.

As it turns out, my network connection problem was one that I had before, and I thought I had fixed for good.  It wasn't ssh that was causing the problem.  My motherboards have Realtek NICs that had driver compatibility problems which, I eventually learned, could reappear every time I accepted a Linux kernel upgrade.  Blacklisting an incompatible NIC driver did not fix the problem, a manual reinstallation was required every time.  

Once Ubuntu switched over to the 3.x kernel series, the problem went away and appears to have stayed away for good.

In the mean time, I'm still running my GROMACS simulations on one motherboard only (but with six CPU cores).  I haven't had time to try a multi-machine simulation over ssh just yet.  Today I'm trying to clear up some firewall issues, and then I'll benchmark a GROMACS run over my LAN.

---

