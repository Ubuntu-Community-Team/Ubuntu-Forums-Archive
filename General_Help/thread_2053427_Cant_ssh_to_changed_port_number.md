---
title: "Cant ssh to changed port number"
date: 2012-09-05
forum: General Help
---

### Post by miloSA on 2012-09-05
Hi guys

Wonder if someone can help.

I'm running ubuntu 10.04.4.

I've edited /etc/ssh/sshd_config and changed the default Port 22 to a number above 20 000 and restared the service. I can see in the auth.log file that the server is now listening on this port, however I get an operation timed out error when trying to ssh on this port.

I have another server (albeit fedora) setup on this same port which I can access without a problem.

If I try ssh to the default Port 22 I just get connection refused, which is the expected response.

I've even tried disabling UFW, but that made no difference.

Any clues would be much appreciated.

---

### Post by TheFu on 2012-09-05
There are a few things to check.
* Exactly what command are you using from the client side?
* Did you setup the ~/.ssh/config file to make the port automatic?
* Did you redirect the public IP on the router port?  Actually, this is the easier way than telling every server to listen on a different port. Using router port translation, that is.
* Are you running fail2ban on something similar that needs a configuration change for the new port?  BTW, you SHOULD be running fail2ban.
* Did you try a non-root account?  root via ssh should be locked out.
* Did you try with key-based authentication?  Using passwords over the internet isn't nearly as safe ... or as convenient as using keys.

Here's a why-to [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) ; not really a how-to, but it does provide some details.

---

### Post by miloSA on 2012-09-05
Hi TheFu

Thanks for replying. Heres answers to your points to the best of my ability.

** Exactly what command are you using from the client side?*
ssh -p portnumber username@server_ip

** Did you setup the ~/.ssh/config file to make the port automatic?*
I've set the Port value in /etc/ssh/sshd_config

[I]* Did you redirect the public IP on the router port? Actually, this is the easier way than telling every server to listen on a different port. Using router port translation, that is.
[/I]This is a dedicated server with a hosting company so I have no access to the router.

[I]* Are you running fail2ban on something similar that needs a configuration change for the new port? BTW, you SHOULD be running fail2ban.
[/I]You've just taught me something new here. It is not installed, but I plan to do so now. Am going to investigate this further tonight.

** Did you try a non-root account? root via ssh should be locked out.*
Both as root was previously active. I have since set PermitRootLogin to no 

[I]* Did you try with key-based authentication? Using passwords over the internet isn't nearly as safe ... or as convenient as using keys.
[/I]Yeah I use keys so that I dont need to enter my password when logging in. This works perfectly when on port 22

Thanks again for your feedback. Anything else to look at?

---

### Post by TheFu on 2012-09-05
> ** Exactly what command are you using from the client side?*
ssh -p portnumber username@server_ip
Could your client network be blocking outbound traffic to that port?  I know every business that I've worked at blocked all ssh outbound traffic.
Test with 
```
telnet username@server_ip portnumber
```You should see the OpenSSH prompt. If not, you have a different connection issue.

> * Did you setup the ~/.ssh/config file to make the port automatic?
I've set the Port value in /etc/ssh/sshd_configsshd_config is fine - I'd assumed you did that correctly.  On the client side, setting up ~/.ssh/config makes changing ports and calling the server something memorable easier.  Use of the **ssh -p** should work however.  I like using the  ~/.ssh/config since 95% of ssh-using programs honor it, ... like rsync or cssh.  It also documents in a useful way which ports are used for ssh for all the different servers.  If you have more than just a few servers, that gets confusing.

> * Did you redirect the public IP on the router port? Actually, this is the easier way than telling every server to listen on a different port. Using router port translation, that is.
This is a dedicated server with a hosting company so I have no access to the router.
Ok. That means you are doing the best you can by going to a high port, but the hosting company might block other ports, including the port you've selected.

> * Are you running fail2ban on something similar that needs a configuration change for the new port? BTW, you SHOULD be running fail2ban.
You've just taught me something new here. It is not installed, but I plan to do so now. Am going to investigate this further tonight.Yes. Fail2ban rocks.  By default it handles ssh on port 22, so you'll need to configure it on the other port.

I think you are looking at blocked ports. Either on your network or at the ISP.  You'll probably need to open a support case with them.

---

### Post by miloSA on 2012-09-06
Have tried to telnet from my mac and got the following:
nodename nor servname provided, or not known

which I suspect is probably due to telnet not being installed.

I think you may be right about the blocked ports at the hosting company. I will raise a case with them. Have installed fail2ban in the meantime, and you're right, it rocks! Am now trying to figure out how to best setup the graphs, etc as displayed on their site. A suggestion is to use RRDTool, so more homework for me ;)

Thanks again

---

### Post by TheFu on 2012-09-06
If you are using the public IP and telnet isn't working, that's bad.  Do you have a real computer ... running Linux?  Not a fan of Apple here, sorry.  I forced myself to try OSX for a week a few months ago.  It felt like Linux-Lite. It was painful to me, but I've been on X/Windows so long that select/paste is 2nd nature.   OSX is soooo close, but not quite there.  Anyway, for me, it was maddening.

Graphs from fail2ban? Interesting.  I use logwatch across the 30-ish servers I run. No pretty graphs, but it does get to the important stuff to my email daily.

For performance monitoring, I use SysUsage. The "enterprise grade" solutions were simply too much hassle to setup across all the nodes for me.  SysUsage provides all the same stats **and** pretty graphs without all that hassle.  My performance server pulls the graphs a few times daily, but I really should just grab the rrd files and build the graphs locally for each machine.  Getting the data off the host is important. If there's an issue, the data is needed for analysis.  However, if I were starting again, I'd look at **monitorix**.

For centralized management, I use cssh and ssh with some scripting, but I'm really looking hard at Rex [http://rexify.org/](http://rexify.org/) .  I like that it doesn't require an entire new ecosystem be installed to work like Puppet demands.  Some of these system config management solutions seem worse than the problem.  OTOH, my problem level isn't as large as many other companies.

---

