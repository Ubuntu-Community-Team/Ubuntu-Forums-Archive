---
title: "extracting between strings from terminal"
date: 2009-08-06
forum: General Help
---

### Post by Kimeras on 2009-08-06
I want to use terminal to use the command "ping google.co.uk -c 1". With this command i then want to extract the latency (time=138ms) and only have it output the numbers between the = and ms.

I know this includes some use of grep, awk, a combination of the two or something else as well! but i'm having difficulty doing this.

```
ping google.co.uk -c 1 | awk '/time=.*/,/.*ms/'
```

I figured it would look something along these lines, any help would be appreciated :)

---

### Post by dcstar on 2009-08-06
> **Kimeras said:**
> I want to use terminal to use the command "ping google.co.uk -c 1". With this command i then want to extract the latency (time=138ms) and only have it output the numbers between the = and ms.

I know this includes some use of grep, awk, a combination of the two or something else as well! but i'm having difficulty doing this.

```
ping google.co.uk -c 1 | awk '/time=.*/,/.*ms/'
```

I figured it would look something along these lines, any help would be appreciated :)

**sed** is probably a better option.

---

### Post by kaibob on 2009-08-06
An alternative would be to obtain the data from a different line:

```
ping -c 1 google.co.uk | grep rtt | cut -d / -f5
```

or

```
ping -c 1 google.co.uk | awk -F "/" '/rtt/ { print $5 }'
```

I know little about the ping command, but the data from the rtt line appears to always be consistent with the data in the line you reference.

SAMPLE OUTPUT BEFORE PIPE
> $ ping -c 1 google.co.uk
PING google.co.uk (74.125.77.104) 56(84) bytes of data.
64 bytes from ew-in-f104.google.com (74.125.77.104): icmp_seq=1 ttl=49 time=163 ms
--- google.co.uk ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 163.985/163.985/163.985/0.000 ms

---

### Post by Kimeras on 2009-08-07
thanks kaibob, this does the job perfectly! :)

---

