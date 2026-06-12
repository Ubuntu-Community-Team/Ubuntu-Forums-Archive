---
title: "Slow boot -- fsck"
date: 2010-01-13
forum: General Help
---

### Post by rodrigo.toste.gomes on 2010-01-13
I'm having a small problem with ubuntu 9.10 Karmic.
I bought an SSD so I could boot faster and open programs faster, etc.
However, the boot up time isn't better, it's actually worst than my other laptop with a Hard Drive.
Recently, when installing burg, and enabling GRUB to work through console, I found the problem -- in every single boot, fsck is there.
Does anyone know why this happens? And does anyone know how to avoid this?

I'm using ubuntu 9.10 Karmic, 64 bit version.
If required, I'll post the output of any commands.

Thanks for the input!

---

### Post by Forbees on 2010-01-13
thats odd . . . 

when you installed the SSD you did a clean installation right?

---

### Post by drs305 on 2010-01-13
Disclaimer: No SSD knowledge.

You can use tune2fs (see the man page) to set how often fsck checks are performed on your partitions. However, if it is checking on every boot your system may be finding errors and not fully fixing them. I would recommend booting to a livecd and running a check on each partition. You can see if any errors are found and hopefully correct them.

You can also check how often your partitions are scheduled to be checked by running:
```

sudo tune2fs -l /dev/sdXY

```
The checking frequency is near the bottom of the output. Once your partitions are free of errors, you can set the frequency by days, mounts, etc.

---

### Post by Leppie on 2010-01-13
excuse my ignorance, but what's this "burg" you installed?

---

### Post by drs305 on 2010-01-13
> **Leppie said:**
> excuse my ignorance, but what's this "burg" you installed?

'burg' is a boot loader which currently allows better theming capabilities than the released versions of Grub/Grub 2. It is broadly based on GRUB and uses most of the same conventions. 

There is a very popular thread currently devoted to theming, with most of the recent posts devoted to burg.[http://ubuntuforums.org/showthread.php?t=1371288]("http://ubuntuforums.org/showthread.php?t=1371288")

---

### Post by Leppie on 2010-01-13
> **drs305 said:**
> 'burg' is a boot loader which currently allows better theming capabilities than the released versions of Grub/Grub 2. It is broadly based on GRUB and uses most of the same conventions. 

There is a very popular thread currently devoted to theming, with most of the recent posts devoted to burg.[http://ubuntuforums.org/showthread.php?t=1371288]("http://ubuntuforums.org/showthread.php?t=1371288")
cool, thanks for the explanation and links. i'll have a nice read ;)

---

### Post by s3a on 2010-01-13
I don't know if this will solve your problem but trying to check (and repair) the partition with System --> Administration --> gparted (through the live CD) wouldn't hurt.

---

### Post by rodrigo.toste.gomes on 2010-01-13
Forbees: Yes, fresh install.
drs305: I ran that program.
It says the file system is due for checking every 6 months.
Maximum mount count is 34, so it's not set to check at every reboot.
Error from previous fsck is most likely, however, it shows no error on boot fsck :/
s3a: Will try that now, will post reply here when I get anything.

Thanks for everyone who's contributed until now. Anyone got any more ideas?

---

### Post by rodrigo.toste.gomes on 2010-01-13
Continuation of my previous post:
Tried to run fsck from a live CD, no difference :/

---

### Post by rodrigo.toste.gomes on 2010-01-13
Ok, I found what was causing the fsck message!
It was fstab, on the last column, there was a one.
I changed it.
However, after having measured the time it took to boot, it was identical, around 30 seconds from the moment I chose the OS on grub. This feels like a lot of time to boot from an SSD, especially since other laptops with HDs boot faster :/
Is there any log where I can see what happens from the moment I choose the OS on grub, or any way I can tell grub to be verbose?
Messages do appear on the screen, but only after a while, as it remains most of the time as a prompt where I can't write.
Maybe knowing what it does in that time could help me to shorten the boot time.

Thanks for any input.

---

### Post by drs305 on 2010-01-13
> **rodrigo.toste.gomes said:**
> Ok, I found what was causing the fsck message!
It was fstab, on the last column, there was a one.
I changed it.

What you have done is disabled the fsck check. So you have hidden the problem rather than solved it. 0 (or probably nothing, I don't know what happens when there is no entry) omits the check, 1 runs the check first when it is due, and 2 runs the check after performing the checks on partitions set at 1.

> 
Is there any log where I can see what happens from the moment I choose the OS on grub, or any way I can tell grub to be verbose?
Messages do appear on the screen, but only after a while, as it remains most of the time as a prompt where I can't write.
Maybe knowing what it does in that time could help me to shorten the boot time.

You can check the contents of /etc/default/grub. If you have the following:
> GRUB_CMDLINE_LINUX_DEFAULT="[COLOR="DarkRed"]**quiet**[/COLOR] splash"
If you have "quiet" you can remove it (and splash if you don't want the splash image) and then see the messages, although they can scroll by pretty quickly.

If you make any change to /etc/default/grub, run "sudo update-grub" afterward to incorporate the changes before rebooting.
Thanks for any input.[/QUOTE]

---

### Post by Leppie on 2010-01-13
> **rodrigo.toste.gomes said:**
> Is there any log where I can see what happens from the moment I choose the OS on grub...
there's dmesg:
```
dmesg
```

or if you want something more detailed:
```
less /var/log/dmesg
```

---

### Post by rodrigo.toste.gomes on 2010-01-13
Tried your suggestions, and was able to see what happened.
There was nothing wrong, and no specific process causing the slow booting.
It's probably just the hardware that is causing this then.
It just felt slow, but it seems that it's the computer.
Thanks for your help and suggestions. I'm declaring this solved :P

---

### Post by oldfred on 2010-01-13
There is also bootchart in the repository.

bootchart allows you to audit the boot sequence of your computer and
generate a pretty chart of the processes run, including how long they
took and how much CPU and I/O they used.

You can also see dmesg and other logs in the log view viewer.
/system/administration/log file viewer

---

### Post by rodrigo.toste.gomes on 2010-01-13
Thanks for the tip!
So, before I mark this as solved, I'd like anyone's input on my bootchart! Unfortunately I don't know how to read it :S
Anyone see anything wrong or that can be improved?

---

### Post by mirach on 2010-01-13
The slow boot in Karmic may be due to a libatasmart bug described here:

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852?comments=all]("https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852?comments=all")

I tried the temporary workaround for this problem and and my boot time went from over two minutes to 32 seconds - Faster than Jaunty, faster than with the factory installed STEC 4GB SSD. Everything seems to run fine.

Mini 9, Super Talent FEM16GFDL, Ubuntu 9.10 lpia.

---

### Post by rodrigo.toste.gomes on 2010-01-14
Thanks for the suggestion, but it doesn't seem to have had any effect.

---

