---
title: "synaptic package manager vs command in terminal"
date: 2011-10-19
forum: General Help
---

### Post by masuch on 2011-10-19
Hi,

I would like to see the list of all packages in terminal as they are in synaptic package manager visible.

example:
command:
dpkg --list |grep linux-image
shows some of linux-images but not all of linux-images which I can see in synaptic package manager.

any command/s please.
thanks,

---

### Post by gmargo on 2011-10-19
"dpkg -l" (or "dpkg --list") shows the currently installed packages.

To search all available packages (installed or not), use the **apt-cache search** command:

```

$ [COLOR=Red]apt-cache search linux-image[/COLOR]
alsa-base - ALSA driver configuration files
linux-image-2.6.32-305-ec2 - Linux kernel image for version 2.6.32 on x86/x86_64
linux-image-ec2 - Linux kernel image for ec2 machines
linux-image - Generic Linux kernel image.
linux-image-2.6.35-22-generic - Linux kernel image for version 2.6.35 on x86/x86_64
linux-image-2.6.35-22-server - Linux kernel image for version 2.6.35 on x86_64
linux-image-2.6.35-22-virtual - Linux kernel image for version 2.6.35 on x86/x86_64
... (snipped for shortness)

```

---

### Post by masuch on 2011-10-19
thanks a lot :-)

(just need more info - when I run

dpkg --list |grep linux-image

result:
rc  linux-image-2.6.38-10-generic                               2.6.38-10.46                                             Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-2.6.38-11-generic                               2.6.38-11.50                                             Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-2.6.38-11-virtual                               2.6.38-11.49                                             Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-2.6.38-12-generic                               2.6.38-12.51                                             Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-2.6.38-8-generic                                2.6.38-8.42                                              Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-3.0.0-10-generic                                3.0.0-10.16                                              Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-11-generic                                3.0.0-11.18                                              Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-12-generic                                3.0.0-12.20                                              Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-7-generic                                 3.0.0-7.9                                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-7-virtual                                 3.0.0-7.9                                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-8-generic                                 3.0.0-8.10                                               Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-9-generic                                 3.0.0-9.14                                               Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.1-030001-generic                            3.0.1-030001.201108060905                                Linux kernel image for version 3.0.1 on x86/x86_64
rc  linux-image-3.0.1-030001-i7                                 3.0.1-030001.201108060905                                Linux kernel image for version 3.0.1 on x86/x86_64
rc  linux-image-3.0.2-030002-generic                            3.0.2-030002.201108161204                                Linux kernel image for version 3.0.2 on x86/x86_64
rc  linux-image-3.0.3-030003-i7                                 3.0.3-030003.201108180913                                Linux kernel image for version 3.0.3 on x86/x86_64
ii  linux-image-3.0.4-030004-i7                                 3.0.4-030004.201108301138                                Linux kernel image for version 3.0.4 on x86/x86_64
ii  linux-image-generic                                         3.0.0.12.14                                              Generic Linux kernel image

and only ii* are installed.
that's confusing me little bit.

---

