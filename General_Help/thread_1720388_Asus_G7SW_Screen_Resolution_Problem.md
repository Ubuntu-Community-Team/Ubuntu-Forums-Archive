---
title: "Asus G7SW Screen Resolution Problem"
date: 2011-04-03
forum: General Help
---

### Post by Darth Penguin on 2011-04-03
Hello, I'm having a bit of a problem. I bought an Asus G7SW for my mom and I set it up to dual boot with Windows 7. Once I installed Ubuntu 10.10 the only resolutions available are 600x480 and 800x600. I've been trying to fix it to no avail and from what I've read it may be an issue with nVidia proprietary drivers(the Asus G7SW has a GEFORCE GTX 440 graphics card). I'd really love to be able to get the resolution up to the 1600X900 it can have on Windows if at all possible, because otherwise I'd have to uninstall Ubuntu and that would make me sad. :(

---

### Post by realzippy on 2011-04-03
Is it an [Optimus]("http://ubuntuforums.org/showthread.php?p=10304516#post10304516") laptop?

run
```
lspci |grep VGA
```
+ post output

---

### Post by Darth Penguin on 2011-04-03
**01:00.0 VGA compatible controller: nVidia Corporation Device 0dd1 (rev a1)**

It's not an Optimus. I'm going to try that fix you posted if nothing else works though. :D

---

### Post by realzippy on 2011-04-03
Which fix?
The command only shows your graphics adapter,would you please run it?
Did you install the proprietary NVIDIA driver?

---

### Post by Darth Penguin on 2011-04-03
The output was:

01:00.0 VGA compatible controller: nVidia Corporation Device 0dd1 (rev a1)

---

### Post by realzippy on 2011-04-03
Did you install the proprietary NVIDIA driver?

---

### Post by Darth Penguin on 2011-04-03
> **realzippy said:**
> Did you install the proprietary NVIDIA driver?I did not manually install any driver. Should I?

---

### Post by realzippy on 2011-04-03
Is there a driver offered in System=>Administration=>Hardware Drivers?
If so,install it.
If problems rebooting,boot in recovery mode and uninstall the driver.

---

### Post by Darth Penguin on 2011-04-03
> **realzippy said:**
> Is there a driver offered in System=>Administration=>Hardware Drivers?
If so,install it.
If problems rebooting,boot in recovery mode and uninstall the driver.I'll try that and I'll report back with the results in a bit. Thank you for helping me! :P

edit

I did a reinstall and did not add third party source to the install, then installed the proprietary driver and it worked! Thank you!!!

---

### Post by realzippy on 2011-04-14
Can you set thread as solved (threadtools) ?

---

