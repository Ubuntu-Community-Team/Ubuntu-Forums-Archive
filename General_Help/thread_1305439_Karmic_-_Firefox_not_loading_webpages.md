---
title: "Karmic - Firefox not loading webpages"
date: 2009-10-29
forum: General Help
---

### Post by keaotix on 2009-10-29
Hey guys,
I've upgraded to 9.10 from 9.04 (everything in 9.04 worked perfectly this morning)

Basically firefox won't load web pages,  it just times out.  Otherwise I have full network connectivity,  I'm able to ping sites. (this is on my home network by the way)

The weird thing is that this problem only seems to exist on my home network.  I've been going through my router settings all morning, there is nothing I can find that suggests it's blocking HTTP traffic.  

Any ideas?

---

### Post by Giblet5 on 2009-10-29
Can you open a terminal window and post the output of ```
ifconfig
```

---

### Post by keaotix on 2009-10-29
Thanks for the reply.


output of ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:23:8b:14:bb:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:32 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:a4:fe:90  
          inet addr:192.168.1.196  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5dff:fea4:fe90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:381221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:705822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36339824 (36.3 MB)  TX bytes:1034660032 (1.0 GB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5D-A4-FE-90-61-34-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by jen1963 on 2009-10-30
I'm having the same !@#$%^ issue with Firefox under Karmic too. Web pages just DON'T want to load.
I multi boot between 9.04, 9.10 and Debian Testing and only 9.10 has the Firefox issue.
GGGGGGGGGGRRRRRRRRRR
:x

---

### Post by mikeyy on 2009-10-30
I'm also having this problem.  Firefox won't load any pages.  Actually it does, but Firefox takes more than 5 min to load Google's homepage or any page for that mattter.

---

### Post by keaotix on 2009-10-30
Thanks for the replies guys,  good to know I'm not the only person having an issue :D  I've done some more testing. Switched Modems and Routers (that I know work) still no luck.  Ran a Virtual Machine within 9.10, with IE (yuck!) and all works fine :(.    @mikeyy, Yes I have the same issue with google :(

---

### Post by jen1963 on 2009-10-30
The bug is in Firefox!
I downloaded FF 3.5 from Mozilla and had the same problem.
Opera, Konq and other browsers worked fine.
This Firefox bug almost makes me wish for IE under Ubuntu!!
Until FF under 9.10 is fixed I'll stay with 9.04.
Seems 9.10 isn't one of Canonicals best releases. 9.10 is buggy and crashes like Windows! Certain features and settings present in earlier releases are also missing. My Debian TESTING partition has fewer issues then 9.10!
I'm sure M$ is  gonna love 9.10 Karmic...It's LOUSY compared to prior releases!
:x

---

### Post by lovinglinux on 2009-10-30
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

### Post by keaotix on 2009-10-30
> **lovinglinux said:**
> See **Solution** [*[COLOR=Red]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005").

Thanks mate, I've reverted back to 9.04.  If any of the other guys are still using 9.10, can you please give it a shot and let me know if it works?  Thanks in advance.

---

### Post by jen1963 on 2009-10-30
Those fixes didn't work for me either. I'll go back to 9.04 as well.
Think of it this way...Karmic 9.10 is gonna be the best advertisement Microsoft has had in a while because of the poor quality control on Canonical's part.
Canonical really blew it with Karmic. Bad timing with Win 7 just out too...
:x

---

### Post by mikeyy on 2009-10-30
Thanks for the help but the fixes didn't work.  I'm reverting back also.

---

### Post by broncosis on 2009-10-31
well wow are you guys quick to bash 
I bet you would have given MS more time to sort it out 

not only that how much did you pay for 9.10 
I don't remember how much my last windows cost me 
but I bet it was more than 100x what I paid for 9.10 

and I have never paid for firefox either as this is 
the only issue I have seen in karmic so far 
and a reload or 2 has brought my pages up typically 
I haven't found it so painful 

give them a week at least before you say that MS has a new add 
I am yet to see them advertise against Ubuntu directly and really 
they don't do much bashing of other os's at all really 
Mac does the most OS bashing in public 

so before you guys close your minds and get all anti linux (open source) 
think about the nature of the project your using the cost of developing it and giving it away if you don't like the bugs the break open the code and fix them or wait quietly until someone else does 
don't trash talk the people that give you things for free 

/rant 

I have been having a similar issue and it seems to clear itself with a reload or 2

---

