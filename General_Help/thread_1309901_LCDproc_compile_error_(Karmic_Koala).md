---
title: "LCDproc compile error (Karmic Koala)"
date: 2009-11-01
forum: General Help
---

### Post by skooter on 2009-11-01
Following this guide, [http://www.mythtv.org/wiki/LCDproc](http://www.mythtv.org/wiki/LCDproc), I'm getting errors when compiling LCDproc. "Configure" runs without problems:
```
./configure --enable-drivers=all
```

Then when running "make" i get these errors:
```
make  all-recursive
make[1]: Entering directory `/home/mythtv/lcdproc-0.4.5-imon'
Making all in shared
make[2]: Entering directory `/home/mythtv/lcdproc-0.4.5-imon/shared'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mythtv/lcdproc-0.4.5-imon/shared'
Making all in clients
make[2]: Entering directory `/home/mythtv/lcdproc-0.4.5-imon/clients'
Making all in examples
make[3]: Entering directory `/home/mythtv/lcdproc-0.4.5-imon/clients/examples'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mythtv/lcdproc-0.4.5-imon/clients/examples'
Making all in headlines
make[3]: Entering directory `/home/mythtv/lcdproc-0.4.5-imon/clients/headlines'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mythtv/lcdproc-0.4.5-imon/clients/headlines'
Making all in lcdproc
make[3]: Entering directory `/home/mythtv/lcdproc-0.4.5-imon/clients/lcdproc'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mythtv/lcdproc-0.4.5-imon/clients/lcdproc'
Making all in metar
make[3]: Entering directory `/home/mythtv/lcdproc-0.4.5-imon/clients/metar'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mythtv/lcdproc-0.4.5-imon/clients/metar'
make[3]: Entering directory `/home/mythtv/lcdproc-0.4.5-imon/clients'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/mythtv/lcdproc-0.4.5-imon/clients'
make[2]: Leaving directory `/home/mythtv/lcdproc-0.4.5-imon/clients'
Making all in server
make[2]: Entering directory `/home/mythtv/lcdproc-0.4.5-imon/server'
Making all in drivers
make[3]: Entering directory `/home/mythtv/lcdproc-0.4.5-imon/server/drivers'
gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I./.. -I../..    -Wall -O3 -c irmanin.c
irmanin.c:27:44: error: ../../../libirman-0.4.1b/irman.h: No such file or directory
irmanin.c: In function &#8216;irmanin_init&#8217;:
irmanin.c:123: warning: implicit declaration of function &#8216;ir_init_commands&#8217;
irmanin.c:128: warning: implicit declaration of function &#8216;ir_default_portname&#8217;
irmanin.c:128: warning: assignment makes pointer from integer without a cast
irmanin.c:142: warning: implicit declaration of function &#8216;ir_register_command&#8217;
irmanin.c:152: warning: implicit declaration of function &#8216;ir_init&#8217;
irmanin.c:90: warning: unused variable &#8216;filename&#8217;
irmanin.c:89: warning: unused variable &#8216;j&#8217;
irmanin.c: In function &#8216;irmanin_close&#8217;:
irmanin.c:168: warning: implicit declaration of function &#8216;ir_free_commands&#8217;
irmanin.c:169: warning: implicit declaration of function &#8216;ir_finish&#8217;
irmanin.c: In function &#8216;irmanin_getkey&#8217;:
irmanin.c:185: warning: implicit declaration of function &#8216;ir_poll_command&#8217;
irmanin.c:186: error: &#8216;IR_CMD_ERROR&#8217; undeclared (first use in this function)
irmanin.c:186: error: (Each undeclared identifier is reported only once
irmanin.c:186: error: for each function it appears in.)
irmanin.c:189: error: &#8216;IR_CMD_UNKNOWN&#8217; undeclared (first use in this function)
irmanin.c:180: warning: unused variable &#8216;i&#8217;
make[3]: *** [irmanin.o] Error 1
make[3]: Leaving directory `/home/mythtv/lcdproc-0.4.5-imon/server/drivers'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mythtv/lcdproc-0.4.5-imon/server'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mythtv/lcdproc-0.4.5-imon'
make: *** [all-recursive-am] Error 2
``` 

Also I did:
```
sudo apt-get install libirman-dev

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libirman-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Help appreciated :)

---

### Post by skooter on 2009-11-05
I just realized (se this link: [https://bugs.launchpad.net/ubuntu/+source/lcdproc/+bug/153185](https://bugs.launchpad.net/ubuntu/+source/lcdproc/+bug/153185)) that lcdproc should work just by 
```
sudo apt-get install lcdproc
```

I tested by starting LCDd in one termial
```
sudo LCDd -f -r 4
```
... and lcdproc in another termial
```
lcdproc
```
But nothing shows up on the display. Also I tested with MythTV - but still no luck.

I've got the display working before in Feisty Fawn.

Using dmesg:
```
dmesg | grep lcd
```
... shows:
```
[  965.174972] lirc_imon: lcd_write: invalid payload size: 32 (expecting 8)
[  965.300065] lirc_imon: lcd_write: invalid payload size: 32 (expecting 8)
[  965.425160] lirc_imon: lcd_write: invalid payload size: 32 (expecting 8)
[  965.550754] lirc_imon: lcd_write: invalid payload size: 32 (expecting 8)
[  965.676776] lirc_imon: lcd_write: invalid payload size: 32 (expecting 8)
[  965.802755] lirc_imon: lcd_write: invalid payload size: 32 (expecting 8)
[  965.928755] lirc_imon: lcd_write: invalid payload size: 32 (expecting 8)
[  966.053814] lirc_imon: lcd_write: invalid payload size: 32 (expecting 8)
[  966.178907] lirc_imon: lcd_write: invalid payload size: 32 (expecting 8)
[  966.270060] lirc_imon: lcd_write: invalid payload size: 32 (expecting 8)
```

---

### Post by skooter on 2009-11-05
Ok, got it working! Found this thread: [http://ubuntuforums.org/showthread.php?t=1243179&page=3](http://ubuntuforums.org/showthread.php?t=1243179&page=3)

What I did:
```
sudo nano /etc/modprobe.d/lirc-imon.conf
```
... and entered the following into the file:
```
options lirc_imon display_type=1
```
... where 1 os for VFD. Use this command for more info
```
modinfo lirc_imon
```

Se above post for testing.

Thanks to... hmm myself! :P

---

### Post by red321 on 2009-11-05
And thanks from me too ! did a straight upgrade on my antec mythfrontend, from Jaunty to Koala and no VFD no remote, so thanks for this.

---

