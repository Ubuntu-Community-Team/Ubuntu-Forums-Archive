---
title: "jaunty randomly locking up..."
date: 2009-07-15
forum: General Help
---

### Post by Darkoblivion2 on 2009-07-15
specs:

intel core 2 quad 9550
geforce gtx 260
1tb western digital hdd
8gb of kingston ram
jaunty 9.04 64bit

so every once and awhile, my ubuntu will freeze, but, i will be able to move the mouse pointer on screen a lil bit every 5 secs or so after the initial "lock up"

and it isnt just one thing that causes this... i have had it happen to me multiple times in firefox, and wow. and sometimes while im just doing some file management...

anyone experiencing these symptoms as well?

most of what i have googled, and searched on these forums says that its just jaunty...
is this true?

or is my problem more specific?

any replies would be appreciated!

thanx in advance!

---

### Post by tommcd on 2009-07-15
Is this a hard lockup, where nothing works, including the keyboard, and you have to push the power button to restart the system? Since you said "i will be able to move the mouse pointer on screen a lil bit every 5 secs or so..." it sounds like the system is just running very slow, and it is not a hard lockup. Is that correct?
Open a terminal and run the **top** command to see if any processes are maxing out the CPU.
Also, do you have the nvidia driver properly installed? In the terminal run:
```
glxinfo | grep -i direct
```
It should report:
```

bash-3.1$ glxinfo | grep -i direct
direct rendering: Yes

```
With such a new system, I would assume you have a sata hard drive. Is that correct? Or is it IDE?
Also, what chipset does your motherboard use?

---

### Post by Darkoblivion2 on 2009-07-15
direct rendering: Yes

sata hdd: yes

im running an intel core 2 quad 9550 64bit.

and yes its a hard lockup, i cant use the keyboard, and requires me to push the restart button

---

### Post by Darkoblivion2 on 2009-07-15
awww... any help? puhhhleeeeez!

---

### Post by tommcd on 2009-07-16
It is hard to diagnose a problem like this without more information. Even then it can be difficult.

What **chipset** does your motherboard use?

To look for the source of the problem, open a terminal and try reading through:
dmesg
/var/log/messages
/var/log/syslog
/var/log/Xorg.0.log
to see if there are any clues as to what is causing the problem. 
You may have to boot to recovery mode to read these files if the system keeps locking up.
Try running the system in recovery mode for a while. Do some file management. See if the system locks up in recovery mode. If the system does not lockup in recovery mode, but locks up when you boot normally, then it is possible that some driver or daemon is causing the lockup.

---

