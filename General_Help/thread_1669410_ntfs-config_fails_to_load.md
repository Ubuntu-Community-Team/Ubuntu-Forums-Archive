---
title: "ntfs-config fails to load"
date: 2011-01-17
forum: General Help
---

### Post by ELD on 2011-01-17
Ok guys wandering what this means when i try to run ntfs-config?

> 
Traceback (most recent call last):
  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.6/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'


Installed to a very fresh Ubuntu10.10

---

### Post by fuct_ on 2011-01-23
same thing here, were you trying to run it from a Live CD as well?

the workaround performed was to do the following:

```

sudo mkdir /etc/hal
sudo mkdir /etc/hal/fdi
sudo mkdir /etc/hal/fdi/policy
sudo ntfs-config &

```

** last line just (test) executes the program, just make sure to issue a 'kill' command.

---

