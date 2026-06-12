---
title: "major boot problems"
date: 2011-03-03
forum: General Help
---

### Post by kingdraco41 on 2011-03-03
I've been using ubuntu 10.04 for a couple of months, and there hasn't been any major problem that I couldn't fix with a search until now. When I try to boot, I get stopped at initramfs, which has a code that states:
```

mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory

```
 
This problem occurs when I load I any of my kernels:
```

2.6.32.28-generic
2.6.32.28-generic [recovery mode]
2.6.32.24-generic 
2.6.32.24-generic [recovery mode]

```
 
As I have been suggested that the problem is being caused by grub not being able to find my operating system, I've tried typing these commands into the grub ((hd0,1) and sda1 are my hard drives): 
```

set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

```
 
While that does not fix it, it does give me a "Done:" message on the initramfs screen after failing to mount /dev. That is the only change of which I am aware. My first wish is to try and solve this without having to reinstall lucid entirely.
 
When I could not find any more information concerning that, I tried to boot ubuntu from an external hard drive and backup the files then reinstall ubuntu. However, I encountered two hair-removing problems there. Firstly, I cannot mount the hard drive. After about thirty minutes attempting to mount, it gives me an error message: 
```

DBus error org.freedesktop.DBus.Error.NoReply: 
Did not receive a reply. Possible causes include: 
the remote application did not send a reply, the 
message bus security policy blocked the reply, 
the reply timeout expired, or the network connection 
was broken.

```
 
I have tried to (I believe) force the mount with:
```

sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu -o force

```
but this is the command which I gave up on after 6 hours of no development. I am not very knowledgeable about mounting.
 
My second problem with backing up and reinstalling ubuntu is that the liveCD does not work on the computer in question. I get no specific error message, but it doesn't move after skipping the "nonexistent" package files, saying I should repeat this process with my other discs. However, the disc itself is not at fault; I have been able to boot the same disc on another computer and even get ubuntu installed. This all, of course, means that, even if I were to become so frustrating to decided to sod it all and erase all my precious data, I would be unable to do so.
 
Shortly before this began (and I think this may have been the cause of the issue) I noticed that my computer would not shut down. I would command it to do so, but it would hold on the little "ubuntu" screen with the circles. I eventually decided to cold shutdown my computer. My laptop still does this, even when I use my external hard drive. 
 
I find it hard to believe that these major bugs are unrelated, so I suspect that some basic software is at fault, but I'm not familiar with grub and initramfs, so I don't know exectly what is wrong. If anybody could give me insight and advice, it would be much apreciated.

---

### Post by jbiggs12 on 2011-03-03
dev, sys, and proc are (i'm fairly certain) virtual directories, so they're apparently not being created before you try to access them. could you show the contents of /etc/fstab, and out of curiosity how old is your hard drive?

---

### Post by kingdraco41 on 2011-03-03
It's fairly recent - around 2007 or 6. I cannot get into fstab. Init cannot find it. And I can't mount the drive externally, either.

---

### Post by kingdraco41 on 2011-03-03
I think the problem lies with the hard drive itself. When i try to mount the drive in init, with:
```

mkdir /mnt
mount /dev/sda1 /mnt

```
it tries to mount, but never succeeds. It doesn't give an error message either - just keeps going for eternity. However, if the hard drive is screwed up, I would think that I wouldn't be able to boot it at all.

---

