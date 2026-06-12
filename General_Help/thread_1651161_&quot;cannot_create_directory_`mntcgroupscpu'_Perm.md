---
title: "&quot;cannot create directory `/mnt/cgroups/cpu': Permission denied&quot; error in terminal"
date: 2010-12-22
forum: General Help
---

### Post by behnaam on 2010-12-22
Hi,

I recently switched from Ubuntu Maverick 32-bit to 64-bit so I could compile Android's latest revision, Gingerbread.

Everything went pretty smoothly and I managed to fix most issues that was caused due to the switch.

But each time I open terminal, the following error shows up:
```
mkdir: cannot create directory `/mnt/cgroups/cpu': Permission denied
bash: /mnt/cgroups/cpu/19088/notify_on_release: No such file or directory
bash: /mnt/cgroups/cpu/19088/tasks: No such file or directory
```

I've searched for any bugreports or anything actually that might suggest that someone else had this issue, but without any success. I've tried manually creating that directory as root but the error remains.

Anybody out there that might be able to help me or give me hints of what is causing this error?

Thanks in advance! :)

---

### Post by TSJason on 2010-12-22
It looks like you partially installed the cgroup optimizations that have been circulating around lately. You can either remove the lines causing those errors from your ~/.bashrc file -OR- you can fix the install by modifying those lines in ~/.bashrc to be:

```
if [ "$PS1" ] ; then
mkdir -p -m 0700 /dev/cgroup/cpu/user/$$ > /dev/null 2>&1
echo $$ > /dev/cgroup/cpu/user/$$/tasks
echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi
```

add the following to /etc/rc.local:

```
mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent
```

and 

```
sudo bash -c "echo '
#!/bin/sh
if [ "$*" != "/user" ]; then
rmdir /dev/cgroup/cpu/$*
fi' > /usr/local/sbin/cgroup_clean
```

**Protip**: if you can't find the lines in your ~/.bashrc then check /etc/bash.bashrc

Either reboot, or run the lines in rc.local as root to apply them.

---

### Post by behnaam on 2010-12-22
> **TSJason said:**
> It looks like you partially installed the cgroup optimizations that have been circulating around lately. You can either remove the lines causing those errors from your ~/.bashrc file -OR- you can fix the install by modifying those lines in ~/.bashrc to be:

```
if [ "$PS1" ] ; then
mkdir -p -m 0700 /dev/cgroup/cpu/user/$$ > /dev/null 2>&1
echo $$ > /dev/cgroup/cpu/user/$$/tasks
echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi
```

add the following to /etc/rc.local:

```
mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent
```

and 

```
sudo bash -c "echo '
#!/bin/sh
if [ "$*" != "/user" ]; then
rmdir /dev/cgroup/cpu/$*
fi' > /usr/local/sbin/cgroup_clean
```

**Protip**: if you can't find the lines in your ~/.bashrc then check /etc/bash.bashrc

Either reboot, or run the lines in rc.local as root to apply them.

You sir, are awesome :)

I patched my kernel with the shed autogroup patch, so you're fully right about that being the cause of this issue. 

Thank you again, merry Christmas and a Happy New Year!

---

