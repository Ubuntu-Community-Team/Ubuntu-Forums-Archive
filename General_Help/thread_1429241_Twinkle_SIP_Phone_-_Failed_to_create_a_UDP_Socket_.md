---
title: "Twinkle SIP Phone - Failed to create a UDP Socket (SIP) on port 5060 Address alrea.."
date: 2010-03-13
forum: General Help
---

### Post by Seithe on 2010-03-13
I can't seem to get on my Twinkle SIP Phone, it says: "Failed to create a UDP Socket (SIP) on port 5060 Address already in use" after that message it brings me back to the window were I'm supposed to run my profile, how do I fix this?
--------
Pictures of the problem:
[IMG]http://i43.tinypic.com/x3zcrp.jpg[/IMG]
--------
Pictures of the problem (2)
[IMG]http://i40.tinypic.com/1zq4ti9.jpg[/IMG]

---

### Post by dcstar on 2010-03-13
> **Seithe said:**
> I can't seem to get on my Twinkle SIP Phone, it says: "Failed to create a UDP Socket (SIP) on port 5060 Address already in use" after that message it brings me back to the window were I'm supposed to run my profile, how do I fix this?


Then you probably already have another SIP app installed and running, you need to find it and remove/disable it.

---

### Post by Joachim49 on 2010-04-28
Hi,

I've got exactly the sameproblem on my computer.
Twinkle is already launched when I try to click on a phone number in a webpage. Is this the problem?

I iniatially tried to use Ekiga but then removed it. How can i check that there is not another application running on port 5060?

Thanks.

Joachim

---

### Post by autosuggested on 2010-05-08
Hi Joachim,

Try opening a terminal and typing in the following. ```
netstat -anp | grep 5060
```

It should show you the process that's currently using port 5060. Something like this:

```
user@host:~$ netstat -anp | grep 5060
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
udp        0      0 192.168.1.41:5060       0.0.0.0:*                           1778/ekiga
```      

// Dave

---

### Post by agkrish on 2010-06-08
[FONT=Courier New][SIZE=3]Hi 

I have the same issue and ran netstat and got result as in the attached image.

what do i do now  to set twinkle right ?

am trying for a long time to use a softphone on Ubuntu but unable to do so. Is it because this installation of Lucid Lynx is a dual boot with Windows Vista   ?

thanks
GK
Lucid Lynx 10.04
HP Pavilion dv5-1050ee
AMD Turion X2 Ultra 64 bit

[/SIZE][/FONT]

---

### Post by Topazgb on 2011-01-11
sudo nmap -sS -sV -O -p- -PI -PT 192.168.1.2
Showed me what was using the port
(nmap is in the software centre.  Your IP may be different)

SIP Expess Router was using the port

Not sure if it installed when I installed a windows softphone on wine ? 

I just unistalled SIP Expess Router and Twinkle connected

Unfortunately sound did not work on Twinkle so I installed SLFphone with full success

---

### Post by Topazgb on 2011-01-11
sudo nmap -sS -sV -O -p- -PI -PT 192.168.1.2
Showed me what was using the port
(nmap is in the software centre.  Your IP may be different)

SIP Expess Router was using the port

Not sure if it installed when I installed a windows softphone on wine ? 

I just unistalled SIP Expess Router and Twinkle connected

Unfortunately sound did not work on Twinkle so I installed SLFphone with full success

---

