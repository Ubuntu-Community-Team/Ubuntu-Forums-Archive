---
title: "Monitoring Temperature"
date: 2006-05-28
forum: General Help
---

### Post by nami on 2006-05-28
Hi

How do I monitor the temperature of my CPU?

nami

---

### Post by twotonz on 2006-05-28
Hallo,
If think the program that you are searching for is called lm-sensors. Firstly you must check that your hardware is supported. (not reccomended for Dell computers for example). To install do a search using synaptic.

Love & Peace to all
anthony

---

### Post by nami on 2006-05-28
Hi

Thanks for the reply

I have the following motherboard
MSI KT3 Ultra (MS-6380E)

How do I find out if lm-sensors supports my motherboard?

nami

---

### Post by twotonz on 2006-05-28
Hi,
[http://secure.netroedge.com/~lm78/](http://secure.netroedge.com/~lm78/)
Thats the homepage of the people that make lm-sensors, you need to know what chipset is on your board (a guess is kt333 but im really not sure) .
 I have just done a google search and found that you need ic2 (it shall be called i2c-2.7.0.tar.gz or something simular), but read this page first.....
[http://www.linuxforen.de/forums/archive/index.php/t-70437.html](http://www.linuxforen.de/forums/archive/index.php/t-70437.html)
 I do not have an msi board so I don't know them that well. hope this helps.

Love & Peace to all
anthony

STOP*********
Sorry, I have just read a bit further in the info's (must be bored!) and have read that if you are using a kernel>2.6 then you do not need the patch - it should work without any problems "out of the box" and for your board (if smoke starts pouring out of the computer, i take no liability ------only joking!)

---

### Post by nami on 2006-05-28
OK I got 2.6.12.10-k7

Here is some more info about my motherboard/chipset

Motherboard Name
MSI KT3 Ultra (MS-6380E)

Motherboard Chipset
VIA VT8367 Apollo KT333

Sensor Type
Winbond W83697HF  (ISA 290h)

I'm not sure if my sensor type is supported?

Any ideas?

nami

---

### Post by twotonz on 2006-05-28
Hi,
I guess everything is OK. I take it you have an AMD processor, in this case the k7 version is the right one.
lm-sensors gives you (or rather the kernel) the possibility to read the values from your board, to read these nicley in x you will proberly like to have a look at gktrellm or xsensors (in gnome) or ksensors (kde). Unfortuantly, I have a dell here, so I cannot have the luxury of sensors (correct me if i'm wrong someone), so I cannot give you much more info. I know I had gtkrellm running on suse, and I liked it a lot.

By the way, sometimes it takes me a while to reply (dapper, & trying everything out, which means that sometimes I am not online........oooopppps)

Love & Peace to all
anthony

---

