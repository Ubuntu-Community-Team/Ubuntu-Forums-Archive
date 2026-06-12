---
title: "Dual Boot running extremely slow"
date: 2010-08-12
forum: General Help
---

### Post by JHaimson on 2010-08-12
Hi. I recently attempted to set up my laptop (Sony Vaio VGN FS850) to dual boot Windows XP Professional and Ubuntu 10.04 LTS. I set everything up following this tutorial: [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

When I try to boot into Ubuntu though, it took me 17 minutes to get to a workable desktop. And once I was there it takes about 3 minutes to open an application like OpenOffice. Everything runs at decent speeds once it is open but that is still ridiculously slow speeds. I was expecting the 15 second boot times that I had heard about. Does anyone know why this might be happening and how to fix it?

---

### Post by oldfred on 2010-08-12
If you want the 15sec boot time, I assume you have upgraded to a large SSD.:)

My system takes about a minute but I have several NTFS & FAT partitions that I mount and 3 drives. All the extras you have to load in the way of drivers slows down boot.

How much memory do you have. The more the better for any system. 
requirements:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Several years ago I installed the then current version of Ubuntu on a low memory system. It did install but was very slow. There are versions that work better for low memory.

---

### Post by JHaimson on 2010-08-12
I have 2 GB of RAM which is double the suggested requirements and I have a 1.86 GHZ Processor which is also more than needed. So I don't see why its sooo slow. I have one hard drive with one NTFS partition for windows and one ext3 partition for Linux. Then I also have a very small recovery partition that came pre-loaded on the laptop. The odd thing is that most of the boot-up time is spent on a blank black screen and then once Ubuntu comes up it only takes 2-3 minutes (which is still a lot longer than I expected). So I think it is a problem with the Bootloader right?

---

### Post by JHaimson on 2010-08-12
Ok, I updated Ubuntu, and now the applications and everything run at normal speed, but the boot time is still upwards of 10 minutes which is ridiculous. I'm not sure which bootloader it is, I think Grub right? It's whatever is default on Ubuntu 10.04 LTS and I'm almost certain that that is where my problem lies.

---

### Post by oldfred on 2010-08-12
If you are past the grub menu then it is not grub but some device not loading and eventually timing out.

Have you looked in your log files. They show times and any long time between entries or repeating errors/warnings or attempts at something will tell what may be the problem.

system, administration, log file viewer. I look at all of them but messages & kern.log may have more booting info. The log file called boot log is not turned on normally, and used to cause issues if on.

---

### Post by JHaimson on 2010-08-14
Here are all of the warnings I could find.
```

Aug 13 12:27:32 josh-laptop gdm-binary[753]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 13 12:27:32 josh-laptop gdm-simple-slave[957]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 13 12:27:32 josh-laptop gdm-binary[753]: WARNING: Unable to find users: no seat-id found
Aug 13 12:27:32 josh-laptop acpid: client connected from 982[0:0]
Aug 13 12:27:32 josh-laptop acpid: 1 client rule loaded
Aug 13 12:27:35 josh-laptop gdm-session-worker[1099]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory

Aug 13 12:27:43 josh-laptop gdm-simple-greeter[1097]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Aug 13 12:28:14 josh-laptop gdm-session-worker[1099]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

```


It seems like this was eating up a bunch of time as well.
```

Aug 13 12:27:37 josh-laptop rtkit-daemon[1147]: Sucessfully called chroot.
Aug 13 12:27:37 josh-laptop rtkit-daemon[1147]: Sucessfully dropped privileges.
Aug 13 12:27:37 josh-laptop rtkit-daemon[1147]: Sucessfully limited resources.
Aug 13 12:27:37 josh-laptop rtkit-daemon[1147]: Running.
Aug 13 12:27:37 josh-laptop rtkit-daemon[1147]: Watchdog thread running.
Aug 13 12:27:37 josh-laptop rtkit-daemon[1147]: Canary thread running.
Aug 13 12:27:39 josh-laptop rtkit-daemon[1147]: Supervising 1 threads of 1 processes of 1 users.
Aug 13 12:27:41 josh-laptop kernel: [  208.096026] eth1: no IPv6 routers present
Aug 13 12:27:42 josh-laptop rtkit-daemon[1147]: Supervising 2 threads of 1 processes of 1 users.
Aug 13 12:27:42 josh-laptop rtkit-daemon[1147]: Supervising 3 threads of 1 processes of 1 users.
Aug 13 12:28:40 josh-laptop rtkit-daemon[1147]: Supervising 4 threads of 2 processes of 2 users.
Aug 13 12:28:41 josh-laptop rtkit-daemon[1147]: Supervising 5 threads of 2 processes of 2 users.
Aug 13 12:28:41 josh-laptop rtkit-daemon[1147]: Supervising 6 threads of 2 processes of 2 users.
Aug 13 12:28:48 josh-laptop rtkit-daemon[1147]: Supervising 4 threads of 2 processes of 1 users.
```

---

### Post by oldfred on 2010-08-14
I do not have a custom.conf. Did you do something special on your graphics setup? I would undo that and see if it boots quicker.

In logs did you have any large gaps in time. I do not see huge time gaps in what your posted, but that is about 45secs, where is the minutes of lost time booting?

---

