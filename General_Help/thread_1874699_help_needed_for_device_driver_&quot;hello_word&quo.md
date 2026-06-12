---
title: "help needed for device driver &quot;hello word&quot; program"
date: 2011-11-03
forum: General Help
---

### Post by just_abhi22 on 2011-11-03
hi all
i am trying to learn device drivers.
there, i am executing standard hello.c file using make file. it gets executed successfully but after i do **sudo insmod ./hello.ko,** it doesnt give me the any output, whereas the desired output was "hello world"....this is happening both in ubuntu inside vmware or ubuntu installed on fresh partition. i could file any output on log files as well. why this is happening?? my ubuntu version is 11.10.

kindly solve my query as soon as possible.

---

### Post by WorMzy on 2011-11-03
Where are you checking for output? Have you checked dmesg?

---

### Post by just_abhi22 on 2011-11-03
as per book Linux device driver-3, Jonathan corbet, Alexander rubini, they say that after compiling **hello.c** using make file, then writing **insmod ./hello.ko** should show me "Hello World" on my screen. when i ask for **rmmod hello**, it should give "Goodbye cruel world".....
but i am getting blank screen after execution and control comes out of it and shows me my command prompt. why???

---

### Post by WorMzy on 2011-11-03
How old is the book? I don't think I've ever seen a kernel module print to stdout when inserted, except perhaps when booting in verbose mode.

Check dmesg.

```
dmesg
```

---

### Post by just_abhi22 on 2011-11-03
book is 3-4 years back (2007), 3rd edition of Linux Device Drivers.
any how,your suggestion worked fine but i am getting lot other outputs as well and at the very bottom i get the message as "hello word". how to remove other messages that are not required here??

how to set path for my header files present at different locations in same main program: say most of my header files lies in /lib/modules/3.0.0-12-generic/build/include/linux, so in my program i would say as # include <linux/module.h>
if i have some other header file present at some other location, say: /lib/modules/3.0.0-12-generic/build/include/config, now how to connect header file available here to the same main program?? would writing #include<config/config.h> in main program works??

could you suggest me any book on device drivers that is good enough to take me from basics to considerable height. i want to learn this subject in detail.

---

### Post by WorMzy on 2011-11-03
You don't need to clear the contents of dmesg, it just contains the messages from the kernel (printk). I would assume that any kernel modules you write will only ever need to output information to assist with debugging any problems, your average user won't ever need to see them. If you want to write something that the user interacts with, you should consider writing a normal C application instead.

As for what you can use to learn how to write modules, I can't offer any advice in that area. It can't hurt to continue reading the book you're currently reading; I don't think kernel development has changed *that* much in the last five years, so most of the information in there should still be relevant.

Oh, and yes, I would assume that your include statement would work.

---

### Post by just_abhi22 on 2011-11-04
i want to seen only "hello word" as output when i write dmesg. now,lot messages are comminf from kernel and at last of all,i receive "hello word". i am inserting module as sudo and then dmesg.

any ways, thank you for your help.

---

### Post by WorMzy on 2011-11-04
I don't understand. Why do you only want to see the "Hello world" message? Your module isn't the only one in the kernel, so there will always be other messages in dmesg.

If you really want to only see your messages, run

```
sudo dmesg --clear
```

before using insmod. Assuming that no other modules need to tell you anything in the meantime, your module's message will be the only one there when you read dmesg.

---

### Post by just_abhi22 on 2011-11-04
thanks for you reply. i well understood things now.

---

