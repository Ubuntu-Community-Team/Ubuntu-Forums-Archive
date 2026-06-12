---
title: "Using a proxy in bash"
date: 2006-02-07
forum: General Help
---

### Post by lifeperfecti0n on 2006-02-07
Hi all,
    I am facing a wierd problem with bash. I CAN use Synaptic, Firefox, ProzGUI, aMSN and other software which use the Internet, but only their GUI versions. apt-get, aget, cvs, gcvs, wget, prozilla (all such programs u can think of) do NOT work in bash. I always get the error 'Host not found' when they attempt to open any link. I have tried exporting the http_proxy environment variable in bash but no change. Please note that I use the internet behind an ISA server with static IP. For all these progs I also tried configuring the proxy internally but this also did not work. I have given up on it...
Any suggestions:confused:
The most absurd thing is-why can't I use apt-get if Synaptic is perfectly working????

---

### Post by lifeperfecti0n on 2006-02-12
Update:
It seems that i have to declare the proxy in conf files of each program. apt-get and wget worked in this way. Since every program is developed in different languages, it would be much more convenient if the bash COULD use a proxy
Btw I checked in Configuration Editor and the proxy has been declared there.
I would love to use cvs to download Cedega's source so please reply soon.:-?

---

