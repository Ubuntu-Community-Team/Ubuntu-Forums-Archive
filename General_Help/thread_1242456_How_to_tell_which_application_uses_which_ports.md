---
title: "How to tell which application uses which ports"
date: 2009-08-17
forum: General Help
---

### Post by moody_mark on 2009-08-17
Out of curiosity I ran a port scan on my own IP. I have ssh open (port 22) but I also noticed a connection to various random port numbers using tcp to "ten.mydomain.com"

```
netstat -a | grep 37344
tcp        0      0 ten.mydomain.com:37344  ten.mydomain.com:37344 TIME_WAIT
```

I noticed that this connection is using different port numbers all the time. Im not worried about malware as its likely something like the toolbar weather update etc. However how can I map a port back to an application?

---

### Post by nikhilk on 2009-08-17
> **moody_mark said:**
> However how can I map a port back to an application?

Use the -p option of netstat which also lists the PID of the process using the port.

---

### Post by moody_mark on 2009-08-17
Thanks, but it seemed in this case it still didnt show the process ID

```
sudo netstat -p | grep 46271
[sudo] password for curtis: 
tcp        0      0 ten.mydomain.com:46271  ten.mydomain.com:46271  TIME_WAIT   -   
```  

Any other switches I can use for netstat? Im not really that strong on netstat, yes I did try reading the man page too, thats why im asking for help :-)

---

### Post by moody_mark on 2009-08-17
I also tried "lsof" but that doesnt bring anything back

```
lsof -i :47464

```

---

### Post by nikhilk on 2009-08-17
Can you see this "weird" process in the output of
```
ps ax
```

---

### Post by Brandon Williams on 2009-08-17
A socket in the TIME_WAIT state has already been orphaned, which means that it is not attached to a process any longer. Run 'sudo netstat -anp' when you have an active socket and you will see that the name of the process does show up, along with the pid.

---

### Post by moody_mark on 2009-08-18
> **nikhilk said:**
> Can you see this "weird" process in the output of
```
ps ax
```

No, it does bring back information, but nothing that relates to the port number, its really strange, like the open port is constantly changing

---

### Post by moody_mark on 2009-08-18
> **Brandon Williams said:**
> A socket in the TIME_WAIT state has already been orphaned, which means that it is not attached to a process any longer. Run 'sudo netstat -anp' when you have an active socket and you will see that the name of the process does show up, along with the pid.

This is all I get from that

```
$ sudo netstat -anp | grep 60884
[sudo] password for curtis: 
tcp        0      0 192.168.0.15:60884      192.168.0.15:60884      TIME_WAIT   
```

Its like the port is not attached to a process, is this correct?

---

### Post by moody_mark on 2009-08-19
Any other idea on this folks?

---

### Post by Bachstelze on 2009-08-19
```
sudo fuser -n tcp port_number
```

---

### Post by moody_mark on 2009-08-19
this process seems to be opening up and changing port number rapidly, i get no results from the fuser command

```
curtis@Homer:~$ sudo fuser -n tcp 38669
curtis@Homer:~$ sudo fuser -n tcp 60529
curtis@Homer:~$ sudo fuser -n tcp 48782
curtis@Homer:~$ sudo fuser -n tcp 50693
curtis@Homer:~$ sudo fuser -n tcp 38601
curtis@Homer:~$ sudo fuser -n tcp 38601
```

how I could trace this?

---

### Post by Brandon Williams on 2009-08-19
> **moody_mark said:**
> This is all I get from that

```
$ sudo netstat -anp | grep 60884
[sudo] password for curtis: 
tcp        0      0 192.168.0.15:60884      192.168.0.15:60884      TIME_WAIT   
```

Its like the port is not attached to a process, is this correct?

As I said in my previous comment, netstat can't tell you the process if the socket is in TIME_WAIT, because the socket has already been orphaned. Are you saying that you _never_ see these strange sockets when they are in ESTABLISHED state? If that's true, then you will have a very difficult time figuring out which program is doing it. The only thing I can think of is to selectively stop running processes and watch for these connections to stop being opened.

---

