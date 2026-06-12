---
title: "jar file ubuntu x86 to arm or ppc"
date: 2010-03-25
forum: General Help
---

### Post by IdealVithVodka on 2010-03-25
Hello,


I've written an application (CLI) in java that does some network detection. I would like to port it to an arm or powerpc device/machine. I was just thinking if it would work without any problems since it will be a jar file. Also the program uses jpcap to access the network interface. So the second question would be : are jar files platform specific ?? Will it be possible to use the jpcap.jar file on the ported device ?

Also, is it possible to somehow emulate a ppc / arm machine on a ubuntu box ??


Thank You in advance

---

### Post by Chronon on 2010-03-25
I would think that as long as there is a properly implemented java virtual machine for the architecture then you won't have any problems.  I am not a java expert, however, so don't take that as authoritative.

I found some free ARM emulators here:
[http://www.thefreecountry.com/emulators/arm.shtml](http://www.thefreecountry.com/emulators/arm.shtml)

---

### Post by IdealVithVodka on 2010-03-26
Thank you for the prompt reply. Hmmmm... The jar cross-platform thing could be good news, but still like you said I need to confirm this somehow - tried to get some info via google but no luck. I was hoping to maybe get something like VirtualBox that could set the cpu type you want to emulate.

Any ideas anyone ?

---

### Post by Chronon on 2010-03-26
Did you check the page I linked?  VirtualBox won't work because it doesn't emulate a different architecture.  You need a real emulator instead for that.

---

### Post by IdealVithVodka on 2010-03-26
Yes, I've checked the link you gave me. I wanted to install for example debian arm/powerpc port (in the same way you install debian x86 via VirtualBox), but seems like that will be hard with the tools that are available.

---

