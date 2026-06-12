---
title: "Ubuntu Server/Desktop Dual Boot"
date: 2009-11-02
forum: General Help
---

### Post by intermentals on 2009-11-02
I would like my system to have a dual boot between the Server and Desktop editions of Ubuntu. However when I install them, whichever one was last installed, is the one that boots giving me no choice.

Please help!

---

### Post by zzzBrett on 2009-11-02
Why are you attempting to dual boot Server and Desktop?  You know you can run the server applications in Ubuntu desktop?

To get both listed on the bootloader, GRUB might need some configuration because it sounds like it is not auto-detecting both.  Are you sure you are installing them on separate partitions and not overwriting the previous?

Also, what version of Ubuntu are you using?

---

### Post by destroyedlolo on 2009-11-02
It's exactly a response to your question, but the solution I choose was to configure sever or desktop at init level.

By default, it's starting as server (because it's the default usage for my machine), the ... 
```
sudo init3
``` and the desktop is loading.
After, you have to play w/ startup/shutdown scripts but it save lot of disk space.

Hopping it helps.

---

### Post by intermentals on 2009-11-02
It's version 9.10 (32 bit)

I'm installing both as, in work we are currently using OpenBSD 4.4 and I want to move over to Ubuntu Server - however before I do so I want to set it up on my laptop to make sure I can make it work as it's supposed to on there before touching the main set up. I have Desktop installed at the moment for my own use.

During the installation I'm selecting the run side by side option so I don't think that it's just overwriting.

I am new to UNIX servers but am learning quite quickly and have an intermediate to advanced understanding of computers/programming.

@ destroyedlolo - could you please provide a little more detail about what's required and what scripts I'll have to edit/how to edit them

@ zzzBrett - how do I run the server applications in Desktop mode please?

Thanks so much for your help guys, I'm a bit lost with all this.

---

### Post by zzzBrett on 2009-11-02
What applications do you want to run?  A web server? MySQL server? FTP Server?

---

### Post by destroyedlolo on 2009-11-04
> **intermentals said:**
> 
@ destroyedlolo - could you please provide a little more detail about what's required and what scripts I'll have to edit/how to edit them

You have to have a look on the documentation about runlevel, init.d and rc*.d

The default runlevel is 2 so is corresponding to your default environment.
Then put your alternative environment for another runlevel (let say ... 3).

You can manage content of your runlevel using **sysv-rc-conf tool**.
You can switch from one to another using **runlevel** command.

Hoping it's helping.

Best regards,

Laurent

---

### Post by fela on 2009-11-04
> **intermentals said:**
> I am new to UNIX servers but am learning quite quickly and have an intermediate to advanced understanding of computers/programming.

You're not running a UNIX server. Linux != UNIX. Just a clarification.

---

