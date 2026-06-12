---
title: "CPU temp and fan control PLEASE HELP ME!!!"
date: 2010-02-15
forum: General Help
---

### Post by lkthornton on 2010-02-15
Hi, I have used Ubuntu 9.10 on my previous desktop computer with absolutely no problems whatsoever. I have now installed 9.10 as primary OS on my Toshiba Satellite L30-10X Laptop. 

My problem is that when the laptop is idleing, the CPU temperature raises steadily from 56 degrees celcius until it reaches 70 and the fan kicks in, bringing it back down to 56. This process happens constantly every 2 minutes and is rather frustrating becuase I love Ubuntu but cannot stant this cycle. 

I am using gkrellm to monitor the CPU temp. Can someone please explain why my cpu temp keeps raising, triggering the fan at 70 and cooling, and raising etc constantly even though idleing? And does anyone have a solution? I would be ever so grateful!!!

Thanks in advance, Lee
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8830632")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8830632")

---

### Post by mörgæs on 2010-02-16
There are some bugs in 9.10 regarding the processor overheating on portable PC's, for example
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)

Some workarounds are in this thread, or you could try to add "acpi=off" as the boot parameter. Updating the BIOS might work, but I can not promise...

Probably the best bet is a clean install of 9.04
[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

I hope this helps...

---

