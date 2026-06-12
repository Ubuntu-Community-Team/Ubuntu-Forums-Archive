---
title: "Nvidia Driver Installation Problem"
date: 2009-09-13
forum: General Help
---

### Post by WRB852 on 2009-09-13
When I went to "System>Administration>Hardware Drivers", 3 available drivers came up for my Nvidia 8800GTS. I attempted to install each one, and for all 3, I recieved an error message looking like this:

```
Ubuntu is running in low-graphics mode

The following error was encountered. You may need
to update your configuration to solve this.

(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:2:0:0.
(EE) NVIDIA(0):   Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):   additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration.
```Then I navigated to a window where I set it back to default configuration, and restarted.

Now I really don't know what to do about solving this problem. If you need any other information to help, just let me know.

---

### Post by WRB852 on 2009-09-13
Bump?

---

### Post by beastrace91 on 2009-09-13
When you boot into Ubuntu does a window pop up telling you it needs to run in low-graphics mode? Are you running Jaunty? 32bit or 64bit? Did you have any previously installed GFX drivers on the system or is this a fresh install?

Also just as an fyi don't bump a thread that is less than an hour old... Just so you know alot of people search on here for "answered" threads so adding a "bump" post to yours takes it out of that search ;)

~Jeff

---

### Post by WRB852 on 2009-09-13
No, 32bit, fresh install.

---

### Post by beastrace91 on 2009-09-13
Perhaps try giving the [manual install](https://help.ubuntu.com/community/NvidiaManual) a go. I always use this method anyways as I like to have the latest gfx driver installed.

~Jeff

---

### Post by WRB852 on 2009-09-13
Error:API mismatch: the NVIDIA kernel module has version 180.44, and this NVIDIA driver component had version 185.18.36. Please make sure that the kernel module and all NVIDIA driver components have the same version.

No idea what to do now.

---

### Post by WRB852 on 2009-09-13
Here's a bad quality picture of the error.

[http://i221.photobucket.com/albums/dd132/WRB852/0913091420.jpg](http://i221.photobucket.com/albums/dd132/WRB852/0913091420.jpg)

:P

---

### Post by beastrace91 on 2009-09-13
I think post pertains to your card, and is a solution to your problem - [http://ubuntuforums.org/showpost.php?p=4125964&postcount=32](http://ubuntuforums.org/showpost.php?p=4125964&postcount=32)

The whole thread can be found here - [http://ubuntuforums.org/showthread.php?t=665018](http://ubuntuforums.org/showthread.php?t=665018)

~Jeff

---

