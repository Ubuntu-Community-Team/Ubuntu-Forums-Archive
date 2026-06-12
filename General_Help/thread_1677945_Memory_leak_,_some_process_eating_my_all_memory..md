---
title: "Memory leak , some process eating my all memory."
date: 2011-01-29
forum: General Help
---

### Post by sukhdeepsingh on 2011-01-29
Hola,

I have had a fresh install of Ubuntu 9.10 and installed some software after that.
Since third some, some process is eating half of my memory.
I have checked processes running in system manager but everything is normal.
Maximum is consumed by compiz which is about 26 mb, seems very normal.

I did restarted my computer several times, and in the start for 5 mins, its fine after that again my cpu fans runs at very fast speed and my one cpu is used up 95 % (I have dual core).
Please help me out, this invisible thing is driving me crazy.

I am attaching my htop screen shot (sorted by cpu %), now the cpu is not used by completely but fan is still struggling hard and fast.

[http://uploadpic.org/storage/originals/dn29eujsn3nun23jnsesdn2ff3.png](http://uploadpic.org/storage/originals/dn29eujsn3nun23jnsesdn2ff3.png)

Thanks a lot,

Sukhdeep Singh

---

### Post by gufide on 2011-01-29
sorry, I don't see memory leaks here

---

### Post by sukhdeepsingh on 2011-01-29
> **gufide said:**
> sorry, I don't see memory leaks here
Hi gufide,
Thats what i am saying. but fan is running harder than normal work.

I will post another htop, when the system is occupied again with that invisible process.

Thanks
SS

---

### Post by no2498 on 2011-01-29
try in a terminal free-m
may need to leave the - out free m

---

### Post by sukhdeepsingh on 2011-01-30
Hi no2498 and gufide,
I am attaching new htop and free -m results.
I have figured it out, there's a process called snort, but i dont know why its running and using 100% of my 1 cpu.

```

             total       used       free     shared    buffers     cached
Mem:          2003       1419        584          0        113        868
-/+ buffers/cache:        437       1566
Swap:         3153          0       3153

```

htop file
[http://uploadpic.org/storage/originals/fufseserdkdj2dfl2sfe2kjfud.png](http://uploadpic.org/storage/originals/fufseserdkdj2dfl2sfe2kjfud.png)

if its snort, then what is it associated with and how to kill it without further harm.
Cheers

---

### Post by P4man on 2011-01-30
This is snort:
[http://www.snort.org/](http://www.snort.org/)

It should not be installed by default, its a network sniffer.
To get rid of it, kill it first

```
sudo killall snort
```

then uninstall it

```
sudo apt-get remove snort
```

---

### Post by sukhdeepsingh on 2011-01-30
> **P4man said:**
> This is snort:
[http://www.snort.org/](http://www.snort.org/)

It should not be installed by default, its a network sniffer.
To get rid of it, kill it first

```
sudo killall snort
```then uninstall it

```
sudo apt-get remove snort
```

Thanks mate,
I think it was there, because I was using vpn, 
so does it mean , after un installing it, I wll not be able to use my vpn.

Thanks
SS

---

### Post by NightwishFan on 2011-01-30
Your mem seemed fine. This output says that you were only using 437mb.
```
-/+ buffers/cache:        437       1566
```

---

### Post by P4man on 2011-01-30
> **sukhdeepsingh said:**
> Thanks mate,
I think it was there, because I was using vpn, 
so does it mean , after un installing it, I wll not be able to use my vpn.

Thanks
SS

SHouldnt interfere with the VPN. But if you run the uninstall command, you will get a rather verbose output of snort's dependencies, that is the other packages that will be removed (because they depend on snort). I highly doubt that will include any VPN stuff, but see for yourself. You can always abort the uninstall if for some reason apt-get does want to remove your VPN stuff (in which case, please copy paste the output here).

---

### Post by mc4man on 2011-01-30
A leak would show increasing memory use, you should just keep on eye on for awhile.
In the sysstat package is pidstat, you could use that.
Ex.
```
pidstat -r -p [COLOR="Red"]XXXX[/COLOR] [COLOR="Blue"]60 100[/COLOR] >> mem.log
```

Replace red with the process id, blue with time between reports in sec's, # of reports respectively. just minimize the terminal, report in home folder 
This may show id if you don't happen to see in htop
ps -A |grep snort

---

### Post by sukhdeepsingh on 2011-01-30
> **P4man said:**
> SHouldnt interfere with the VPN. But if you run the uninstall command, you will get a rather verbose output of snort's dependencies, that is the other packages that will be removed (because they depend on snort). I highly doubt that will include any VPN stuff, but see for yourself. You can always abort the uninstall if for some reason apt-get does want to remove your VPN stuff (in which case, please copy paste the output here).

Cheers mate,
Its sorted , i removed snort, but i dont know if i have to use it later for some purpose, but amazingly its uses one cpu completely which is not good.
I am afraid if i install it again, this will happen again.

Thanks
SS

---

### Post by sukhdeepsingh on 2011-01-30
> **NightwishFan said:**
> Your mem seemed fine. This output says that you were only using 437mb.
```
-/+ buffers/cache:        437       1566
```

Ok, but I dont know how you see this, my 1st CPU processor was utilized 99%, when I was using nothing, so its has to do with usage but i dont know if its classified buffers/cache or not.

Any ways it was snort program, who was using all the memory, I removed it.

Thanks any ways,
SS

---

### Post by sukhdeepsingh on 2011-01-30
> **mc4man said:**
> A leak would show increasing memory use, you should just keep on eye on for awhile.
In the sysstat package is pidstat, you could use that.
Ex.
```
pidstat -r -p [COLOR=Red]XXXX[/COLOR] [COLOR=Blue]60 100[/COLOR] >> mem.log
```Replace red with the process id, blue with time between reports in sec's, # of reports respectively. just minimize the terminal, report in home folder 
This may show id if you don't happen to see in htop
ps -A |grep snort


Thanks mc4man,
Its a good advice and I will keep this info handy for future.

Any ways, I removed snort.

[FONT=Impact]Thanks any ways,[/FONT]
SS

---

### Post by P4man on 2011-01-30
You have no need for snort unless you are a hacker/network security kind of guy. If you are unsure, you definitely dont need it.

---

