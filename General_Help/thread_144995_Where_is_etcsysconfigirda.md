---
title: "Where is /etc/sysconfig/irda ?"
date: 2006-03-15
forum: General Help
---

### Post by icebite on 2006-03-15
I'm trying to set up IrDA on my laptop, and I need access to the file that is  placed in /etc/sysconfig/irda on other distro's.

Where can I find /etc/sysconfig/irda equivalent in Ubuntu?

These are the parameters I need to set:
IRDA=yes
DEVICE=irda0
#DEVICE=/dev/ttyS2
#DONGLE=actisys+
DISCOVERY=yes

---

### Post by mlind on 2006-03-15
does irda *irda-utils* or *toshset* (for Toshiba laptop) provide configuration
file for irda?

---

### Post by icebite on 2006-03-15
I have both toshset & irda-utils installed. toshset does not provide any irda support that I can see. irda-utils is just a set of tools to get hardware adress of irda & such, what I understand. I already know the hardware info about my IR device and want to set it up so that it works. I am trying to follow these advices written for a non-debian system (step 3 is the one I need help with);

1. Download tosh1800-smcinit and install from [http://irda.sourceforge.net/smcinit/](http://irda.sourceforge.net/smcinit/) (you will need pciutils-devel for this)
2. Install setserial if it is not installed
3. Edit your /etc/sysconfig/irda

IRDA=yes
DEVICE=irda0
#DEVICE=/dev/ttyS2
#DONGLE=actisys+
DISCOVERY=yes

4. add these lines to your modules.conf
install smsc-ircc2 /usr/local/sbin/tosh1800-smcinit -s 0x3e8 -f 0x130 -m 3 -i 7 -x 0x5a -c 0x4e; /sbin/modprobe --ignore-install smsc-ircc2
pre-install smc-ircc2 /bin/setserial "/dev/ttyS2" "uart" "none"
options smc-ircc2 ircc_fir=0x130 ircc_sir=0x3e8 ircc_irq=7 ircc_dma=3
alias irda0 smsc-ircc2
5. start irda

---

### Post by mlind on 2006-03-15
have tries using irtty_sir driver that's provided by ubuntu kernel?

here's an article [http://www.softlab.ece.ntua.gr/~amanous/Inspiron-Linux/](http://www.softlab.ece.ntua.gr/~amanous/Inspiron-Linux/)
which contains instructions how to setup this module.

---

### Post by icebite on 2006-03-16
Thanks for answer!

I followed the instructions on the page you linked to, then I used

irattach /dev/ttyS1 -s

to start up IR. Now I at least get some info when I start irdadump (earlier nothing was shown when starting irdadump!):

10:58:27.014119 xid:cmd 172664ac > ffffffff S=6 s=0 (14)
10:58:27.104095 xid:cmd 172664ac > ffffffff S=6 s=1 (14)
10:58:27.194075 xid:cmd 172664ac > ffffffff S=6 s=2 (14)
10:58:27.284074 xid:cmd 172664ac > ffffffff S=6 s=3 (14)
10:58:27.374050 xid:cmd 172664ac > ffffffff S=6 s=4 (14)
10:58:27.464036 xid:cmd 172664ac > ffffffff S=6 s=5 (14)
10:58:27.554036 xid:cmd 172664ac > ffffffff S=6 s=* toshiba hint=0400 [ Computer ] (23)

But this does not seem to be correct! I should be able to see the changes with irdadump when I hold my mobile phone with IR turned on against the IR sensor on my laptop, but it just keeps repeating the info above..

---

