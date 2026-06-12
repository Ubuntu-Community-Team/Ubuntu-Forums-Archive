---
title: "Bunch of broken stuff?"
date: 2009-11-05
forum: General Help
---

### Post by stuartbh on 2009-11-05
Hello all!

I am new to Ubuntu and have some several questions regarding its everyday usage.

1) Follows hereupon the command and associative responsa I received when attempting to prepare the system for the execution of "zerofree" while in single user mode:

# mount -n -o remount,ro -t ext4 /dev/sda1 /

towit I was met with the response:

mount: / is busy

Any ideas why this did not work?


2) Every Unix since "the beginning of time" has been able to easily move form runlevel 3 (Full multi-user with TUI) to runlevel 5 (Full multi-user with GUI), and vice versa (using the "init" or "telinit" commands).

I booted into single user mode recently from Ubuntu 9.10, and then told it to "resume booting". When it did I ended up in TUI (runlevel 3) mode. While I thought this somewhat strange (figuring resuming a boot would resume to boot as if I had not gone into single user mode, and expected to end up in runlevel 5 with a full GUI), I was further shocked to see that when I attempted both "init 5" and "telinit 5", which seemed (according to the runlevel command) to have raised the system to runlevel 5, but it did not bring up the GUI, what is broken?

It is notable that I am running Ubuntu 9.10 64-bit, and have tried this under both VirtualBox and VMware 3.0 softwares.


Thanks,

Stuart

---

### Post by VolkerLanz on 2009-11-06
> **stuartbh said:**
> # mount -n -o remount,ro -t ext4 /dev/sda1 /

towit I was met with the response:

mount: / is busy

Any ideas why this did not work?


It says it right there: Because the file system is busy. There are open files, I'd guess. lsof or fuser will tell you.

> **stuartbh said:**
> ... I was further shocked to see that when I attempted both "init 5" and "telinit 5", which seemed (according to the runlevel command) to have raised the system to runlevel 5, but it did not bring up the GUI, what is broken?

Ubuntu 9.10 doesn't use SysV-Init anymore. Try

```
# service gdm start
```

or

```
# service kdm start
```

if you're running Kubuntu.

---

