---
title: "Installed ntfs-config but can't start it from dash or terminal. V11.10"
date: 2012-01-04
forum: General Help
---

### Post by Expert Novice on 2012-01-04
Hi there, I'm very new to Ubuntu. I have installed ntfs-config but when I attempted to run it from the dash after entering my password when asked nothing more seemed to happen. I tried starting it from the terminal window and got the following output

david@ubuntu:~$ gksudo ntfs-config

(gksudo:4360): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:4360): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:4360): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:4360): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(ntfs-config:4362): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(ntfs-config:4362): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(ntfs-config:4362): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Traceback (most recent call last):
  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.7/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'
david@ubuntu:~$ 


It seems there is a file missing. Is this something I need to add myself or has it been omitted from the installation in error?

Am I going wrong somewhere?

Thanks

---

### Post by fdrake on 2012-01-04
> **Expert Novice said:**
> Hi there, I'm very new to Ubuntu. I have installed ntfs-config but when I attempted to run it from the dash after entering my password when asked nothing more seemed to happen. I tried starting it from the terminal window and got the following output

david@ubuntu:~$ gksudo ntfs-config

(gksudo:4360): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:4360): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:4360): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:4360): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(ntfs-config:4362): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(ntfs-config:4362): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(ntfs-config:4362): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Traceback (most recent call last):
  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.7/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'
david@ubuntu:~$ 



It seems there is a file missing. Is this something I need to add myself or has it been omitted from the installation in error?

Am I going wrong somewhere?

Thanks

```
sudo apt-get install gtk2-engines-pixbuf

gksudo ntfs-config
```

---

### Post by Expert Novice on 2012-01-04
Ok, thanks for that. After pasting the gksudo ntfs-config command and hitting enter still nothing seems to happen.

Here is the output generated from the commmands


david@ubuntu:~$ sudo apt-get install gtk2-engines-pixbuf
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  gtk2-engines-pixbuf
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/127 kB of archives.
After this operation, 1,069 kB of additional disk space will be used.
Selecting previously deselected package gtk2-engines-pixbuf.
(Reading database ... 152395 files and directories currently installed.)
Unpacking gtk2-engines-pixbuf (from .../gtk2-engines-pixbuf_2.24.6-0ubuntu5_i386.deb) ...
Setting up gtk2-engines-pixbuf (2.24.6-0ubuntu5) ...
david@ubuntu:~$ gksudo ntfs-config
david@ubuntu:~$

---

