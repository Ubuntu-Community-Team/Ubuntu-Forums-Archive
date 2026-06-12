---
title: "/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed"
date: 2010-02-20
forum: General Help
---

### Post by markp1989 on 2010-02-20
Im trying to setup pwm config on this computer so that the fans wont come on to loud. 

Motherboard is DFI lanparty JR p45-t2rs. there is pwm hardware, as i have used pwm config in arch on the same computer.

any pointers you can give me to get pwm control working on this pc?

thanks mark

edit: during sensors detect. im told that the it87 module is needed. but i cannot load it:

mark@torrentslave:~$ sudo modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.31-17-server/kernel/drivers/hwmon/it87.ko): Device or resource busy
mark@torrentslave:~$

---

### Post by remymarathe on 2010-06-26
I can't get you past pwmconfig, but the issue with it87 not loading is discussed here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246]("http://https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246")

The following post in there from Stefan Divjak worked for me, at least got it87 to load:

                 Detailed workaround if you are already  using grub2:
 - open /etc/default/grub
- insert GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
- save and close
- run update-grub
- reboot


I realize this is an old question and you've hopefully figured it out by now, but for anyone else who stumbles on this with the same problem.

---

### Post by shmatic on 2012-01-18
[FONT=Trebuchet MS][SIZE=2]Hi!
[/SIZE][/FONT][SIZE=1][FONT=Arial][/FONT][/SIZE]
[FONT=Trebuchet MS] if  [/FONT][FONT=Trebuchet MS][SIZE=2]pwmconfig gives you:

[B]There are no pwm-capable sensor modules installed
[/B]
You can get it working by loading the it87 module with the command:

[/SIZE][/FONT][INDENT][FONT=Trebuchet MS][SIZE=2]modprobe it87 fix_pwm_polarity=1[/SIZE][/FONT]
[/INDENT][FONT=Trebuchet MS][SIZE=2]
pwmconfig should work as expected.

[/SIZE][/FONT]

---

