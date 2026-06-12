---
title: "whats using internet ?"
date: 2011-09-16
forum: General Help
---

### Post by flipper T on 2011-09-16
when not using browser, lights on wireless router still showing activity.

how can i find out which apps are causing this ?

---

### Post by pastalavista on 2011-09-16
> **flipper T said:**
> when not using browser, lights on wireless router still showing activity.

how can i find out which apps are causing this ?

Open a terminal and enter```
netstat
```


also Ububtu One runs by default...

---

### Post by LMP900 on 2011-09-16
Do you have any cloud services installed e.g. Dropbox, Ubuntu One, etc.? It also could be mail, social applications, or update checks.

---

### Post by RyanRahl on 2011-09-16
```
netstat
```

is a usefull but you can get a faster output from

```
ss
```

but my favorite for real time monitoring is

```
iptraf
```

and

```
top
```

can provide you with an easier to read process activity monitor to better help determine what is running and what is connected

otherwise you could use

```
ps
```

for this

---

### Post by flipper T on 2011-09-16
no drop box or ubuntu one, but did have banshee running.

tried netstat but columns not wide enough to read. can i dump it to a text file.

i guess my main concern is others using the bandwidth. its all password protected, but how do i know for sure? i have a measly bandwidth cap, so of some importance.

---

### Post by 3rdalbum on 2011-09-16
The lights on the router will flicker because there's constant little pieces of data going backwards and forwards from computer to router. These are "keep alive" packets - the router is checking that the computer is still there, and vice-versa.

What you want to check is System Monitor and see the actual datarate of what's going inwards and outwards.

---

### Post by hakermania on 2011-09-16
EDIT: 3 secs quicker [3rdalbum]("http://ubuntuforums.org/member.php?u=61044") from me :P
It could also be only communication between router and your PC.
Me too have this type of packets coming and going but WireShark (a sniffer) says that the Source is localhost and Destination is 192.168.1.1 or vice versa, so no fears for me...

---

