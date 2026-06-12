---
title: "Omnibook module does not load on Maverick"
date: 2010-12-23
forum: General Help
---

### Post by dukerussian on 2010-12-23
Hi folks,

I own a Toshiba Satellite L305D and it has the infamous overheating issues (fan does not turn on). In the past, this problem was resolvable by installing the omnibook module. (As per here: [http://swinky-linuxblog.blogspot.com/2008/11/ubuntu-on-toshiba-satellite-l305-howto.html](http://swinky-linuxblog.blogspot.com/2008/11/ubuntu-on-toshiba-satellite-l305-howto.html))

I recently upgraded from Lucid to Maverick and, unfortunately, I cannot get the omnibook module to load.
Downloaded latest source:
sudo git clone git://omnibook.git.sourceforge.net/gitroot/omnibook/omnibook

sudo make (compiles with a few warnings)
sudo make install
sudo depmod -a
sudo modprobe omnibook ectype=11
hangs 

The last few lines of strace output are:
14983      0.000179 nanosleep({0, 100000000}, NULL) = 0
14983      0.100385 open("/sys/module/omnibook/initstate", O_RDONLY) = 3
14983      0.000300 fstat(3, {st_mode=S_IFREG|0444, st_size=4096, ...}) = 0
14983      0.000261 mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fdd65e27000
14983      0.000193 read(3, "coming\n", 4096) = 7
14983      0.000229 close(3)            = 0
14983      0.000178 munmap(0x7fdd65e27000, 4096) = 0
14983      0.000429 nanosleep({0, 100000000}, NULL) = ? ERESTART_RESTARTBLOCK (To be restarted)
14983      0.012859 --- SIGINT (Interrupt) @ 0 (0) ---
14983      0.000442 +++ killed by SIGINT +++


This is a serious issue as the fan won't turn on without the omnibook module and without the fan the machine gets up to about 100C, overheats and turns itself off.

Any ideas?

---

