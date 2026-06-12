---
title: "Newsreader help"
date: 2010-01-12
forum: General Help
---

### Post by phreakn001 on 2010-01-12
Hello,

Im looking for some help with using a news reader to connect to a newsgroup.  Im a total newb to news group but I have followed all the troubleshooting guides on the news server provider astraweb.  

I have tried to connect with Lottanzb, Pan Newsreader and SABnzbd.  No sucess.  The error I keep getting is failed to connect.  I have checked my user name and password several times, bypassed my router and changed the port.

Not sure what other info I could provide to get help with this but any links to information on this would be much appreciated.

---

### Post by gsmanners on 2010-01-12
This site is good for stuff like that: [http://www.slyck.com/Newsgroups_Guide](http://www.slyck.com/Newsgroups_Guide)

Some of those apps you might need Wine to run.

---

### Post by michy99 on 2010-01-12
Are you able to connect to a free news server? Your ISP may have one that provides limited groups.(Most no longer carry binary groups.) If you can, then the problem is with astraweb. I assume you have paid for a subscription, so you should try to get help from their customer support.

---

### Post by phreakn001 on 2010-01-12
> **gsmanners said:**
> This site is good for stuff like that: [http://www.slyck.com/Newsgroups_Guide](http://www.slyck.com/Newsgroups_Guide)

Some of those apps you might need Wine to run.

thanks i will check that out.

> **michy99 said:**
> Are you able to connect to a free news server? Your ISP may have one that provides limited groups.(Most no longer carry binary groups.) If you can, then the problem is with astraweb. I assume you have paid for a subscription, so you should try to get help from their customer support.

i tried my ISP news server and couldnt connect to it either.  the customer support kind of sux at astraweb.

thanks for the info guys... im going to keep trying. patience is truly a virtue

---

### Post by phreakn001 on 2010-01-16
Ok made some progress on this.  It appears that my iptable rules are blocking me.  I tried to ping yahoo.com and I get a "destination port unreachable" error.  I did some google searching on this and found the following command to flush the iptable rules ```
iptables -F
```  after running this I try to ping again and it works.

Immediately upon doing this i fire up my newsreader and try to connnect to the news server.  Success!  However, after a few minutes I lose my connection with the server and it goes back to the old cannot connect message. I then open up a terminal and try to ping yahoo.com again and i get "destination port unreachable" again.  My guess is the iptables are reseting.  So my thinking is that I need to prevent the refresh or add a rule to allow traffic.

Im a newb and dont know much about iptables but here is the output of ```
sudo iptables -L
```

```

brad@brad-laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
blockcontrol_in  all  --  anywhere             anywhere            state NEW mark match !0x14 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
blockcontrol_fw  all  --  anywhere             anywhere            state NEW mark match !0x14 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
blockcontrol_out  all  --  anywhere             anywhere            state NEW mark match !0x14 

Chain blockcontrol_fw (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            mark match 0xa 
RETURN     all  --  anywhere             192.168.1.1         
RETURN     all  --  192.168.1.0/24       192.168.1.0/24      
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 92

Chain blockcontrol_in (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            mark match 0xa 
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  192.168.1.0/24       anywhere            
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 92

Chain blockcontrol_out (1 references)
target     prot opt source               destination         
REJECT     all  --  anywhere             anywhere            mark match 0xa reject-with icmp-port-unreachable 
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  anywhere             192.168.1.1         
RETURN     all  --  anywhere             192.168.1.0/24      
RETURN     tcp  --  anywhere             anywhere            tcp dpt:https 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:www 
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 92


```

Can anybody interpret the problem by looking at this?  Or help me out with the code to allow traffic on port 119.

TIA

---

