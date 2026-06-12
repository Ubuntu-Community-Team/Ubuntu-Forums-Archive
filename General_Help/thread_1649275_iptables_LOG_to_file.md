---
title: "iptables LOG to file"
date: 2010-12-20
forum: General Help
---

### Post by terminator14 on 2010-12-20
I'm working with a Linux based distribution (meant to be run on machines that act as a router and firewall), and I need to make iptables record all traffic in the FORWARD chain to a separate file so that I can analyze it later. The problem is that the module that provides -j LOG for iptables is not available here. What is available is nflog, which, as far as I can figure, is an alternate way of logging data from iptables.

I have a choice here:

1. Figure out how to enable/load the LOG module into iptables, and make syslog-ng take care of writing the log to a separate file

OR

2. Figure out how to use the already existing NFLOG system

I have tried both, and hit dead ends in both cases. What is the easier of the two solutions? 

Questions about solution 1:

Do I have to recompile iptables or the entire kernel to do option 1? Or can I simply compile the LOG module and load it? If I can get away with just compiling the LOG module, where do I find it online?

Is syslog-ng complicated? Looking at /etc/syslog-ng.conf, it seems to be. I have to create a filter in /etc/syslog-ng.conf to pick up on the traffic I need copied to a file don't I? Can I make the filter based on a tag I create with --nflog-prefix?

Questions about solution 2:

Where can I find documentation on nflog? Is it the same thing as ulogd2? If so, where can I find documentation on /etc/ulogd.conf? I've been searching for hours, and other then some specific examples that make ulogd write to a mysql database and not a file (not what I want), I haven't found anything even remotely attempting to explain how that file works. If nflog is NOT the same thing as ulogd2, where do I find info on NFLOG? This is driving me crazy since there seem to be plenty of poorly documented examples online of nflog and ulog being used as iptables targets, but the lack of documentation makes me wonder how in the world anyone figured out how to use them.

---

