---
title: "64-bit system with 8GB RAM. Memory issue"
date: 2010-02-11
forum: General Help
---

### Post by titansking on 2010-02-11
Hello All,

I am a newb to ubuntu. Not sure if this is the right place to post. Here is my problem:

My system config:

Intel i5 750 2.67ghz Quad Core CPU
8GB RAM (2GB x 4)
Seagate Barracuda 1TB HDD x 2
Nvidia GT220 1GB DDR3

I am sure my ram is more than enuf to run my system. But to my irony, when i do top, i see that 90% of my memory is being used up. However, there is very lil or no heavy CPU activity. Below is the output of my top:

top - 23:07:52 up  1:55,  2 users,  load average: 0.00, 0.06, 0.12
Tasks: 150 total,   1 running, 149 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.8%us,  1.0%sy,  0.0%ni, 95.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8185204k total,  7450500k used,   734704k free,    23028k buffers
Swap: 23976972k total,        0k used, 23976972k free,  6313932k cached

Can anyone tell me why do i have such heavy memory usage? 

Regards,
Titan

---

### Post by titansking on 2010-02-11
ok i found my answer here - [http://www.linuxatemyram.com/play.html](http://www.linuxatemyram.com/play.html)
sorry for the trouble guys.

---

### Post by audiomick on 2010-02-11
Hallo.
Has the computer been running for a while without being switched off?
I am not too solid on the details, but from what I have read, Ubuntu accumulates cache space over time. Your cache is showing something more than 6GB at the moment, and this is taken off the figure for free RAM.

As far as I have understood things, this is not a problem as such if the system is not showing any signs of a problem.

Maybe someone else who knows more about it can offer more info, or correct me if I am wrong.

edit: nice link, I hadn't seen that.

---

