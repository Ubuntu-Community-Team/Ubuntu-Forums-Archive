---
title: "open /dev/null failed: no such file or directory"
date: 2010-06-21
forum: General Help
---

### Post by rajmahendra on 2010-06-21
when i restart my Ubuntu 10.4 i am getting this error while booting and its shows login screen!

udevd-work[324]:  open /dev/null failed: no such file or directory

any remedy ?

---

### Post by sjinks on 2010-06-21
sudo mknod -m 666 /dev/null c 1 3

---

### Post by rajmahendra on 2010-06-21
Strange. the command says 

mknod: `/dev/null': File exists

---

### Post by rajmahendra on 2010-06-22
anyone know what the problem in this ?

---

### Post by m.capurso on 2010-06-25
I have the same experience.
It started when I inserted and extracted a wifi pcmcia card while the 
computer was running.
At the next reboot I had the message.

I found here 

[http://forum.openvz.org/index.php?t=msg&goto=39012&&srch=ubuntu#msg_39012](http://forum.openvz.org/index.php?t=msg&goto=39012&&srch=ubuntu#msg_39012)

something that make me think that the package udev is the culprit.
Udev adds and removes dinamically devices in the /dev directory, when they
are inserted and removed.
These are personal observations.
Now, what to do ?
I will continue to search !

---

### Post by Steve Francis on 2010-07-14
I have the same problem with 10.04.

_ *Sometimes*_ when I boot up, I get the message:

[FONT=Courier New]udevd-work[324]:  open /dev/null failed: no such file or directory[/FONT]

before the boot up sequence continues.

The number in square brackets usually changes on the next reboot. What does this number mean?

In my case, the problems started after a kernel upgrade.

Is there any progress on finding a solution?

---

### Post by sjinks on 2010-07-14
> What does this number mean?

udev-work's process id aka PID.

---

### Post by bodhi.zazen on 2010-07-14
> **Steve Francis said:**
> I have the same problem with 10.04.

_ *Sometimes*_ when I boot up, I get the message:

[FONT=Courier New]udevd-work[324]:  open /dev/null failed: no such file or directory[/FONT]

before the boot up sequence continues.

The number in square brackets usually changes on the next reboot. What does this number mean?

In my case, the problems started after a kernel upgrade.

Is there any progress on finding a solution?

If it is kernel specific (old kernels work) report it as a bug.

If you computer still works normally, ignore the error message. If you are having problems, use the old kernel while awaiting a bug fix.

---

### Post by Steve Francis on 2010-07-14
> **bodhi.zazen said:**
> If it is kernel specific (old kernels work) report it as a bug.

If you computer still works normally, ignore the error message. If you are having problems, use the old kernel while awaiting a bug fix.

I didn't have the problem until the new kernel was installed BUT then it occurred when booting into the old kernel too.

I found the following so it looks as though the bug has already been reported?...
[https://bugs.launchpad.net/ubuntu/+bug/575333](https://bugs.launchpad.net/ubuntu/+bug/575333)

The computer seems to work normally but boot up is delayed so it is an irritation that I'd like to remove at some point.

---

### Post by Steve Francis on 2010-07-14
There seems to be a workaround summarised here:
[http://forum.openvz.org/index.php?t=msg&goto=39012&&srch=ubuntu#msg_39012](http://forum.openvz.org/index.php?t=msg&goto=39012&&srch=ubuntu#msg_39012)

Unfortunately, I'm not Linux-literate enough to understand how to implement that solution.
(Makedev?...)

---

### Post by manolomanolo on 2010-07-15
Same problem here.

Any suggestion, please? Thanks.

---

### Post by samloyd on 2011-04-07
The same problem here:

udevd-work[<number>]:  open /dev/null failed: no such file or directory

I have a system with two 250GB hard disks ATA SAMSUNG SP2504C, ubuntu 10.04 and WindowsXP.

In the internet I see several places where the same question is asked, but no convincing answer is given. (There is neither any CD nor any floppy in the way when I boot my system.) 

ubuntu gives the above message, waits for about half a minute - and starts. I don't know if the message means anything serious but did not find any defect when using my system, apart from the fact that the floppy drive is not recognized (a floppy in the floppy drive is "not existent" for ubuntu - but it is for Windows). I don't think, however, that this floppy behavior has to do with the message.

Does anybody know how to get rid of the error message?

---

### Post by bodhi.zazen on 2011-04-07
> **samloyd said:**
> Does anybody know how to get rid of the error message?

First you need to understand this message is from the kernel, and thus the cause of the problem is going to vary from kernel to kernel. Using an older or newer kernel may be the best option.

The kernel is maintained at [http://www.kernel.org/](http://www.kernel.org/) and you will get limited if any support here (due to the complexity of kernel programming).

You first need to determine if the error message is coming from your initrd , and if so rebuild the initrd (and include /dev/null).

If not from your initrd, it is then coming from the kernel. So download the kernel source code and patch it =).

You would need to post a whole lot more information then an error message for us to write a patch for you, and that kind of highly technical / specialized information is probably best posted on LP or on the linux kernel mailing list rather then the Ubuntu forums.

[http://www.kernel.org/](http://www.kernel.org/)

If you did not understand that or if you have no clue where to start, report it on Launchpad and they will likely say it is an "upstream bug" meaning a kernel problem.

If all that seems like too much effort, considering the system boots normally, I would not give it a second thought.

---

### Post by samloyd on 2011-04-11
Thank you, bodhi.zazen, for this friendly reply. As you may have suspected, I am not a Linux expert. But I have been using Linux for about 15 years... (mostly SuSE, but came to ubuntu two years ago), and I learn slowly but steadily! I am grateful for the help and patience of numerous personal and anonymous friends whose time is devoted to Linux work so much more than mine. [I try to be active similarly, but in a rather different area...]
Your remarks tell me that the problem might involve more knowledge than I have in this moment, but also that it is not fatal, it does not look serious. But be sure I am after it - and even if it is only for understanding more about kernel messages and the initrd.
I think it is just fair to give a response about the state of affairs to a kind answer; thank you.

---

### Post by bodhi.zazen on 2011-04-11
> **samloyd said:**
> Thank you, bodhi.zazen, for this friendly reply. As you may have suspected, I am not a Linux expert. But I have been using Linux for about 15 years... (mostly SuSE, but came to ubuntu two years ago), and I learn slowly but steadily! I am grateful for the help and patience of numerous personal and anonymous friends whose time is devoted to Linux work so much more than mine. [I try to be active similarly, but in a rather different area...]
Your remarks tell me that the problem might involve more knowledge than I have in this moment, but also that it is not fatal, it does not look serious. But be sure I am after it - and even if it is only for understanding more about kernel messages and the initrd.
I think it is just fair to give a response about the state of affairs to a kind answer; thank you.

You are welcome.

With your experience you could probably work through the error / build a custom kernel, but, it would take a bit of reading on your part ...

Knowing what I do of kernel building, for a non-fatal error I would not take the time to debug it.

---

