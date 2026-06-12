---
title: "crash to black screen with text"
date: 2011-11-29
forum: General Help
---

### Post by silverhorse33 on 2011-11-29
Hello,
I have ubuntu 11.10 64 bit. It runs fine but crashes/freezes to a black screen with text about three times daily. The text indicates first a 'BUG unable to handle kernel paging request', then a lot more. I cannot figure out how to find this information after I do a hard reboot.
Is the right place to ask how to get the info, and if it is, is this where I should post it, when I do?
Thank you,
S.

---

### Post by BC59 on 2011-11-29
> **silverhorse33 said:**
> Hello,
I have ubuntu 11.10 64 bit. It runs fine but crashes/freezes to a black screen with text about three times daily. The text indicates first a 'BUG unable to handle kernel paging request', then a lot more. I cannot figure out how to find this information after I do a hard reboot.
Is the right place to ask how to get the info, and if it is, is this where I should post it, when I do?
Thank you,
S.

Open a terminal CTRL+ALT+T and execute:

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by silverhorse33 on 2011-11-29
Thank you BC,
The commands yield 

0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

S.

---

### Post by BC59 on 2011-11-29
Well we have a kernel panic here.

Looks like a bug. The problem could be caused from many reasons, usually hardware collaboration problems with the kernel. 

What kernel you use? Go to dash write to search Monitor and from the System Monitor check the tab System to see the kernel.

---

### Post by silverhorse33 on 2011-11-29
The kernel is:

Kernel 3.0.0-13-generic

---

### Post by BC59 on 2011-11-29
So now from the boot grub screen (if you cannot see it during boot hold SHIFT) should be an option, to boot using old kernels. Choose to boot with the old kernel 3.0.0-12 to see if the situation is better.
Use the computer with this kernel and try to reproduce the problem.

---

### Post by silverhorse33 on 2011-11-29
Thanks. 

I did hold the shift button, but there is only the one kernel. I did a clean install from USB drive.

S.

---

### Post by BC59 on 2011-11-29
In that case I don't have a solution. It's a bug and needs to be taken care of the Ubuntu developers.
You could search on Ubuntu Launchpad to find which bug is and report your incident.

---

### Post by silverhorse33 on 2011-11-29
Thanks for your help BC. I did search for how to report the bug, but the crash takes me to a screen that has no way of copying it, and none of the directions I can find really seem to address what to do in this case. I don't really know how to report it.
I will try to downgrade the kernel and see if that helps, then I will format and install an earlier version of ubuntu. 
You were a great help...thank you very much *S*.
S.

---

### Post by BC59 on 2011-11-30
Very sorry I couldn't help.

---

