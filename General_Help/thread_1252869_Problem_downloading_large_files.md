---
title: "Problem downloading large files"
date: 2009-08-29
forum: General Help
---

### Post by Yvon T'lincher on 2009-08-29
Hi all:

I have a laptop with KUBUNTU 9.0.4 and a desktop with UBUNTU 9.0.4 - 64 bits and both exhibit the same behaviour: it is sometimes impossible to download large files (>500k) using kmail or Firefox. 

For example, a 500k .zip attatchement cannot be downloaded with kmail or Thunderbird; a 2Mb file cannot be downloaded with Firefox or any other browser (I have tried Conqueror, Epyphany, Seamonkey with the same results).

BTW, the same files download fine with Outlook and Chrome on XP.

I have checked AppArmor; stopping it does not solve the problem. NetFilter is inactive on both computers.

Any of you has encountered or has a solution for this problem?

---

### Post by NoaHall on 2009-08-29
It might be something to do with your router/ISP. They might not use the right ports.
try to install something from synaptic/apt-get and see what happens.

---

### Post by Yvon T'lincher on 2009-08-29
> **NoaHall said:**
> It might be something to do with your router/ISP. They might not use the right ports.
try to install something from synaptic/apt-get and see what happens.


Thanks for your prompt response.

I dont think that this is network related. I have just downloaded with Firefox the Ubuntu Pocket Guide, a 2 Mb zip file - no problem. As I said, this behaviour is (or seem to be) unique to Ubuntu. My other computers (XP, Win2000, CentOS) do not have this problem. Apt-get works fine...

---

### Post by Defrector on 2009-08-29
What is the nature of the failure? Does the download reach a certain percent then freeze? Any error messages?

After you perform the download attempt, type the following into your terminal:
```
ifconfig | grep "errors:"
```

and paste the results in a reply. This is to check if you are having some sort of driver issue with your network interface.

Some other questions:
Are you using wired ethernet or wireless?
If wireless, what is the model of your wireless card?
If wireless, are you using a WPA network?

The reason for this question is that my Atheros wireless seems to work fine unless put under a lot of heavy use, at which point its speed gets slower... and slower... and slower and the errors in ifconfig start piling up. If this is your case I believe it is a driver issue.

---

### Post by Yvon T'lincher on 2009-08-31
ifconfig reports:

TX packets: 63765 errors: 0 dropped: 0 overruns: 0 carrier:0
TX packets: 21347 errors: 0 dropped: 0 overruns: 0 carrier:0

The network works fine and is wired and WIFI capable but the WIFI driver is not loaded.

Very strange...

---

### Post by Yvon T'lincher on 2009-09-02
Many thanks to those that answered.

The issue has been solved by upgrading the router firmware (Linksys RV082 - 8ports dual wan router) as suggested by [binop]("https://answers.launchpad.net/%7Eubuntu-jacek") in [Launchpad]("https://answers.launchpad.net/ubuntu/").

---

