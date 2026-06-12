---
title: "missing tty"
date: 2010-07-02
forum: General Help
---

### Post by conradin on 2010-07-02
Hi all, 
Im using lucid, and I have noticed only tty7 seems to work. Im logged into graphical mode right now. When I press ctrl+alt+F(number) 
it takes me to a cursor with nothing else. There, it will not let me log in, type anything or respond in anyway. I can swith back to tty7 with no problems. 

Whats going on here? how can i fix this?

---

### Post by dino99 on 2010-07-02
F2 & F3 should work

sudo dpkg --configure -a

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/575255](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/575255)

---

### Post by conradin on 2010-07-02
> **dino99 said:**
> F2 & F3 should work

sudo dpkg --configure -a

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/575255](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/575255)

Yes, They should work, all of them should work, however they do not. I tried the aforementioned code, it has made no change on my system. 

I'm pretty sure the terminals are part of the kernel. What is going on here?

---

### Post by conradin on 2010-07-03
Bump.
Upon further review, the recovery modes also do not work.
(I'm scared that if something happens to my system I'll have to re do everything. (or that this might already be the case))
I tried re-installing the coreutils, and other basic programs related to the terminal modules but have yet to have any success in fixing it. 

The bug ([https://bugs.launchpad.net/ubuntu/+s...el/+bug/575255](https://bugs.launchpad.net/ubuntu/+s...el/+bug/575255))
doesnt represent the total problem I'm having here. The ctrl+alt+F2 and other terminal windowing commands do not cause my system to lock up. Only the Terminals never show up. I just get a flashing cursor that never has a prompt. I can exit back to tty7 at any time with ctrl+alt+F7.

it was working 2-3 weeks ago. Is there anything I can do to help resolve this?

---

### Post by conradin on 2010-07-05
Bump

---

### Post by conradin on 2010-08-21
Ok, I re-installed my OS and no longer have the problem. I'll mark this as solved though Im not thrilled with it as a solution.

---

### Post by timeofmind on 2010-09-28
> **conradin said:**
> Ok, I re-installed my OS and no longer have the problem. I'll mark this as solved though Im not thrilled with it as a solution.

I have the same problem with my system. Ubuntu 9.10

I just installed the system a few weeks ago. I would rather find out the issue, rather than re-install the system everytime this happens.

---

