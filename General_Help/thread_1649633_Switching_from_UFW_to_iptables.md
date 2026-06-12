---
title: "Switching from UFW to iptables"
date: 2010-12-20
forum: General Help
---

### Post by NertSkull on 2010-12-20
So I've used UFW for quite some time now and its been great.  But I'm thinking its time to take the plunge into iptables.  I want to start blocking repeated connections from IPs trying to brute force my SSH.

I've been reading up on iptables, and it doesn't seem too bad.  But I have a few questions I'm hoping people can help with.

1) If I've been using UFW, do I need to do anything special to switch to iptables.  I was just going to do "ufw disable".  But do I need to uninstall it, or something special.  Because even when I do ufw disable, there are still lines in the iptables talking about ufw.

2) regarding those lines, do I need to get rid of them?  Is there a way to revert the iptables back to default? These are the lines.

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination 
```

They don't really seem to be doing anything, but I don't know for sure.

3) I've read some things that the order of rules in the "chain" matters, but I don't fully understand it.  Does it just mean that whatever comes first within the chain takes precedence?  So does that mean that if I want to add a new rule, I can't just add it, but I have to make sure it gets listed in the right order?

4) I don't fully understand what these "chains" are either.  I can kind of understand the three main ones, INPUT, FORWARD and OUTPUT.  But then ufw seems to have added a lot of other ones.  What are those?  

5) again on chains, if I add a drop IP to the INPUT chain.  From my understanding it prevents it from connecting to you.  Do I need to put it in the forward chain also? Or just worry about the input chain to prevent connections to me.


I think thats it, if I can get a handle on those (especially #1) I think I can make the switch to iptables with the aid of various tutorials I've found.

Thanks everyone for helping

---

### Post by NertSkull on 2010-12-22
anyone?

---

### Post by NertSkull on 2011-03-30
I thought I'd bump one more time, its been a few months and I still haven't made the switch yet.

---

### Post by JKyleOKC on 2011-03-30
UFW is simply a front end to configure iptables, so you've been using iptables all along without knowing it.

For what you say you want, have a look at the "fail2ban" package. Also, if you want to maintain your iptables settings on your own, read up on the how-to documents about it. It has a command that will clear ALL of the rules in one fell swoop, which should be used whenever you want to make a drastic change; removing them one by one can lead you into race conditions if you remove a rule before removing all others that call for it. Most of the how-to documents in this area, and sample scripts, led me to lots of confusion -- but it's basically a confusing area. That's why things like UFW and FireStarter were created.

Fail2ban checks log entries, in the background, and when it finds repeated attempts to break into your system, creates a temporary iptables rule to reject the offending IP for 10 minutes (default time; you can change it). This is usually adequate to deter the attempt, but doesn't fill up your rule list with dozens of obsolete rules. When the time is up, fail2ban removes the rule.

As for your existing set of rules that appear to do nothing, that's because you've apparently not specified ufw actions that would fill them. Your observation that they do nothing is correct! Unless you are running services that would open ports for incoming traffic, there's no need to run ufw at all. Unlike some other systems, Linux keeps all ports closed by default, so all attempts to get in are rejected with no need for firewall action. 

Hope this helps a bit. The fail2ban package is in the repositories so you can install it through the Software Center or Synaptic.

---

### Post by JKyleOKC on 2011-03-30
Oops.. I didn't answer your specific questions!

The built-in chains are INPUT, FORWARD, and OUTPUT. The FORWARD chain is only used if your machine is acting as a router and forwarding packets to another machine or machines on your local network. Most personal systems don't do this, so only INPUT and OUTPUT are significant.

All incoming packets go through the INPUT chain before being accepted by the system. Its rules are evaluated in strict sequence and the first one that matches and specifies an action gets executed. In your list, the "actions" are the first portion of each rule, and they transfer the sequence to the other chain that's named there. The very first one says for all source and destination IPs, switch to the "ufw-before-logging-input" chain. Since that chain has no rules, the process goes back to the second rule in INPUT. This repeats for all of the rules in INPUT, never finding any action other than transferring to another chain. When the last rule in INPUT fails, the default action of ACCEPT is executed.

The OUTPUT chain works the same way, for packets that you want to send out of the machine. This is useful for blocking traffic from programs that attempt to "phone home" periodically, but as you've listed, it also winds up with the default ACCEPT and so sends all packets.

For your #1, just disable ufw and then do "sudo iptables -F" to flush all the rules that ufw added. If you then list the rules, you will see only the three built-in chains and no additional ones. This will leave you in exactly the same condition as now, just without the wheel-spinning list of sub-chains...

To manually block an IP, you can add it as the first rule in INPUT.

The fail2ban package creates its own set of sub-chains, on the fly, to do the banning.

Does this make things a bit less murky?

---

### Post by psrdotcom on 2011-09-17
When you add something in UFW it reflects in iptables too. So, there is no point in switching. What you have do is clear the UFW rules in iptables and add your own rules by using iptables command.

---

