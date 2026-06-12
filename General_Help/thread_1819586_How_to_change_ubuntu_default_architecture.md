---
title: "How to change ubuntu default architecture"
date: 2011-08-06
forum: General Help
---

### Post by pigeon1 on 2011-08-06
Hello. I'm newbie. I've installed UBUNTU on Intel based system afterwards I moved the hard drive to AMD based system (Sempron 3000+)

The problem is that the default architecture remains i686. Should it be i386 or amd64 and how could i change it?

---

### Post by pigeon1 on 2011-08-06
Would that command help me?

```
sudo dpkg-reconfigure -phigh -a
```

IT DIDN'T!

---

### Post by oldfred on 2011-08-06
It does not matter whether it is Intel or AMD, they are using the compatible code for 32 bit or 64bit.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
32 or 64 bit
```
uname -a
```i386 or i686 = 32-bit
x86_64 = 64-bit

If you want to convert from 32bit to 64bit you have to back up all your data, /home and a list of installed programs and do a total reinstall of the 64 bit version.

---

### Post by grahammechanical on 2011-08-06
Are you actually having problems? I do not think that you will have issues because of the difference in CPUs but what about video display and wireless adapters?

Regards.

---

### Post by jerome1232 on 2011-08-06
Remphasizing, Intel and AMD chips use the same architecture, no need to change a thing.

---

### Post by pigeon1 on 2011-08-07
thank you all. there're no problems in general, but i have the feeling that there's less software for i686. I had some troubles with installing flash and chrome, but maybe the fault is mine. :)

---

### Post by wildmanne39 on 2011-08-07
Hi, there is not less software for 32 bit version of ubuntu.

To install flash, it is best to open firefox and click on tools then addons and install flashaid,then follow the directions and flash should be working for chrome and firefox.

---

### Post by slooksterpsv on 2011-08-07
64-bit has the same amount of apps as 32-bit, 32-bit probably has more, but it's really becoming even about now.

The only reason you would really want 64-bit is if any of the following is true:

* Running VMs for 64-bit OSes
* 4GB or more RAM
* Need to run 64-bit applications for testing
* Want to be cool and move away from the old out-dated 32-bit era.

That's really it, I mean there's more but that's the basic ones

---

### Post by peterdm on 2012-05-12
Since the PAE kernels, the "4GB or more RAM" is no longer a reason.

---

### Post by Gyokuro on 2012-05-12
It's more a kind of hardware reason, PAE kernels get used in case your CPU do not support x64/AMD64 instruction sets and you want to use the whole amount of installed RAM. For system which supports x64/AMD64 instruction sets it do not make any sense nowadays to use a 32-bit-pae kernel - even with only 2GB RAM as the advantages overweight the disadvantage of such an amd64 setup.

---

