---
title: "Ubuntu 12.04 Wireshark problem"
date: 2012-05-02
forum: General Help
---

### Post by anspectrum on 2012-05-02
Ive recently upgraded to 12.04 from natty and installed wireshark (1.6.7) through software center. When i start wireshark it opens up pretty ok but then after a couple of hundreds of packets captured it gets slowed down....slowed down to a point where it kind of seems to have stuck and not much one can do except kill the process. Ive tried version 1.4.2 as well (on 12.04) but no luck. This problem was not there when I was using 11.04 (natty). My hardware is DELL Latitude E6410, core i5 with 2 GB RAM.

I've to work with wireshark and if it is not operatable then I would have to revert back to previous ubuntu versions....Any help ...?

---

### Post by anspectrum on 2012-05-06
bump.:(

---

### Post by Drowz0r on 2012-05-06
I'm not sure if this is related but I'm having network issues with it too:

[http://ubuntuforums.org/showthread.php?t=1974462](http://ubuntuforums.org/showthread.php?t=1974462)

Empathy and other things can't connect whereby they were able to under 11.10.

---

### Post by smurphy on 2012-05-06
Regarding the networking stuff. I had (on a fresh install) to configure the network (fixed line) statically. the DHCP always failed (this on a Mac-Mini 2011). An upgrade from 11.04 to 11.10 to 12.04 didn't show that behavior.

Regarding wireshark - could you try wireshark out on the command-line ? tshark -i /dev/eth0 
It would tell you if it has something to do with the GUI or not.

---

### Post by anspectrum on 2012-05-07
Ive tried tshark.......and it works however, i notice a packet drop indicated by the program....here is a summary

-----------------------------------------------------------------------------------------

xxx@OS:~$ sudo tshark -w /home/xxx/Desktop/wwww -i eth0 
tshark: Lua: Error during loading:
 [string "/usr/share/wireshark/init.lua"]:45: dofile has been disabled
Running as user "root" and group "root". This could be dangerous.
Capturing on eth0
546401 ^C
[COLOR=Red]11281 packets dropped[/COLOR] :confused:

--------------------------------------------------------------------------------------

So I dont know what to make out of it.....but this behavior was not in 11.04 although I managed to generate traffic of thousands and thousands of packets per second.

Any thoughts.

---

### Post by smurphy on 2012-05-07
try to run tshark and limit the amount of traffic you want to capture. Like tshark -i eth0 -c 1000000 (Will capture 1 Million packets and terminate itself).

I have noticed, that in environments where there is lots of misalignment (usually on mirror ports), tshark drops quite a lot of packets. Nothing you can do about. It just didn't get enough to realign it when stopped. it is showing up more and more often though, as the network throughput gets up with time.

---

### Post by anspectrum on 2012-05-07
> **smurphy said:**
> try to run tshark and limit the amount of traffic you want to capture. Like tshark -i eth0 -c 1000000 (Will capture 1 Million packets and terminate itself).

I have noticed, that in environments where there is lots of misalignment (usually on mirror ports), tshark drops quite a lot of packets. Nothing you can do about. It just didn't get enough to realign it when stopped. it is showing up more and more often though, as the network throughput gets up with time.

Right. But on the other hand we have 11.04 (GNU version) or as a matter of fact MS that perform perfectly alright. I guess there is some thing with the kernel probably. Let's wait together.:popcorn:

---

### Post by anspectrum on 2012-05-28
> **anspectrum said:**
> Right. But on the other hand we have 11.04 (GNU version) or as a matter of fact MS that perform perfectly alright. I guess there is some thing with the kernel probably. Let's wait together.:popcorn:

](*,)

---

### Post by anspectrum on 2012-09-24
Hey,

Today I got lucky. Its not that I got the latest version of Wireshark working on Ubuntu 12.04.  But what I did was I installed Wireshark version 1.2.7 from Canonical site. I installed just two packages (Wireshark, Wireshark-common).

Now I can generate thousands and thousands of packets/ sec without in hangup of the application.

:guitar:

---

