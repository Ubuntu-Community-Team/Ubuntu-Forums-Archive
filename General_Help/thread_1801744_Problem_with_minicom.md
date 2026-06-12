---
title: "Problem with minicom"
date: 2011-07-11
forum: General Help
---

### Post by masali on 2011-07-11
Hi, 
I have a problem with minicom. Although i seem to have the communication parameters matching, i get a question mark whenever i press enter or other character. Any help is appreciated.

---

### Post by An Sanct on 2011-07-11
Could you please elaborate a little bit more on your issue?

What kind of input device is this "minicom"? In what application are you trying to use it?

Are you trying to input Unicode/UTF-8 data into a non Unicode input field?

---

### Post by masali on 2011-07-11
> **An Sanct said:**
> Could you please elaborate a little bit more on your issue?

What kind of input device is this "minicom"? In what application are you trying to use it?

Are you trying to input Unicode/UTF-8 data into a non Unicode input field?
Minicom is a text-based modem control and terminal emulation program for Unix-like operating systems, 
I am trying to communicate with a hardware device through my serial port. On the older version of linux, things worked fine. However, on linux 10.10 I cannot establish communications. 
My serial port are installed as shown below:
dmesg|grep 8250
[    3.192041] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.192132] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

---

### Post by masali on 2011-07-11
Question is the serial port on linux 10.10 named ttys0 or tty0. I tried both in my minicom seting, but none worked. 
user@user-OptiPlex-780:~$ dmesg|grep 8250
[    3.192041] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.192132] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
user@user-OptiPlex-780:~$ ls /dev
autofs           ecryptfs  loop5               psaux  ram7    sg2       tty15  tty3   tty44  tty59    usbmon1  vcsa
block            fb0       loop6               ptmx   ram8    shm       tty16  tty30  tty45  tty6     usbmon2  vcsa1
bsg              fd        loop7               pts    ram9    snapshot  tty17  tty31  tty46  tty60    usbmon3  vcsa2
btrfs-control    full      lp0                 ram0   random  snd       tty18  tty32  tty47  tty61    usbmon4  vcsa3
bus              fuse      mapper              ram1   rfkill  sr0       tty19  tty33  tty48  tty62    usbmon5  vcsa4
cdrom            hidraw0   mcelog              ram10  root    stderr    tty2   tty34  tty49  tty63    usbmon6  vcsa5
cdrw             hidraw1   mem                 ram11  rtc     stdin     tty20  tty35  tty5   tty7     usbmon7  vcsa6
char             hpet      net                 ram12  rtc0    stdout    tty21  tty36  tty50  tty8     usbmon8  vcsa7
console          input     network_latency     ram13  scd0    tty       tty22  tty37  tty51  tty9     vcs      vga_arbiter
core             kmsg      network_throughput  ram14  sda     tty0      tty23  tty38  tty52  ttyS0    vcs1     zero
cpu              log       null                ram15  sda1    tty1      tty24  tty39  tty53  ttyS1    vcs2
cpu_dma_latency  loop0     oldmem              ram2   sda2    tty10     tty25  tty4   tty54  ttyS2    vcs3
disk             loop1     parport0            ram3   sda5    tty11     tty26  tty40  tty55  ttyS3    vcs4
dri              loop2     pktcdvd             ram4   sdb     tty12     tty27  tty41  tty56  uinput   vcs5
dvd              loop3     port                ram5   sg0     tty13     tty28  tty42  tty57  urandom  vcs6
dvdrw            loop4     ppp                 ram6   sg1     tty14     tty29  tty43  tty58  usbmon0  vcs7
user@user-OptiPlex-780:~$

---

### Post by masali on 2011-07-11
Thank everyone, no need for reply coz problem solved.

the serial port name is ttyS0

and I had to enter minicom -s 
then choose "exit minicom" NOT "exit"

and then enter minicom. However, i have to enter as root: sudo minicom.

then communications established.

---

### Post by An Sanct on 2011-07-11
Great :) Please mark this thread as solved, so others can benefit from your knowledge!

---

