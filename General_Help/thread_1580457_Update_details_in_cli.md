---
title: "Update details in cli"
date: 2010-09-23
forum: General Help
---

### Post by al_mic on 2010-09-23
Hello,

Is there a way to see details for a packet before updating it?

Like, if you do:
apt-get update
and
apt-get upgrade
it will give you a list of packets that can be updated, but you don't know to what version and why.

How can I fund out, before updating, what is the version that the new packet will have.

Here I am talking about updates made from the command line.

On a Desktop system, you have that nice list in update manager, and if you click on an item you can see the new version and some details (what will fix, links..)

How can I find these info in cli?
Does anyone know?

Thanks!

---

### Post by andrewthomas on 2010-09-23
```
andrew@790Fx:~$ aptitude search linux-image
i   linux-image                       - Generic Linux kernel image.                 
v   linux-image-2.6                   -                                             
p   linux-image-2.6.32-305-ec2        - Linux kernel image for version 2.6.32 on x86
i   linux-image-2.6.35-21-generic     - Linux kernel image for version 2.6.35 on x86
i   linux-image-2.6.35-22-generic     - Linux kernel image for version 2.6.35 on x86
p   linux-image-2.6.35-22-server      - Linux kernel image for version 2.6.35 on x86
p   linux-image-2.6.35-22-virtual     - Linux kernel image for version 2.6.35 on x86
i   linux-image-2.6.35.3              - Linux kernel binary image for version 2.6.35
i   linux-image-2.6.36-rc5-dirty      - Linux kernel binary image for version 2.6.36
p   linux-image-ec2                   - Linux kernel image for ec2 machines         
i   linux-image-generic               - Generic Linux kernel image                  
p   linux-image-server                - Linux kernel image on Server Equipment.     
p   linux-image-virtual               - Linux kernel image for virtual machines  
```and 
```
andrew@790Fx:~$ aptitude show linux-image
Package: linux-image                     
New: yes
State: installed
Automatically installed: no
Version: 2.6.35.22.23
Priority: optional
Section: metapackages
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 32.8k
Depends: linux-image-generic (= 2.6.35.22.23)
Provided by: linux-image-2.6.32-305-ec2, linux-image-2.6.35-21-generic,
             linux-image-2.6.35-22-generic, linux-image-2.6.35-22-server,
             linux-image-2.6.35-22-virtual, linux-image-2.6.35.3,
             linux-image-2.6.36-rc5-dirty
Description: Generic Linux kernel image.
 This package will always depend on the latest generic Linux kernel image
 available.
``` furthermore

```
andrew@790Fx:~$ aptitude why linux-image
i   linux Depends linux-image (= 2.6.35.22.23)
```

---

### Post by gmargo on 2010-09-23
Adding a **-V** flag to **apt-get** (or **aptitude**) will give you the from/to version number information.

---

### Post by al_mic on 2010-09-24
These tools you told me about are great!
Just what I needed to know.

Thank you!

---

