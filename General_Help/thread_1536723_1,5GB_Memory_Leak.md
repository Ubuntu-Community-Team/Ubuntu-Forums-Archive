---
title: "1,5GB Memory Leak"
date: 2010-07-22
forum: General Help
---

### Post by rafadev on 2010-07-22
I'm running 64 bits 10.04 on a Lenovo Y560 laptop. Each time I turned on the computer it would be using about 1,5GB of ram by default but when looking at the TOP or at the running processes, the largest process was using only 20MB of ram.

I read on the forums that ATI propietary drivers had a memory leak so I tried running glxinfo, and every time I ran it a lot of memory got freed (it was occupied again after some minutes). Because of this, I upgraded the drivers to the latest version from ATI, and the problem was solved, but out of nowhere, it started again. Each time I turn on my laptop, 1,5GB of ram are used by... nothing?

[IMG]http://www.ubuntu-pics.de/bild/113780/selection_005_uni6zz.png[/IMG]

See, the process that's using the most ram here is Xorg with 3.7% (143MB) but the total used ram reported is 2GB.

Has anyone got an idea? Please let me know if I can provide any other useful information.

Thank you very much for your help

Rafa

---

### Post by davidmohammed on 2010-07-22
... sometimes removing the ureadahead pack file and rebooting a couple of times to regenerate it, fixes this sort of issue.

give it a go

sudo rm /var/lib/ureadahead/pack

---

### Post by rafadev on 2010-07-22
> **davidmohammed said:**
> ... sometimes removing the ureadahead pack file and rebooting a couple of times to regenerate it, fixes this sort of issue.

give it a go

sudo rm /var/lib/ureadahead/pack

Tried that but it didn't work, should I recreate that file somehow now?

---

### Post by davidmohammed on 2010-07-22
you have to reboot a couple of times - it gets rebuilt automatically.  See [here]("http://ubuntuforums.org/showthread.php?t=1434502") for more details.

---

### Post by techunit on 2010-07-22
Generally you don't need to worry about a small leak like say 256mbs of leak.... but the amount of leak your experiencing is not unacceptable.

---

### Post by Welly Wu on 2010-07-28
Did you find a solution to this massive memory leak issue on your Lenovo IdeaPad Y560? If so, then please post the solution. Thank you.

---

### Post by rafadev on 2010-08-04
> **Welly Wu said:**
> Did you find a solution to this massive memory leak issue on your Lenovo IdeaPad Y560? If so, then please post the solution. Thank you.

Hey!
I did solve this problem by updating to the latest ATI Catalyst driver (the bundled version is buggy)

Downloaded the latest version from here:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

To an empty temporary folder

Then executed

sudo sh ./ati*.run --buildpkg Ubuntu/lucid

once completed

sudo dpkg -i *.deb

to install all packages built

Reset your machine and it's fixed!

Let me know if you need further instructions.

Rafa

---

