---
title: "DHCP problem"
date: 2006-01-23
forum: General Help
---

### Post by Leigh on 2006-01-23
Do you have enough available IP addresses set in the DHCP server?  I ask this as we had a similar problem at work but with our wired PCs - we didn't have enough IP addresses. Extending th scope solved the problem.

What is the make & model of your DHCP gateway device?

---

### Post by Leigh on 2006-01-23
Well, I've no idea how that happened, but my response seems to have come before your question!!

What I was going to add was that you might try this [troubleshooting guide for wireless devices]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide"). It may give a clue as to what might be worng.

---

### Post by pharmdad2007 on 2006-01-23
That is weird how your replies showed up before my question.  Anyway, I do have plenty of IP addresses.  I have 9 available IP addresses and only 1 is used on a regular basis.  My DHCP device is a wireless DSL modem/router, the model is Actiontec GT701-WG.  I will take a look at that guide you pointed me to in the meantime.
Thanks,
Jesse

---

### Post by pharmdad2007 on 2006-01-23
Hi there,
I have a wireless network set up at home, and I have successfully used ndiswrapper to configure my wireless card and connect to the network. However, I can only connect if I enter a static IP on my laptop, even though my wireless gateway is set up for DHCP. When I try to connect using DHCP, it will connect to the network, but never get an IP address. So I am perfectly happy with using a static IP, but the problem is this: I want to connect to the wireless network at school as well, but they don't allow you to use a static IP, so in order to connect there I need to get this DHCP problem solved. I think there must be some communication problem between my laptop and the DHCP server, but I don't know what it is. Any help would be greatly appreciated!
Thanks in advance,
Jesse

---

### Post by pharmdad2007 on 2006-01-24
Update:

Using the wireless troubleshooting guide that Leigh directed me to, I have been able to get an IP address and connect through my home router.  The command that got things to work was

sudo invoke-rc.d networking restart

My question is this:  am I going to have to do this everytime I restart my computer, or is there some way to have this automatically happen each time?  Also, what exactly does this command do?
Thanks in advance,
Jesse

---

### Post by pharmdad2007 on 2006-01-24
Update:

Using the wireless troubleshooting guide that Leigh directed me to, I have been able to get an IP address and connect through my home router.  The command that got things to work was

sudo invoke-rc.d networking restart

My question is this:  am I going to have to do this everytime I restart my computer, or is there some way to have this automatically happen each time?  Also, what exactly does this command do?
Thanks in advance,
Jesse

---

