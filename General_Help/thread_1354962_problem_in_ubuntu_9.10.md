---
title: "problem in ubuntu 9.10"
date: 2009-12-14
forum: General Help
---

### Post by taimur on 2009-12-14
hi
i got 16 serial com ports in my computer in 8.04.2 lts version it was working i change  some setting in /boot/grub/menu.list

and now i installed ubuntu 9.10

i didn't find menu.list in /boot/grub

so by default i got only 4 ports open and other 12 ports are not working

please do reply
thanks

---

### Post by cariboo on 2009-12-14
I can't help you with your problem of not seeing all the com ports, but have a look [here]("http://ubuntuforums.org/showthread.php?t=1345518"), for a grub2 tutorial.

---

### Post by taimur on 2009-12-16
Hi cariboo907 
thanks for your help but my problem is solved i just changed one line in /boot/grub/grub.cfg



### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 7531878b-616b-4edb-a492-5e59cf3cdd0d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=7531878b-616b-4edb-a492-5e59cf3cdd0d ro quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic


you will find this file in grub.cfg all you have to do just put 8250.nr_uarts=16 before ro quiet splash

like this......

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 7531878b-616b-4edb-a492-5e59cf3cdd0d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=7531878b-616b-4edb-a492-5e59cf3cdd0d 8250.nr_uarts=16 ro quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic

save and exit

now install apt-get install setserial

and reboot system

and check by typing dmesg | grep tty

and you will see all ports will work 
i got 13 ports it is showing me 13
like this

[    0.002042] console [tty0] enabled
[    0.806836] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.807371] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.807630] 0000:04:00.0: ttyS4 at I/O 0xd000 (irq = 20) is a 16550A
[    0.807725] 0000:04:00.0: ttyS5 at I/O 0xd100 (irq = 20) is a 16550A
[    0.807818] 0000:04:00.0: ttyS6 at I/O 0xd200 (irq = 20) is a 16550A
[    0.807911] 0000:04:00.0: ttyS7 at I/O 0xd300 (irq = 20) is a 16550A
[    0.808003] 0000:04:00.0: ttyS8 at I/O 0xd400 (irq = 20) is a 16550A
[    0.808096] 0000:04:00.0: ttyS9 at I/O 0xd500 (irq = 20) is a 16550A
[    0.808200] 0000:04:01.0: ttyS10 at I/O 0xd600 (irq = 19) is a 16550A
[    0.808295] 0000:04:01.0: ttyS11 at I/O 0xd700 (irq = 19) is a 16550A
[    0.808388] 0000:04:01.0: ttyS12 at I/O 0xd800 (irq = 19) is a 16550A
[    0.808481] 0000:04:01.0: ttyS13 at I/O 0xd900 (irq = 19) is a 16550A
[    0.808586] 0000:04:01.0: ttyS14 at I/O 0xda00 (irq = 19) is a 16550A
[    0.808679] 0000:04:01.0: ttyS15 at I/O 0xdb00 (irq = 19) is a 16550A

thanks :)

---

### Post by philinux on 2009-12-16
You need to make that minor change in /etc/default/grub at line #9.

Then run sudo update-grub.

grub.cfg should not be edited as it gets generated from other files.

---

### Post by taimur on 2009-12-18
what change should be done?

---

