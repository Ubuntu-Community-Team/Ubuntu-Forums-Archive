---
title: "Ubuntu 11.04 doesn't boot with new kernels"
date: 2011-07-15
forum: General Help
---

### Post by deleter24 on 2011-07-15
My OS boots with 2.6.35-22-generic, if using more new kernels (2.6.38-8-generic, 2.6.38-10-generic and 3.0.0-0300rc7-generic), the system doesn't boot normally: the monitor doesn't light, upper and lower gnome panels are absent.

**Machine configuration: **Acer Aspire 5734Z, Intel Pentium Dual-Core T4500 2.3 GHz, 2 GB DDR3 Memory, videocard Mobile Intel 4(R) Series Express Chipset Family.

P.S. Excuse me for errors in the message: i'm from Russia =)

---

### Post by drpjkurian on 2011-07-15
Are you getting any error message?
If yes, Please post that message

---

### Post by deleter24 on 2011-07-15
No, because i don't see anything on my display: it isn't light

---

### Post by avernuss on 2011-07-15
I have a similar problem, and I have been trying to resolve it for the last 24h. 

I got a kernel update two days ago, didn't reboot right away, kept on working as usual and then turned the computer off. Afterwards, the system didn''t boot with either version of the kernel.
It just stops at some point while loading - I choose the kernel from grub, splash screen appears for a moment, then the screen goes black, a couple of lines appear and then it stops responding, the last line being either "Stopping  configure virtual netwok devices" or "Starting CUPS printing  spooler/server", no error message.


  I tried dabbling with recovery mode to reinstall kernel of various version (I got hundreds of them already), to no avail.
 I tired running failsafeX graphic mode. It returned the message "Ubuntu  is running in low-graphics mode. Your screen, graphic card and input  device settings could not be detected correctly. You will need to  configure these yourself". And, as you probably have already guessed,  I'm not able to do it. Also, "Run Ubuntu in low-graphics only in this session"  does nothing but return "Stand by one minute while display restarts".  Nothing changes afterwards.
When I choose "Resume normal boot" from the rescue mode, I can log in to  my account and basically work on it. I mean, I could work, if I wasn't  so dependent on GUI.

Right now, I'm on the verge of either reinstalling the whole system or throwing the computer out of the window. Please, if you can, save the life of this little Lenovo T61 (Intel Core 2 Duo, Intel express chipset family 965).

---

### Post by samigina on 2011-07-15
Similar symptoms here. Vaio cr220e, core 2 duo. Intel graphics.

---

### Post by avernuss on 2011-07-17
Hey guys, doesn't anybody know what to do about it? 
Mind you, by ignoring this thread you sentence us (or at least me) to using Windows, which is a terrible, terrible thing to go through.

---

### Post by deleter24 on 2011-07-18
I need old kernel (in particular, 2.6.35-22-generic) to boot the system. But my monitor goes black when I boot the OS using the new kernel (normal room light). But in bright light you can see the barely visible background and cursor. Upper and lower panels are absent. I think that my graphic card is not support more new kernel than 2.6.35-22-generic.

---

### Post by drpjkurian on 2011-07-19
Hi
I think you all guys have to stick on to old kernel for a while.,
To do so   

0. Boot from ubuntu 11.04 install disk and tell it I wanted to recover a system. 

1. Look in /boot/grub/grub.cfg to find the entry for the old kernel,

2.you have to edit the file /etc/default/grub and change the entry:    GRUB_DEFAULT=0 to the value where your old kernel 

3. run update-grub

4. Ctrl-D to exit the shell and reboot. It works!

---

### Post by deleter24 on 2011-07-19
Yesterday I solved this problem by typing "nomodeset" into the  /etc/default/grub, but I'm having a new problem: display resolution is  1024x768 instead of 1366x768, compiz isn't working.

---

### Post by UnnamedUzer on 2011-07-19
When i usually install new kernel, i also install new video drivers, because OS doesn't load. May be installation of new video drivers will solve the problem.

---

### Post by deleter24 on 2011-07-19
Now I'm downloading updates using synaptic. It includes xorg updates, video driver updates and kernel updates which necessary for my ubuntu.

---

### Post by avernuss on 2011-07-19
Doesn't work for me at all. :( I give up, gonna make a format. 
Thanks for the replies anyway.

---

