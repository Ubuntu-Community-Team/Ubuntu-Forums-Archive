---
title: "&quot;build&quot;-Folder missing"
date: 2006-04-29
forum: General Help
---

### Post by orkomedix on 2006-04-29
Hello there...
I want to install the pwc-driver for a Philips SPC 900nc webcam from [Luc Saillard]("http://www.saillard.org/linux/pwc/") and make would give me
```
me@mymaschine:~/pwc-10.0.12-rc1$ make
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/orkomedix/pwc-10.0.12-rc1 modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
```
When I look into ```
/lib/modules/2.6.12-10-386/
``` there is in fact no folder "build".
```
uname -r
``` says ```
2.6.12-10-386
``` 
but under /usr/src/ there is only a tar.bz2 for the linux-source.

How do I get the /lib/modules/2.6.12-10-386/build-Folder ???

Please help !

---

### Post by xenmax on 2006-04-29
Try this:
Look for package linux-headers-<your kernel version> and install it or
from command line ```
sudo apt-get install linux-headers-<your kernel version>
```

---

### Post by orkomedix on 2006-04-29
Hallo again...

Yes, I did that before but there seems to be NO exact packedge for my version. 
I have installed the the linux-headers-386 and linux-headers-2.6.12-9 and they are, as far as I know, correctly installed, since ls gives me
```
me@mylaptop:/lib/modules/2.6.12-10-386$ ls
initrd   modules.alias   modules.ieee1394map  modules.pcimap    modules.usbmap
kernel   modules.ccwmap  modules.inputmap     modules.seriomap  volatile
madwifi  modules.dep     modules.isapnpmap    modules.symbols

```
But the "build"-Folder is still not there...

Any Idea ? I am running out of ideas at the moment....](*,)

---

### Post by xenmax on 2006-04-29
I am not sure if this is a minor detail or not, but did you install the package "linux-headers-2.6.12-9-386" (You only mentioned "linux-headers-2.6.12.9" in your earlier post)? The reason i ask this is, in my machine the build dir is actually a link as follows: > /lib/modules/2.6.12-9-386/build -> /usr/src/linux-headers-2.6.12-9-386 which is install location of "linux-headers-2.6.12-9-386" package as mentioned in Synaptic.
A package for exact version *might* not be necessary because according to Synaptic;s description of package "linux-headers-2.6.12-9-386" 
> Linux kernel headers 2.6.12 on 386
This package provides kernel header files for version 2.6.12 on
386,
for sites that want the latest kernel headers.
Please read /usr/share/doc/linux-headers-2.6.12-9/debian.README.gz for
details where only 2.6.12 is mentioned which i presume means it is ok for 2.6.12.*

Hope this helps.

---

### Post by orkomedix on 2006-04-30
Hello there...

Yes, I did install the headers 2.6.12-XX as the Synaptic-Description sounded like I could need them. But in fact it only created a ".bz2" in the /usr/src/ ...

I will try to unpack them and create the link myself - this might work !

Thanks for the help - I'll be back...

---

### Post by xenmax on 2006-04-30
Yep, i was about to ask you in last post as to what tar.bz2 contains and if it contains folder linux-headers-*, untar it and create link yourself. But i was hoping installing package linux-headers-2.6.12.9-386 would do that, but it obviously didn;t do that as you say package is already installed.

Anyways, good luck with that. Hopefully that should solve problem.

---

### Post by orkomedix on 2006-04-30
Solved !
I just untared the linux-headers-2.6.12.9-386 and made a softlink in /lib/modules/2.6.12-10-386/build  ...

Sometimes it is that easy.

Thanks a lot !!:mrgreen:

---

### Post by xenmax on 2006-04-30
Glad it worked out for you. :)

---

### Post by wydra on 2007-11-18
How did you make a softlink? I'm having the same problem, I'm new to this.

Thx for the help.

---

### Post by xenmax on 2007-12-08
I am just replying in case you still face the problem. 

To create a link, first cd to directory where you want the link
 then use ln -s to create a link
```

cd <dir>
ln -s <relative path to target> <linkname>
```

For eg:
```
ln -s ../../foo link_to_foo 
```

---

