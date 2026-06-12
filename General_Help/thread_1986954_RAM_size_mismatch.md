---
title: "RAM size mismatch"
date: 2012-05-25
forum: General Help
---

### Post by chenxinghao on 2012-05-25
I installed Ubuntu 11.10 in January on my IBM ThinkCentre P51 with 2GB RAM with dual-boot option co-exist with Windows XP Pro. At the time Ubuntu showed 2GB RAM in the System Monitor.

I added two more 1GB DDR RAM modules to the PC box, making it a total of 4GB RAM. In Windows XP Pro it shows 4.01GB, but in Ubuntu the System Monitor reports 3.6GB.

Why the mismatch of the total RAM size?

---

### Post by papibe on 2012-05-25
Hi chenxinghao.

My first guess is that you are running the 32bit version and using the normal kernel. There is a an extension called 'pae' that will allow you to see the 4Gb (well, minus what low lever drivers, and graphic card use)

Could you post the result of this command?
```
uname -a
```
Regards.

---

### Post by chenxinghao on 2012-05-25
Here is the output in Terminal:

~$ uname -a
Linux MyUbuntuSandBox 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux
~$

---

### Post by papibe on 2012-05-25
There it is.

To install the pae extension:
```
sudo apt-get install linux-generic-pae
```
Then reboot.

Then you should see almost all 4Gb of RAM. For example in my case I see 3956Mb.

Regards.

---

### Post by chenxinghao on 2012-05-25
What does this pae do?

I have GNU C/C++ compiler installed, as well as a few other applications (GNU emacs and VLC, etc.). Would this pae run into conflict with these applications?

---

### Post by xyzzyman on 2012-05-25
PAE just allows 32-bit kernels to access 4GB's of RAM and higher... Your install of Ubuntu still may not show more than 3.6GB's, as part of your RAM is taken up for graphics memory automatically. Windows because it's consumer orientated takes this into account and shows the full # so people don't get all nosey and ask questions. **cough cough**

---

### Post by chenxinghao on 2012-05-25
Many thanks.

---

