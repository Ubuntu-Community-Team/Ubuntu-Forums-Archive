---
title: "no virtual terminals on Ubuntu 9.10"
date: 2010-01-05
forum: General Help
---

### Post by igor.R on 2010-01-05
Hello, Hello, everybody.

I have a problem - after installation of Ubuntu 9.10
I discovered that I do not have virtual terminals on my 
computer.
When I am trying to switch, to another virtual
terminal with, say, Ctr-Alt-F2, I am getting a black 
screen with lonely cursor blinking in the upper left 
corner (no login prompt).

my tty2.conf file is


```
# tty2 - getty                                                                  
#                                                                               
# This service maintains a getty on tty2 from the point the system is           
# started until it is shut down again.                                          

start on runlevel [23]
stop on runlevel [!23]

respawn
exec /sbin/getty -8 38400 tty2
```

Does anybody know why this does not work?

What should I do to make virtual 
terminals to work on my machine by default?
What config file should I change

Also I cannot find inittab file.
Where is it? 

what file tells to execute tty#.conf on ubuntu?

PS: removing splash as someone suggested on the Internet 
did not help.


/etc/default/console-setup file has line

```

ACTIVE_CONSOLES="/dev/tty[1-6]"
```



If I start in the safe mode - can not login to my computer
because I do not have a login prompt.

Any ideas, please how to fix this. Virtual terminals
worked before. I did not edit any configuration files,
so I do not know what happened - why they don't work now.

---

### Post by wasd591 on 2010-01-05
Do you have any information on the machine? And could you also run a
```
lsb_release -a
``` command and copy it in the reply?

---

### Post by igor.R on 2010-01-05
> **wasd591 said:**
> Do you have any information on the machine? And could you also run a
```
lsb_release -a
``` command and copy it in the reply?

Here it is, please...


```
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

```


Machine is a Thinkpad w500 with ATI videocard



processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T9600  @ 2.80GHz
stepping	: 10
cpu MHz		: 2801.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 5585.48
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T9600  @ 2.80GHz
stepping	: 10
cpu MHz		: 2801.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 5585.95
clflush size	: 64
power management:



Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009

I think it is a regular desktop/laptop version


I can connect to the Internet.

---

### Post by wasd591 on 2010-01-05
Did you try and reboot the computer. You may also need to reset the terminal. Just give me a minute and let me find more information on that topic.

---

### Post by wasd591 on 2010-01-05
Goto your GUI screen with Xcode (**Ctrl + Alt + F7**) and press **Alt + F2**.
Then copy this in:
```
xterm
```
It should open a terminal window.
Now use this command after logging in to the root user. If you don't have the root account activated, you log in with your normal account and type in:
```
sudo -i
```
Type in your password again and you have root access.
To re-install terminal type in:
```
sudo apt-get install --reinstall gnome-terminal
```
And reboot the computer after that.

---

### Post by igor.R on 2010-01-05
> **wasd591 said:**
> Did you try and reboot the computer. You may also need to reset the terminal. Just give me a minute and let me find more information on that topic.

Yes, I rebooted several times, tried to uninstall
some packages (some package broke the system, 
I had virtual terminals couple of days before) - 
removed splash screen in /boot/grub/grub.cfg and 
rebooted again - it did not help.

---

### Post by igor.R on 2010-01-05
> **wasd591 said:**
> Goto your GUI screen with Xcode (**Ctrl + Alt + F7**) and press **Alt + F2**.
Then copy this in:
```
xterm
```
It should open a terminal window.
Now use this command after logging in to the root user. If you don't have the root account activated, you log in with your normal account and type in:
```
sudo -i
```
Type in your password again and you have root access.
To re-install terminal type in:
```
sudo apt-get install --reinstall gnome-terminal
```
And reboot the computer after that.

Just tried - it did not help. Same problem persist.

---

### Post by igor.R on 2010-01-05
```
ps -ef | egrep 'tty[1-6]' 
```


does not output anything


So this is the problem - why getty processes do not run automatically after reboot (tty#.conf files look normally).
Why getty processes don't start.

---

### Post by el_txavo on 2010-01-24
I have the same problem. At least I can start them up manually with:
```
sudo start tty1
...
sudo start tty6
```
Now the problem is keyboard layout, which is wrong: it should be PC-105 ES (Spanish).

---

