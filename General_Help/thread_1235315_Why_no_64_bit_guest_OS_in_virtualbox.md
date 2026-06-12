---
title: "Why no 64 bit guest OS in virtualbox?"
date: 2009-08-08
forum: General Help
---

### Post by s3a on 2009-08-08
I installed the latest non-open source Virtualbox from Sun's website which supposedly could run a 64 bit guest not only within a 64 bit host but also a 32 bit host! Either way, I have a 64 bit CPU/OS. I chose the non-open source version due to kernel complications. I have a .iso file of a 64 bit operating system however it gives me the classic "Your CPU does not support this kernel" kind of error. I've been told there is a way to enable 64 bit from one person and I've been told by someone else that I had to disable 3D acceleration however by default 3D acceleration is turned off and I see no *enable 64 bit* option. Believe it or not, this is all for a bug report since at this time, I only plan to run Windows XP (32-bit) for school purposes just in case they demand a Windows operating system.

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by coldReactive on 2009-08-08
Open virtual machine settings, select Operating System (IE: Windows) and then select a 64-bit version of the operating system from the version dropdown.

---

### Post by s3a on 2009-08-09
I see no 64 bit version of any OS in the drop down list...why is this the case and what can I do about it?

---

### Post by coldReactive on 2009-08-09
> **s3a said:**
> I see no 64 bit version of any OS in the drop down list...why is this the case and what can I do about it?

Do you have 32-bit X/K/Ubuntu Installed?

Also, there is no way to enable 64-bit separately, it has to be under the dropdowns.

---

### Post by s3a on 2009-08-09
Yes, I am using 64 bit. Which version do I need? I have Virtualbox 3.0.4 r50677.

---

### Post by coldReactive on 2009-08-09
> **s3a said:**
> Yes, I am using 64 bit. Which version do I need? I have Virtualbox 3.0.4 r50677.

I have that same version with Ubuntu 9.04 amd64, and I can select 64-bit versions of the OSes. Sorry, I can't help.

---

### Post by blurpo on 2010-08-15
I have the same problem (only see one version of each OS -- 32-bit implied I think) and I think I know the reason.

I'm running Ubuntu 10.04 64-bit on an Intel Core 2 Duo T5800. According to the VirtualBox docs you need hardware virtualization support, so I looked in my BIOS to enable it. Can't find the option. Then I looked on [http://ark.intel.com](http://ark.intel.com) for the specification of the CPU and it says "no Intel Virtualization Technology supported". So I guess it's a limitation of my CPU, in the end.

Hope that helps.

(Find your CPU model by typing ```
grep name /proc/cpuinfo
```).

---

