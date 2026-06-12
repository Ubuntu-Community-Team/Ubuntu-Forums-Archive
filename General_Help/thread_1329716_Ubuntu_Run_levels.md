---
title: "Ubuntu Run levels"
date: 2009-11-17
forum: General Help
---

### Post by A_M_S on 2009-11-17
Hello
What is exactly the purpose of run levels?

Run level 0 stands for shutdown
Run level 6 stands for reboot

Ubuntu uses by default run level 2. 

Is there any use for the run levels 3-5 in Ubuntu?


Thanks.

---

### Post by 0cton on 2009-11-17
[http://lmgtfy.com/?q=runlevel](http://lmgtfy.com/?q=runlevel)

---

### Post by sisco311 on 2009-11-17
Ubuntu, since Edgy (6.10), uses Upstart as a replacement for the traditional init-process. You can still use the traditional init scripts and Upstart's SysV-rc compatibility tools to start services and emulate runlevels.

[http://en.wikipedia.org/wiki/Runlevel]("http://en.wikipedia.org/wiki/Runlevel")

runlevels 3-5 are not used by default, but you can write your own scripts or Upstart jobs and start them on runlevel 3,4 or 5.

You can also add a custom grub entry to boot directly in runlevel 3, 4 or 5.

Just append the linux(grub2) line or kernel (grub) line with 3, 4 or 5.

i.e. (in >= Karmic) you can edit the gdm Upstart job
 /etc/init/gdm.conf:
```
description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

start on (**runlevel [3]**
          and filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0**2**16]
```

to start it on runlevel 3. by default the computer will boot in text-mode. Then you can start gdm by entering in runlevel 3.

grub 2 entry:
```
menuentry "Ubuntu, Linux 2.6.32-4-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f36ae9ca-b10d-49d5-8323-f5f7e63dcc69
	linux	/boot/vmlinuz-2.6.32-4-generic root=UUID=f36ae9ca-b10d-49d5-8323-f5f7e63dcc69 ro quiet splash **3**
	initrd	/boot/initrd.img-2.6.32-4-generic
}

``` 
[thread=1302743]GRUB 2 - 5 Common Tasks[/thread]

---

### Post by A_M_S on 2009-11-17
Tnx for the replies :)

---

### Post by Blond_Knight on 2009-11-23
Im sure everyone here knows more about Linux or is more well informed than me, but I dont like the move from the traditional init-process to Upstart.  I think moving away from the way Debian does things, unless the official Debian release is using Upstart also, is a bad idea and hurts cross-compatability.

[edit]
OK I see that Fedora and Debian are starting to use Upstart, and it does have some interesting features. Its just that the pace of change is so darn fast.

---

### Post by sisco311 on 2009-11-23
> **Blond_Knight said:**
> Im sure everyone here knows more about Linux or is more well informed than me, but I dont like the move from the traditional init-process to Upstart.  I think moving away from the way Debian does things, unless the official Debian release is using Upstart also, is a bad idea and hurts cross-compatability.

[edit]
OK I see that Fedora and Debian are starting to use Upstart, and it does have some interesting features. Its just that the pace of change is so darn fast.

Upstart is able to run sysvinit scripts unmodified. Easy transition and perfect backwards compatibility with sysvinit were explicit design goals.

Fast? Ubuntu uses Upstart since 2006 (6.10 Edgy Eft). 

from [http://lists.debian.org/debian-devel-announce/2009/09/msg00003.html]("http://lists.debian.org/debian-devel-announce/2009/09/msg00003.html")

> ...
The problem is fundamental to the way we boot Debian today - sequentially, and a solution needs to address this fundamental problem. We believe the solution is to migrate to an event based boot system.
...

To solve the fundamental problem, the plan is to replace /sbin/init with an implementation that is able to handle kernel events. It will allow us to modify the boot system for the early boot to become event based, while keeping the existing boot stuff working. We could rewrite sysvinit to become event based, or have a look at the existing boot systems that handle kernel events. After checking the options and the systems used in other distributions, upstart seems like the most promising candidate. It is used by Ubuntu and Fedora at the moment, and solves the problem in a backwards compatible way. The plan is to change upstart to actually use /etc/inittab, to ease the switch between sysvinit and upstart. We will also change the init.d script handling to treat upstart jobs as init.d scripts, to provide an
alternative for architectures lacking upstart support. These changes should make it transparent for the users which package provides /sbin/init, and thus make it easier to migrate from sysvinit to upstart.


---

### Post by Blond_Knight on 2009-11-23
Since Edgy may be true but I havent been forced to use Upstart until now.

---

### Post by sisco311 on 2009-11-23
> **Blond_Knight said:**
> Since Edgy may be true but I havent been forced to use Upstart until now.

You can still write/use System-V style init scripts.

---

### Post by igoddard on 2009-11-26
> **sisco311 said:**
> Ubuntu, since Edgy (6.10), uses Upstart as a replacement for the traditional init-process. You can still use the traditional init scripts and Upstart's SysV-rc compatibility tools to start services and emulate runlevels.


Is there any documentation for upstart?  Here on Hardy man upstart still finds nothing.  Is it yet another typical open source effort where documentation follows on later when, or, as is too often the case, if someone gets round to writing it?

---

### Post by sisco311 on 2009-11-26
> **igoddard said:**
> Is there any documentation for upstart?  Here on Hardy man upstart still finds nothing.  Is it yet another typical open source effort where documentation follows on later when, or, as is too often the case, if someone gets round to writing it?

In pre-Karmic releases Upstart is only used to start the virtual consoles and to run the sysinitv scripts (/etc/init.d).

I found this guide very useful:
[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")

upstart wiki:
[http://upstart.ubuntu.com/wiki/]("http://upstart.ubuntu.com/wiki/") 

NOTE: some features may not be implemented in the version used by Hardy.

---

### Post by A_M_S on 2009-11-28
> **sisco311 said:**
> In pre-Karmic releases Upstart is only used to start the virtual consoles and to run the sysinitv scripts (/etc/init.d).


So the Upstart functions in Karmic have been extended?

---

### Post by sisco311 on 2009-11-28
> **A_M_S said:**
> So the Upstart functions in Karmic have been extended?

Yep, most of the sysinitv scripts (/etc/init.d) are replaced by upstart jobs(/etc/init) .

---

