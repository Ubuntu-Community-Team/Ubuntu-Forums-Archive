---
title: "a few questions regarding acpi and grub rescue"
date: 2010-05-14
forum: General Help
---

### Post by hardwired112 on 2010-05-14
hello everyone. I'm new to the ubuntu forums as well as ubuntu. I'm excited to learn more about linux itself as well as ubuntu

I got ubuntu 10.04 running on my toshiba L505D laptop by disabling acpi in the boot commands. My first question is how do i do this permanently, is this bad, and would updating fix the issue? If so how would I go about updating.

Secondly, when the external hard drive I installed ubuntu on is not plugged in to the laptop, GRUB rescue comes up. I kind of like this because it provides a level of hardware security. I would however like to know how to load my windows partition encase the external hard drive fails.

thanks in advance for any help you folks might be able to provide.

---

### Post by hardwired112 on 2010-05-14
anyone able to help out with this? im still stumped.

---

### Post by colinwhipple on 2010-05-14
There are some alternate boot parameters that work with 9.10, but not with 10.4.

There are some very good instructions for compiling your own kernel with a patch that solves the problem, either in 9.10 or 10.4 here:

[http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d&page=8](http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d&page=8)

Using acpi=off permanently could damage your laptop through overheating.  I used that parameter while installing Ubuntu, and then while compiling a patched kernel.

Grub should detect your windows partition and add it to the Grub menu automatically.  I don't know why it isn't doing that.  It does for me.

Colin

---

