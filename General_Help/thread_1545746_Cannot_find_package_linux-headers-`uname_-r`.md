---
title: "Cannot find package linux-headers-`uname -r`"
date: 2010-08-04
forum: General Help
---

### Post by wesg on 2010-08-04
I'm trying to reinstall my Hauppauge 1600 drivers since upgrading kernels but following the same instructions I did before, I get nothing. The instructions are found at [http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Installation_Guide](http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Installation_Guide) and when I enter the command ```
sudo apt-get install linux-headers-`uname -r` build-essential
``` it doesn't find the package. 

Suggestions?

---

### Post by dino99 on 2010-08-04
use synaptic its the easiest way

---

### Post by 101011010010 on 2010-08-04
Hello,
shouldn't there be a "$" symbol before (uname -r)?> $ [sudo] apt-get install linux-headers-$(uname -r) build-essentialI hope this helps.

---

### Post by wesg on 2010-08-04
> **101011010010 said:**
> Hello,
shouldn't there be a "$" symbol before (uname -r)?I hope this helps.

I should have mentioned that the problem is not that the nested commands aren't working, it's that the full command doesn't find anything (ie. the search linux-headers-2.6.28.xx doesn't find a match)

---

### Post by LowSky on 2010-08-04
The command should work just fine, heck I copied and pasted what you typed and it works just fine.

```
sudo apt-get install linux-headers-`uname -r`
```
if your typing it by hand, this:```
`
``` is not ```
'
```

If your system is fully updated it should be linux-header-2.6.32-24, use synaptic to install the file

---

### Post by oldos2er on 2010-08-04
Do you have the Source code repos enabled? System, Administration, Software Sources.

---

### Post by wesg on 2010-08-06
I'm using the CLI. Any different instructions?

---

### Post by LowSky on 2010-08-06
```
sudo apt-get install linux-headers-*
```

---

### Post by GlazedDonut on 2010-08-06
You can search for packages on the command line by using apt-cache search. ```
apt-cache search kernel-headers
```

---

### Post by wesg on 2010-08-06
Does it have something to do with my kernel version + ubuntu version combination? I just upgraded to 9.10 but apparently I'm still running a 2.6.28 kernel. I just sent the command ```
sudo apt-get install linux-headers-2.6.31-305-generic
``` and it downloaded 85 MB. I ran the command ```
sudo apt-get install linux-headers-*
``` afterwards and it found a whole bunch of header packages.

---

### Post by wesg on 2010-08-06
Problem mostly solved. I upgraded the kernel to the 9.10 expected 2.6.31 and it compiled again. Restarting now.

---

