---
title: "ctrl + alt + F1 ~ F6 does not display terminal"
date: 2012-02-07
forum: General Help
---

### Post by superfriend on 2012-02-07
Hi all, 

I updated my Ubuntu 10.04 Linux Kernel from 2.6.32-37 to 2.6.32-38, then I wanted to stop the X server and re-install the NVIDIA driver. I have two problems:

1:
None of Ctrl + Alt + F1 ~ F6 works:
the screen freezes when I try to switch to tty

I can feel that tty is running, because I can still type my username and password and even sudo reboot the system, just without seeing the terminal on the screen! 

2:
I tried to ssh from another computer, but I can't really stop /etc/init.d/gdm, I tried with:
sudo /etc/init.d/gdm
sudo service gdm stop
none of above could stop gdm, then I am not able to install NVIDIA driver. This is so weird, especially in problem 1 tty seems work in background!

Thanks in advance for your help!

Greetings,
sf

---

### Post by superfriend on 2012-02-07
> **superfriend said:**
> Hi all, 

I updated my Ubuntu 10.04 Linux Kernel from 2.6.32-37 to 2.6.32-38, then I wanted to stop the X server and re-install the NVIDIA driver. I have two problems:

1:
None of Ctrl + Alt + F1 ~ F6 works:
the screen freezes when I try to switch to tty

I can feel that tty is running, because I can still type my username and password and even sudo reboot the system, just without seeing the terminal on the screen! 

2:
I tried to ssh from another computer, but I can't really stop /etc/init.d/gdm, I tried with:
sudo /etc/init.d/gdm
sudo service gdm stop
none of above could stop gdm, then I am not able to install NVIDIA driver. This is so weird, especially in problem 1 tty seems work in background!

Thanks in advance for your help!

Greetings,
sf

I am back to post the solution (maybe not the best but works to me)
1. Enter the recovery mode of the current kernel version
2. go to "Drop to root prompt" (with or without network)
3. type: "init 2" to change the runlevel to 2, otherwise NVIDIA driver warns runlevel = 1 is risky ..
4. you will enter the normal tty now, type in user name and password.
5. reinstall NVIDIA driver
6. type: "/etc/init.d/gdm start"

Everything comes back to normal, and Ctrl + Alt + Fx works again. 

Greetings, 
SF

---

