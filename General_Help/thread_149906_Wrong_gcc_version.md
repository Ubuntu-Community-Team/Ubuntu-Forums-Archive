---
title: "Wrong gcc version"
date: 2006-03-24
forum: General Help
---

### Post by rhomsy on 2006-03-24
I was trying to configure vmware, and I got the following error:

Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.plwith CC environment variable pointing to the "gcc" version "3.4.5".

How can I fix this?

---

### Post by Jason_25 on 2006-03-24
Install gcc-3.4 from synaptic.  Then
```

CC=gcc-3.4
export CC

```

---

### Post by rhomsy on 2006-03-24
[QUOTE=Jason_25]Install gcc-3.4 from synaptic.  Then
```

CC=gcc-3.4
export CC

```[/QUOTE]

Great.... I installed gcc 3.4, now where do I put that code?  I really appreciate your help.  Thank you.

---

### Post by Jason_25 on 2006-03-24
Put it in the terminal right before you run the configure script.

---

### Post by rhomsy on 2006-03-24
[QUOTE=Jason_25]Put it in the terminal right before you run the configure script.[/QUOTE]

Now the script is asking me for the path of the c header files that match my running kernel (in my case K7).  Where the hell are these things.... what is a name of one so maybe I can do a find?  The script tries to look in /usr/src/linux/include but the directory doesn't exist.

---

### Post by Jason_25 on 2006-03-24
You'll need to install the headers for your kernel version from synaptic.  To find your kernel version type
```

uname -r

```
at the terminal.

---

### Post by rhomsy on 2006-03-24
[QUOTE=Jason_25]You'll need to install the headers for your kernel version from synaptic.  To find your kernel version type
```

uname -r

```
at the terminal.[/QUOTE]

My kernel is 2.6.12-10-k7.
How do I get the headers?  I couldn't find them in synaptic.

---

### Post by Jason_25 on 2006-03-24
Just search for headers in synaptic.  I'm sure there is a much better way but it's how I do it.

---

### Post by rhomsy on 2006-03-24
[QUOTE=Jason_25]Just search for headers in synaptic.  I'm sure there is a much better way but it's how I do it.[/QUOTE]

Here is my latest error from the installer script:

The path "/etc/src/kernel-source-2.6.10/include" is a
kernel header file directory, but it does not contain the file "linux/version.h"as expected.  This can happen if the kernel has never been built, or if you haveinvoked the "make mrproper" command in your kernel directory.  In any case, you
may want to rebuild your kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

now what do I do?

---

### Post by Jason_25 on 2006-03-24
I'm not entirely sure on this one, but just to assist others in helping you, you may want to post the name of the package you installed from synaptic..  Maybe you installed some kernel headers, but not the right ones.

---

### Post by akiro.yamamoto on 2006-03-25
Use Synaptic and search for
linux-headers
then select the one for your system ;)
See Pic
Hope this helps...

---

### Post by rhomsy on 2006-03-25
[QUOTE=akiro.yamamoto]Use Synaptic and search for
linux-headers
then select the one for your system ;)
See Pic
Hope this helps...[/QUOTE]

I'm still getting the same error, and I did download the correct header files.  Here is the error:
The path "/usr/src" is a kernel header file directory, but it does not contain
the file "linux/version.h" as expected.  This can happen if the kernel has neverbeen built, or if you have invoked the "make mrproper" command in your kernel
directory.  In any case, you may want to rebuild your kernel.

Evidently, the headers that we download through synaptic don't have the version.h file.  WHat can I do.... I'm totally stuck?  Thanks in advance for any help... I really appreciate this community.

---

### Post by xenmax on 2006-03-25
perhaps the path should be either:
/lib/modules/$(shell uname -r)/build/include 
Actually build is a link to  /usr/src/linux-headers-2.6.12-9-386/   - where 2.6.12-9-386 is my kernel ver.

So your path could also be /usr/src/linux-headers-2.6.12-9-386/include

The above mentioned path has linux/version.h in my machine.

---

### Post by rhomsy on 2006-03-25
[QUOTE=xenmax]perhaps the path should be either:
/lib/modules/$(shell uname -r)/build/include 
Actually build is a link to  /usr/src/linux-headers-2.6.12-9-386/   - where 2.6.12-9-386 is my kernel ver.

So your path could also be /usr/src/linux-headers-2.6.12-9-386/include

The above mentioned path has linux/version.h in my machine.[/QUOTE]


Thanks.  I figured out the problem (i think).  The script kept saying that the headers were not the headers for my kernel.  I knew I had the correct headers, so I sudo vi the version.h file and changed #define UTS_RELEASE "2.6.12-10" to #define UTS_RELEASE "2.6.12-10-k7" and the script installed.  Now I just hope it works.

THanks everyone.

---

