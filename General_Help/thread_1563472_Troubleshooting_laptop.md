---
title: "Troubleshooting laptop"
date: 2010-08-29
forum: General Help
---

### Post by calelettus on 2010-08-29
I've been running Ubuntu problem-free since 6.04 on my Dell Latitude D510. Now, with 10.04LTS I'm having repeated startup problems.

The machine is dual-boot with Windows XP. The XP partition runs fine. The Ubuntu partition runs fine much of the time but about once every 3 or 4 starts the machine hangs. Sometimes it is as soon as I select Ubuntu from GRUB while other times it is right after I login. The screen just sits there and the disk light is on (steady). It stays that way until I reboot when usually it comes right up.

This **never** happens when Windows is selected. At first I tried a clean reinstall of Ubuntu AND Windows and it did not help. I then bought a new larger hard drive and reinstalled Ubuntu & Windows and the same thing is happening. I tried installing a copy of Ubuntu 8.04 and I could not duplicate the problem.

So, any ideas how to troubleshoot this? Ubuntu haw been so reliable for me that I haven't really kept up to date on troubleshooting protocols! Thanks!

---

### Post by coldraven on 2010-08-29
It could be your Intel video chipset 

[LIST]
[*] **Graphics Processor / Vendor**  Intel Graphics Media Accelerator 900 
[/LIST]
10.04 does not like some of the older Intel chips, you may have to stick with 8.04 or another distro.
See my post here: [http://ubuntuforums.org/showthread.php?t=1477407](http://ubuntuforums.org/showthread.php?t=1477407)
I hope that helps.

---

### Post by calelettus on 2010-08-29
I bet you're right. Thanks for that!

---

