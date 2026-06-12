---
title: "Conflicting Port Scan Results"
date: 2010-04-18
forum: General Help
---

### Post by nmaster on 2010-04-18
I just ran the port scanner from the Network Tools utility a few times within a few minutes (see screenshots).  How can  there be different ports open each time? I know that port 631 is for CUPS, but what about the other ones?  

Could someone help me understand what is going on, or at least point me in the direction of some good information?  I am definitely a newbie when it comes to networking so any help would be appreciated.

EDIT:
'sudo nmap -O localhost' only shows 631 as being open.  I ran it a few times to be sure.

---

### Post by 3rdalbum on 2010-04-18
Are you running a Bittorrent client? Are you sure you don't have Transmission-daemon installed?

---

### Post by nmaster on 2010-04-18
> **3rdalbum said:**
> Are you running a Bittorrent client? Are you sure you don't have Transmission-daemon installed?

i'm very sure.  i don't really torrent stuff much.

EDIT:
if I nmap my external IP address, it doesn't show any open ports.  I've done it several times.  if i nmap localhost it only shows the cups port (631).  why does the gui show more open ports and why is it not consistent?

---

### Post by nmaster on 2010-04-19
bump.

any ideas about the difference between the gui and nmap?

---

### Post by lavinog on 2010-04-19
It could be at the moment that you are checking, some program is opening a port for a short period of time.

Try netstat to see what is opening the ports.
```

netstat --numeric --programs --inet


```

---

### Post by nmaster on 2010-04-19
the only things that show up are skype and firefox.  since firefox is a default program, i doubt that its the problem.  could it be skype?


```

$ sudo netstat --numeric --programs --inet
[sudo] password for neal: 
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 10.10.208.198:51593     74.125.19.147:443       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:33019     198.189.255.81:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:43791     74.125.19.18:443        ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:43776     74.125.19.18:443        ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:33022     198.189.255.81:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:49828     198.189.255.73:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:33024     198.189.255.81:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:34756     74.125.19.104:80        ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:33020     198.189.255.81:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:60522     72.14.213.100:80        ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:33021     198.189.255.81:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:49795     173.88.243.113:9412     ESTABLISHED 3682/skype      
tcp        0      0 10.10.208.198:33023     198.189.255.81:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:58223     198.189.255.75:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:41170     198.189.255.89:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:44890     74.125.19.19:443        ESTABLISHED 3998/firefox    


```

---

### Post by Ryan Dwyer on 2010-04-19
Any software on your machine that talks to another one needs to open a port. When you make a HTTP request, for example, your machine will open a high numbered port temporarily so it can receive the response from the server.

At the moment you did the port check your system had some high numbered ports open. It's nothing to be concerned about.

---

### Post by lavinog on 2010-04-19
> **neal.m.master said:**
> the only things that show up are skype and firefox.  since firefox is a default program, i doubt that its the problem.  could it be skype?


```

$ sudo netstat --numeric --programs --inet
[sudo] password for neal: 
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 10.10.208.198:51593     74.125.19.147:443       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:33019     198.189.255.81:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:43791     74.125.19.18:443        ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:43776     74.125.19.18:443        ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:33022     198.189.255.81:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:49828     198.189.255.73:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:33024     198.189.255.81:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:34756     74.125.19.104:80        ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:33020     198.189.255.81:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:60522     72.14.213.100:80        ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:33021     198.189.255.81:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:49795     173.88.243.113:9412     ESTABLISHED 3682/skype      
tcp        0      0 10.10.208.198:33023     198.189.255.81:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:58223     198.189.255.75:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:41170     198.189.255.89:80       ESTABLISHED 3998/firefox    
tcp        0      0 10.10.208.198:44890     74.125.19.19:443        ESTABLISHED 3998/firefox    


```

If firefox was running when you did the initial checks, then it would be firefox.

Notice the port numbers that firefox is showing:
for example: 10.10.208.198:**58223**, the number in bold is the port number.

---

### Post by nmaster on 2010-04-21
thanks for the explanation!  i guess i need to do some reading about this stuff.  i didn't know that different processes use ports to talk to each other.

---

