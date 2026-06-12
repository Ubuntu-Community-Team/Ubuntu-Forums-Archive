---
title: "need help with lexmark printer in chroot"
date: 2011-10-03
forum: General Help
---

### Post by linuxlover42 on 2011-10-03
Hey world, can I have some help. I want to install the driver for my lexmark x2650 on a 32 bit chroot (i have a 64 bit system.) However, whenever I do so i get the message:

```
Verifying archive integrity... All good.
Uncompressing nixstaller...............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86
Error opening terminal: xterm.
```I've looked around and it seems that this is because the chroot cannot open an x server. I have not found any clear instructions to fix this so I must beg your help.

Thanks in advance

---

### Post by searchfgold6789 on 2011-10-03
It's not that it can't open an X server. It can't open up it's own terminal session. I would do a few things:

[LIST=1]
[*]Make sure that you're running the installer as root
[*]Make sure the files are executable, do a ```
sudo chmod a+x {filename}
```
[*]Try putting 'sh' in front of the filename next time you run it. ;) has worked for me before with this sort of thing.
[/LIST]

---

### Post by linuxlover42 on 2011-10-03
the file already has .sh at the end of it's name
```
lexmark-inkjet-08-driver-1.0-1.i386.deb.sh
``` 

It is executable and I'm running it as root, I entered the Chroot with
```
schroot -c natty_i386 -u root
```

---

### Post by linuxlover42 on 2011-10-03
when I try to open xterm from the chroot terminal I get

```

Warning: This program is an suid-root program or is being run by the root user.
The full text of the error or warning message cannot be safely formatted
in this environment. You may get a more descriptive message by running the
program as a non-root user or by removing the suid bit on the executable.
xterm Xt error: Can't open display: %s
xterm:  DISPLAY is not set
```

---

