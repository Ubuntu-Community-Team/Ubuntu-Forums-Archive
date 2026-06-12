---
title: "problems locating /proc directory"
date: 2012-02-17
forum: General Help
---

### Post by danielbbuchanan on 2012-02-17
Ubuntu 11.10 (new install; not an upgrade) is having issues finding /proc directory. I ran mount and the directory is mounting on boot. In gedit when I double click on the /proc directory, it never does find/list all the files/directories in its tree. And I am unable to save a new file to that directory. This problem started when I was looking at files in asound trying to figure out why my usb speakers have no controls on alsamixer. I started getting msgs when I would close a file in /proc/asound that "file had changed disks; reload or cancel". I have attached a copy of my /etc/fstab file:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=4e4d90ff-2db2-4a48-8d43-595f49dc079a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1a141333-4893-4bd7-98cc-d580edfa17f2 none            swap    sw              0       0

I am not sure where to go from here. I wonder if this /proc directory issue has something to do with why alsamixer does not assign any mixer controls to my two usb cards. The other two cards have a codec in their file tree. The usbmixer files in the two usb cards file trees are empty except for the description of the card. Anybody have any suggestions what I do next ??

---

### Post by dcstar on 2012-02-18
> **danielbbuchanan said:**
> Ubuntu 11.10 (new install; not an upgrade) is having issues finding /proc directory.
........

/proc is a **System Folder** that is totally controlled by the system **and not you**. It contains system data of loaded processes.

You cannot "save" files to it as the kernel controls it, and I have never, ever seen an entry for in in a fstab file.

---

### Post by danielbbuchanan on 2012-02-18
I thought I read somewhere that fstab contains the mount instructions for the file system /proc. And the system would not allow a remount unless an error for that particular mount was in the fstab file. I think you can save files in /proc if you change the permissions but you have to save the file in the mirror also as /proc is a virtual file system that merely replicates what your actual file system/operands look like at that given time. Maybe I am not understanding this correctly.

---

### Post by Khayyam on 2012-02-18
> **danielbbuchanan said:**
> I thought I read somewhere that fstab contains the mount instructions for the file system /proc. And the system would not allow a remount unless an error for that particular mount was in the fstab file. I think you can save files in /proc if you change the permissions but you have to save the file in the mirror also as /proc is a virtual file system that merely replicates what your actual file system/operands look like at that given time. Maybe I am not understanding this correctly.

The /proc filesystem is populated at boot by the kernel, it is its own '**proc**ess' structured in the form of a (virtual) filesystem. This allows userland to interface with the kernel, and offers a means whereby runtime changes can be made to certain kernel features. As this filesystem is 'virtual' it is not written to in the normal sense, but it is writeable, parameters can be inserted into /proc to effect changes, and /etc/sysctl.conf exists to set these changes over reboots.

So, /proc being a virtual filesystem is not 'mounted', and there is no "changing permissions" on it (via fstab). Its managed by the kernel, and will allow certain content of files to be altered, but its structure is mostly read-only.

I find your understanding/description a little confusing so I'm not sure I'm answering to you question here. Suffice to say, /proc mostly takes care of itself. If you need  to modify it in anyway this can be done via sysctl.conf and or 'echo value > /proc/path/file.'

HTH ... khay

---

### Post by danielbbuchanan on 2012-02-18
Thanks for the response and info. I will do some reading right now around /etc/sysctl.conf and echo value.....; maybe I will find a solution to my problem in that information. Reboot does not solve the problem; gedit still will not list the contents of /proc directory neither by search or by double click on the directory name. I am fairly certain that, even if the files within are all read only, gedit should still list the contents of the /proc directory when asked to. Thanks again for your help and advice.

---

### Post by dcstar on 2012-02-18
> **danielbbuchanan said:**
> Thanks for the response and info. I will do some reading right now around /etc/sysctl.conf and echo value.....; maybe I will find a solution to my problem in that information. Reboot does not solve the problem; gedit still will not list the contents of /proc directory neither by search or by double click on the directory name. **I am fairly certain that, even if the files within are all read only, gedit should still list the contents of the /proc directory when asked to**. Thanks again for your help and advice.

Gedit **does** list the files on a normal system in /proc. Your system is obviously not normal with that rubbish in /etc/fstab.

---

### Post by danielbbuchanan on 2012-02-20
I'm not seeing any advice or solution in your response. I would appreciate if you did not use this forum to be critical and judgemental. The forum is not here for that purpose. Now I ignored your "and not you" bold print in your first response. Clearly this response has ill intention also. Moving forward, I would appreciate no response from you unless it contains useful guidance and direction in solving the problem at hand. Thanks.

---

### Post by Khayyam on 2012-02-20
I think what dcstar means to say is that your fstab shouldn't have all the options you have provided. It should read:

```
proc /proc proc defaults 0 0
```

Also, there is no reason to use gedit. If you want to set 'tcp_syncookies' then:

```
sudo echo "1" > /proc/sys/net/ipv4/tcp_syncookies
```

or edit /etc/sysctl.conf

```
net.ipv4.tcp_syncookies=1
```

You should **know** what your doing before changing anything in /proc and as you seem to think that changing something in proc will get a control for your usb speakers to show up in alsamixer, then this isn't the case. As I said, /proc is simply the kernels processes structured in the form of a (virtual) filesystem, its not something you can 'edit' and having hardware suddenly recognised. Your problem is more than likely the fact that the usb speakers have no driver (does 'dmesg' show them registered?). Does "usb_audio" recognises them as a sound device?

HTH ... khay

---

### Post by danielbbuchanan on 2012-02-21
Thanks for the info. Yes, now I do know the purpose of /proc file system  and how I am to interact with these files. I did a new install and my  fstab file again has this swap data which apparently is coming from the  install. Maybe something with my partitions is going on at install that  is causing these changes to be noted in fstab. My sound cards are all  recognized and show up as hardware/options in System/Settings/Sound and  each one of them works. aplay -l and -L show each sound card although _one of the usb cards keeps ending up at card 0 slot which I can not seem to get changed ??_ sudo alsamixer only has slider controls for the audio and video inboard cards. _The  usb cards say "this sound device has no controls" where the control  sliders should be and indicate neither of the cards have any playback or  capture ability ??_ although they both have a volume control and  playback and capture in Systems/Setting/Sound. And again, after a new  install, this problem also is still present and again, I  can not search for a file in gedit; i get a GTK Bug....tracker error and  the search does not process, and again I am unable to see the contents  of the /proc directory. I am starting to think that my install disc is  corrupt. I am starting to get sorta frustrated. Here is the dmesg info related to one of the devices; it does show it is registered (right??):

[    2.781549] input: Logitech Logitech Wireless Speaker Z515 as  /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1.1/1-1.1:1.2/input/input6
[    2.781706] generic-usb 0003:046D:BA10.0002: input,hiddev0,hidraw1:  USB HID v1.11 Device [Logitech Logitech Wireless Speaker Z515] on  usb-0000:00:12.2-1.1/input2
[    2.853087] usb 1-1.2: new high speed USB device number 4 using ehci_hcd
[    3.233146] usb 1-1.3: new high speed USB device number 5 using ehci_hcd
[   10.886328] udevd[332]: starting version 173
[   10.913202] lp: driver loaded but no devices found
[   10.967565] acpi device:40: registered as cooling_device2

Any help or advice would be appreciated...Thanks.

---

### Post by roelforg on 2012-02-21
> **danielbbuchanan said:**
> Thanks for the info. Yes, now I do know the purpose of /proc file system  and how I am to interact with these files. I did a new install and my  fstab file again has this swap data which apparently is coming from the  install. Maybe something with my partitions is going on at install that  is causing these changes to be noted in fstab. My sound cards are all  recognized and show up as hardware/options in System/Settings/Sound and  each one of them works. aplay -l and -L show each sound card although _one of the usb cards keeps ending up at card 0 slot which I can not seem to get changed ??_ sudo alsamixer only has slider controls for the audio and video inboard cards. _The  usb cards say "this sound device has no controls" where the control  sliders should be and indicate neither of the cards have any playback or  capture ability ??_ although they both have a volume control and  playback and capture in Systems/Setting/Sound. And again, after a new  install, this problem also is still present and again, I  can not search for a file in gedit; i get a GTK Bug....tracker error and  the search does not process, and again I am unable to see the contents  of the /proc directory. I am starting to think that my install disc is  corrupt. I am starting to get sorta frustrated. Here is the dmesg info related to one of the devices; it does show it is registered (right??):

[    2.781549] input: Logitech Logitech Wireless Speaker Z515 as  /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1.1/1-1.1:1.2/input/input6
[    2.781706] generic-usb 0003:046D:BA10.0002: input,hiddev0,hidraw1:  USB HID v1.11 Device [Logitech Logitech Wireless Speaker Z515] on  usb-0000:00:12.2-1.1/input2
[    2.853087] usb 1-1.2: new high speed USB device number 4 using ehci_hcd
[    3.233146] usb 1-1.3: new high speed USB device number 5 using ehci_hcd
[   10.886328] udevd[332]: starting version 173
[   10.913202] lp: driver loaded but no devices found
[   10.967565] acpi device:40: registered as cooling_device2

Any help or advice would be appreciated...Thanks.

Please post a new thread instead of threadjacking this one.

---

