---
title: "Target filesystem doesn't have /sbin/init."
date: 2009-11-02
forum: General Help
---

### Post by SametAras on 2009-11-02
[FONT=Courier New]Hello,

I'm using Ubuntu 9,4. Very good system, But the system returns an error. Here:

```
Boot from(hd0,0) ext3 ...
Starting up ...
Loading, please wait..
19+0 records in
19+0 records out

kinit: name_to_dev_t(/dev/disk/by-uuid/756.....)
kinit: trying to resume from /dev/disk/by-uuid/756.....
kinit: No reume image, doing normal boot...
mount: mounting /dev/disk/by-uuid/267... on /root failed Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init = bootarg.

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

```Please, help me. My got the important files on the system.


[/FONT][RIGHT][FONT=Courier New]Sincerely;[/FONT]
[FONT=Courier New]Samet Aras.[/FONT]
[/RIGHT]
[FONT=Courier New]
[/FONT]

---

### Post by Giblet5 on 2009-11-02
You can try reinstalling the boot-loader:

Boot from **9.04** live CD. Bring up a terminal window.

Run ```
sudo fdisk -l
```

Which extN device is your / filesystem? Let's assume it's /dev/sda2:

```
sudo mount /dev/sda2 /mnt -text
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo chroot /mnt bash ## DANGEROUS! ENTER COMMANDS EXACTLY!
update-grub
grub-install /dev/sda
exit
sudo reboot
```

Did that fix it? Are you gonna name your first-born child "Giblet5"?

If you get errors, or can't find the / device, just post the output of the 'fdisk -l' command above.

---

### Post by SametAras on 2009-11-02
[FONT=Courier New]Hello,

Very thank you. But in Ubuntu screen not check driver. Here:

```

Unclean shutdown checking drivers:
/dev/sda1 %70 (stage 1/5 287/287)

```

Takes 1 minute. And a terminal screen:

```
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)

* An automatic file system check(fsck) of the root filesytem failed.
A manul fsck must be performed, then the system restarted.
The fsck should be performed in mantenance mode with the
root filesystem mounted in read-only mode.

* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performin system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
root@samet:~#

```

Please, help me.

[/FONT][RIGHT][FONT=Courier New]Sincerely;[/FONT]
[FONT=Courier New]Samet Aras.[/FONT]
[/RIGHT]
[FONT=Courier New]
[/FONT]

---

### Post by SametAras on 2009-11-02
[FONT=Lucida Console]Hello,

My error is solved. And very thank you. Here, I wrote command:

```

fsck -y /dev/sda1

```


[/FONT][RIGHT][FONT=Lucida Console]Sincerely;[/FONT]
[FONT=Lucida Console]Samet Aras.[/FONT]
[/RIGHT]

---

### Post by tech9 on 2009-12-18
> **Giblet5 said:**
> Are you gonna name your first-born child "Giblet5"?

answering for him - H-C no!

---

