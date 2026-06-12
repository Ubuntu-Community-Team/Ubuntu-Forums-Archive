---
title: "Trying to install .run file"
date: 2011-09-24
forum: General Help
---

### Post by derekreilly on 2011-09-24
Hi,

I'm trying to install a new version of my Nvidia graphics card driver: NVIDIA-Linux-x86_64-280.13.run

I have followed the instructions here:
[https://help.ubuntu.com/8.04/add-applications/C/install-file.html](https://help.ubuntu.com/8.04/add-applications/C/install-file.html)

But I get the following message in the terminal: ERROR: nvidia-installer must be run as root.

Can anyone help?

---

### Post by CharlesA on 2011-09-24
Run this:

```
sudo ./NVIDIA-Linux-x86_64-280.13.run
```

---

### Post by derekreilly on 2011-09-24
: command not found

---

### Post by CharlesA on 2011-09-24
Just add sudo before you run the command.

Was it run from the terminal?

---

### Post by derekreilly on 2011-09-24
In the terminal I run sudo ./NVIDIA-Linux-x86_64-280.13.run

it asks for my password, I type it then I receive this message:

sudo: ./NVIDIA-Linux-x86_64-280.13.run: command not found

---

### Post by Tank Jr on 2011-09-24
Are you invoking the command in the same directory?

---

### Post by derekreilly on 2011-09-24
I got it to run now I receive this:

[[IMG]http://img193.imageshack.us/img193/4025/screenshot1ce.png[/IMG]](http://imageshack.us/photo/my-images/193/screenshot1ce.png/)

---

### Post by CharlesA on 2011-09-24
Any reason you aren't installing them via the "Hardware Drivers" applet?

You'd have to stop gdm before installing.

---

### Post by derekreilly on 2011-09-24
Hi Charles, I'm pretty new to Linux. I have no idea where Hardware Drivers applet is.

---

### Post by CharlesA on 2011-09-24
What version are you using?

---

### Post by derekreilly on 2011-09-24
Currently using Ubuntu 11.10 and Linux Mint 11.04

---

### Post by CharlesA on 2011-09-24
Not sure where that would be located. Perhaps post in the dev area, since 11.10 isn't out yet.

---

