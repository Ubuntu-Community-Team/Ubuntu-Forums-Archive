---
title: "Limiting # of threads launched by a script"
date: 2011-03-06
forum: General Help
---

### Post by terminator14 on 2011-03-06
I have a script that basically takes a list of IP addresses, and pings them to tell me if each device (Access Point) is online or not.

The problem with that is, the list contains about a hundred addresses. Making the problem worse is the fact that using a single ICMP packet per device is not an option since, at certain times of the day, the network is too congested to guarantee that a single ICMP packet won't be dropped, despite the device being up and running. That means I need to send multiple pings per device for about a hundred devices. As you can imagine, doing this sequentially takes a while.

What I want to do is make my script open other threads in the background to ping multiple devices in parallel. The problem with that is - if I simply make each ping command run in parallel, soon there are a hundred background tasks, one for each address, and that consumes a lot of CPU (CPU hits 100% and stays there till the script is done).

Is there a way I can make about 10 threads run at a time, and any other threads will queue until a spot opens up for them? Kind of like the token bucket, except when there aren't enough tokens, the main script waits until it can launch more background threads that ping the next addresses on the list.

I've attached my script (net_scanner_v5.sh), and a failed attempt to make it multithreaded (net_scanner-ng.sh). Any advice would be appreciated.

---

### Post by mimor on 2011-03-06
This is not an answer to your question but you might find it awesome:
[https://hackerspace.be/Pamela](https://hackerspace.be/Pamela)

---

### Post by terminator14 on 2011-03-06
> **mimor said:**
> This is not an answer to your question but you might find it awesome:
[https://hackerspace.be/Pamela](https://hackerspace.be/Pamela)

If I understand correctly what the Pamela project is, it's not quite what I'm looking for.

To simplify my problem a little, here's a basic example:

```
#!/bin/bash
for i in $(seq 1 30)
do
        sleep 30 &
done

```

This script would quickly launch 30 background processes and exit. How would I have it only run 10 background processes at a time instead? Basically, the script would start new background processes until there are 10, and then it will pause and wait until one of the background processes exits, at which point the script will run more background processes until there are 10 running at any one time again.

---

### Post by terminator14 on 2011-03-08
After playing around with the code, I finally have a quick and dirty fix:

```
#Counts threads
iCount=0

#Read file
for i in $(seq 1 30)
do
        #Check how many threads are running
        while [[ true ]]
        do
                iCount=$(ps -Af | grep sleep | grep -v grep | wc -l)
                if [[ "$iCount" -ge 10 ]]
                then
                        sleep 1s
                else
                        break
                fi
        done

        sleep 30 &
done

#Only exit script once all children return
while [[ true ]]
do
        iCount=$(ps -Af | grep sleep | grep -v grep | wc -l)
        if [[ "$iCount" == 0 ]]
        then
                break
        else
                sleep 1s
        fi
done

```

I've also attached an updated version of my net_scanner-ng.sh script to show how the above gets translated into the script.

Is there a cleaner, better way to do this? Would that way be more complex? The way it is now, any ping commands running alongside the script would mess with it - by which I mean the script won't even exit unless the system is not running ANY pings - not just the ones the script started.

---

