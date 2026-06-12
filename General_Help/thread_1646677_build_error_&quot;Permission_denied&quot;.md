---
title: "build error: &quot;Permission denied&quot;"
date: 2010-12-16
forum: General Help
---

### Post by Kazimalik on 2010-12-16
Dear All,
I am using ubuntu 10.10 that i have installed inside windows 7. I had downloaded android source code. When i try to build it an error comes. 

The output is
kazim@ubuntu:~/work/android$ make
/bin/bash: prebuilt/linux-x86/toolchain/arm-eabi-4.4.0/bin/arm-eabi-gcc: Permission denied
/bin/bash: prebuilt/linux-x86/toolchain/arm-eabi-4.4.0/bin/arm-eabi-gcc: Permission denied
/bin/bash: build/core/find-jdk-tools-jar.sh: Permission denied
============================================
PLATFORM_VERSION_CODENAME=AOSP
PLATFORM_VERSION=AOSP
TARGET_PRODUCT=generic
TARGET_BUILD_VARIANT=eng
TARGET_SIMULATOR=
TARGET_BUILD_TYPE=release
TARGET_BUILD_APPS=
TARGET_ARCH=arm
TARGET_ARCH_VARIANT=armv5te
HOST_ARCH=x86
HOST_OS=linux
HOST_BUILD_TYPE=release
BUILD_ID=OPENMASTER
============================================
/bin/bash: build/tools/findleaves.py: Permission denied
/bin/bash: out/target/product/generic/clean_steps.mk: Permission denied
/bin/bash: out/target/product/generic/clean_steps.mk: Permission denied
/bin/bash: out/target/product/generic/previous_build_config.mk: Permission denied
/bin/bash: build/tools/findleaves.py: Permission denied
frameworks/policies/base/PolicyConfig.mk:22: *** No module defined for the given PRODUCT_POLICY (android.policy_phone).  Stop.

I have tried to build it from root as well but this error is still same. When i give the mount command the output is 

/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kazim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kazim)
/dev/sda6 on /media/E600E6E500E6BBA5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

Kindly tell me how can i remove this permission problem. I will really appreciate any of your help.

---

### Post by Spyderkid on 2010-12-16
try and put sudo at the beginning of the command

---

### Post by Kazimalik on 2010-12-16
I have tried by putting sudo at beginning but error is still the same.

---

### Post by Spyderkid on 2010-12-16
Do this very selectively and do not overuse (running as root)

>try putting   ```
*sudo su  *
```    at the beginning of a command

>also you can try      ```
*sudo -i*
```     at the beginning of a command

---

### Post by Kazimalik on 2010-12-16
SpyderKid,
The only command that i have to give is 'make' to build the code. I gave it as

sudo su
make

but still the error is same.

---

### Post by Spyderkid on 2010-12-16
do you need to do 
```

make clean

```
then 
```

make

```

---

### Post by Kazimalik on 2010-12-16
After giving these commands the output has not changed.

---

### Post by Kazimalik on 2010-12-17
Will changing permission of directory from nosuid to suid help in this case?

---

