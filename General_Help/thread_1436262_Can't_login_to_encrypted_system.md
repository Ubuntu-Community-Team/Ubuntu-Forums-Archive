---
title: "Can't login to encrypted system"
date: 2010-03-22
forum: General Help
---

### Post by petri on 2010-03-22
I have Ubuntu 9.04 and I have encrypted swap, root partitions and two internal hard drives with this howto: [http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04). 

It's been working about a year now but after an routine fsck (when Ubuntu starts) I can't log in no more. After first passphrase (must be the root partition) the scrolling thingy stops and "Caps lock" and "Scroll lock" starts to blink and nothing happens.

Anyone know what to do now? I have two 1 TB drives full of data which I can't get in to.

---

### Post by petri on 2010-03-23
This is what I got when I start in Recovery mode:
```

Init: Error parsing configuration: Not a directory
      4.648826]Kernal panic - not syncing.  Attempted to kill init!
      4.648901] Dumping ftrace buffer:
      4.648961] ftrace buffer empty
```

I found same problem [here]("http://crunchbanglinux.org/forums/topic/6470/solved-how-do-i-boot-to-a-command-line/") but my skills doesn't manage how to set password for sudo (I'm running LiveCD from USB stick).

Anyone?

---

### Post by bodhi.zazen on 2010-03-23
Hard to know from what you have posted.

I would boot a live CD.

Is there any problem with grub or your /boot partition ?

You can then install LUKS and mount and check the root file system.

[http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)

Once you have decrypted the file system, you can run fsck on it.

---

### Post by petri on 2010-03-24
Thanks LiveCD works I now get access to my files and move them.

But I can't run fsck after mounting. I'm getting same message like this
```

root@ubuntu:/home/ubuntu# fdisk '/media/0adc9a9d-c59d-43d7-9ff1-afc55e6b1753'
last_lba(): I don't know how to handle files with mode 40777
You will not be able to write the partition table.

Unable to read /media/0adc9a9d-c59d-43d7-9ff1-afc55e6b1753
root@ubuntu:/home/ubuntu# 
``` Before that I changed "Permissions" to "Create and delete files" for all.

I did sudo su to get root in live because ```
ubuntu@ubuntu:~$ sudo fdisk '/media/0adc9a9d-c59d-43d7-9ff1-afc55e6b1753'
``` gave same answer

---

### Post by bodhi.zazen on 2010-03-24
Back up your data first.

Then unmount the partition 

And run fsck (not fdisk) on the unmounted partition

fsck -y /dev/mapper/your_partiton

---

### Post by petri on 2010-04-03
I finally managed to run fsck but it didn't solve the problem. Reinstallation was needed as I wrote here: [http://ubuntuforums.org/showthread.php?t=1445220&highlight=root+partition+encrypted+drives](http://ubuntuforums.org/showthread.php?t=1445220&highlight=root+partition+encrypted+drives)

---

