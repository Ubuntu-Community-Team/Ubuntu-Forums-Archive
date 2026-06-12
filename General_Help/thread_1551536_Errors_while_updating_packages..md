---
title: "Errors while updating packages."
date: 2010-08-12
forum: General Help
---

### Post by Mr_VeRiTy on 2010-08-12
Hi, I just tried to updating my packages using synaptic but I got the error 
```
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/status': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A Package failed to install. Trying to recover:
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/status': Input/output error

```
Could this have anything to do with [this thread]("http://ubuntuforums.org/showthread.php?p=9671419") I started a week ago.
The packages I'm trying to update are:

[LIST]
[*]Chromium-browser
[*]chromium-browser-inspector
[*]chromium-codecs-ffmpeg
[*]gnupg-agent
[*]gnupg2
[*]ldap-utils
[*]ldap-2.4-2
[*]slapd
[/LIST]

EDIT: It dosn't work with update manager either.

---

### Post by Mr_VeRiTy on 2010-08-12
*bump*

---

### Post by Mr_VeRiTy on 2010-08-12
Also I can't install anything, as I get the same error.

---

### Post by surfer on 2010-08-12
what happens if you run

```

$ sudo apt-get update
$ sudo apt-get install gnupg-agent

```

in the console? close synaptic before you run those commands.

---

### Post by Intrepid Ibex on 2010-08-12
Could you try something like:
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get install
sudo apt-get autoremove
```

**E:** If that doesn't work, you can try manually reinstalling the "apt" package. If you are using a 32-bit Lucid you can try this:
```
wget http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu7_i386.deb && sudo dpkg -i apt_0.7.25.3ubuntu7_i386.deb && rm apt_0.7.25.3ubuntu7_i386.deb
```

And with 64-bit Lucid this:
```
wget http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu7_amd64.deb && sudo dpkg -i apt_0.7.25.3ubuntu7_amd64.deb && rm apt_0.7.25.3ubuntu7_amd64.deb
```

**E2:** If even that won't do the trick, you can try to use the backup dpkg status list and retry:
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

---

### Post by Mr_VeRiTy on 2010-08-12
> **surfer said:**
> what happens if you run

```

$ sudo apt-get update
$ sudo apt-get install gnupg-agent

```

in the console? close synaptic before you run those commands.
It gives me the same error, I think the problem I described in [http://ubuntuforums.org/showthread.php?p=9671419](http://ubuntuforums.org/showthread.php?p=9671419) has affected the "status" file in /var/lib/dpkg, and to check if it had, I tried to copy it to another location and sure enough I got the "Error splicing file: Input/output error." error.

---

### Post by Mr_VeRiTy on 2010-08-12
> **Intrepid Ibex said:**
> Could you try something like:
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get install
sudo apt-get autoremove
```
Same error.

---

### Post by Intrepid Ibex on 2010-08-12
If it's a physical problem, you've got yourself a problem, mate.

Did you try checking for bad blocks from Live-CD on you partition where /var is located (normally root, "/")?:

```
sudo fsck -f -c -C -V /dev/sdaX
```

Replace the "X" with the partition number.

---

### Post by Mr_VeRiTy on 2010-08-12
> **Intrepid Ibex said:**
> If it's a physical problem, you've got yourself a problem, mate.
It shouldn't be too much of a problem, provided I can backup all my files before they go corrupt, looks like I'll be getting a new hard drive.

---

### Post by Intrepid Ibex on 2010-08-12
A wise decision. Nothing lasts forever.

---

### Post by Mr_VeRiTy on 2010-08-12
> **Intrepid Ibex said:**
> A wise decision. Nothing lasts forever.
I just won't be getting a Toshiba hard drive ever again, this one is only 9 months old, I'll be going the seagate route from now on.

---

