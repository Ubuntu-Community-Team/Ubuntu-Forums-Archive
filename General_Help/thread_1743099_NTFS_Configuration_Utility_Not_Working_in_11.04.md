---
title: "NTFS Configuration Utility Not Working in 11.04"
date: 2011-04-29
forum: General Help
---

### Post by CromsDog on 2011-04-29
I just did a clean install of Ubuntu 11.04 yesterday on my laptop.  My laptop has three partitions.  One for Win 7, one for Ubuntu, and another for data.  The data partition is formatted NTFS and I'd like to have it mounted on startup.  I had done this before using NTFS Configuration Utility and it worked great.  Unfortunetly after installing Natty it seems to no longer work.  Whenever I open the program from the app drawer it asks for my sudo p-word and then nothing happens.  Nothing pops up... If i try to run it from terminal using 

gksudo ntfs-config

The same thing happens but I do get the below text in term

    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.7/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'

Any help would  be appreciated.  Thanks

---

### Post by dino99 on 2011-04-29
seems to be a bug, please report it : open a terminal and run

ubuntu-bug ntfs-config

and add the previous output posted

( need to create or have a launchpad account)

note: i've run the command on my system (natty i386) and dont get your errors.

the packages installed on my system are:ntfsprogs, ntfs-3g, ntfs-config, libntfs-3g79, libntfs10

so check yours first

---

### Post by bijur on 2011-04-29
You just have to create the directory, and then everything works as usual.

But it is a bug.

Cheers,
Daniel

---

### Post by noteviljoe on 2011-04-29
> **bijur said:**
> You just have to create de directory, and then everything works as usual.

But it is a bug.

Cheers,
Daniel

Thanks for the workaround this was really bugging me too

---

### Post by wilee-nilee on 2011-04-29
Using directly fstab is another way as well.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I have a sdhc card that I use as my swap I just stuck it in fstab to mount, here is my fstab. The sda7 with the block# is a ntfs as you describe, inside the extended and a share with W7. I don't need it auto mounted so it is blocked. It could be set with the UUID like the others as well.
```
# /etc/fstab: static file system information.
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=833abb84-d08c-4870-9928-8b0c596d0708 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation

# /dev/sda7      /media/mpoint ntfs-3g    default  0   0

UUID=4a5f902b-e0e9-4f03-928f-58493be6276e   none        swap      sw               0       0 

```

---

### Post by CromsDog on 2011-04-29
> **bijur said:**
> You just have to create de directory, and then everything works as usual.

But it is a bug.

Cheers,
Daniel

I'm sorry but how do I do this? Where does the de directory need to be? home?

---

### Post by AndersonCouncil on 2011-04-30
This should help.

[http://www.ubunturoot.com/2010/11/fix-ntfs-configuration-tool-in-ubuntu.html](http://www.ubunturoot.com/2010/11/fix-ntfs-configuration-tool-in-ubuntu.html)

---

### Post by idarek on 2011-04-30
Make in terminal:
> sudo mkdir -p /etc/hal/fdi/policy

This was in 10.10 also and still not corrected in 11.04

---

### Post by CromsDog on 2011-05-02
Thanks guys! That got it working again.:)

---

