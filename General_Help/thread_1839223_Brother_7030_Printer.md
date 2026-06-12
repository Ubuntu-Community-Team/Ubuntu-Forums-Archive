---
title: "Brother 7030 Printer"
date: 2011-09-05
forum: General Help
---

### Post by whynot on 2011-09-05
Hi
I have Ubuntu 64x natty wubi system.I would like to install and use Brother 7030 printer.But in printer list there is no 7030 printer and when i try to use with 7020, 7025 or else it doesnot work properly.And in brother official website they have a for [Brother]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7030") i386 architect.So how ist possible to get it work?
Thanks

---

### Post by alarme on 2011-09-05
Hi,

take a look at

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

---

### Post by whynot on 2011-09-05
> **alarme said:**
> Hi,

take a look at

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

```

sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```

sudo apt-get install lib32stdc++6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lib32stdc++6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

there are no packages called printer / PC-FAX drivers

```

Pre-required Procedure (5)
    Related distributions
    Debian 64 bit version, Ubuntu 64 bit version
    Related products/drivers
    printer/PC-FAX drivers
    Requirement
    ia32-libs or lib32stdc++ is required to be installed. 

```
What does it mean? I didnt understand this part of installation step.

Thanks.

---

