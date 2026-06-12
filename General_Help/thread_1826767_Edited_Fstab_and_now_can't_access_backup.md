---
title: "Edited Fstab and now can't access backup"
date: 2011-08-17
forum: General Help
---

### Post by beenny on 2011-08-17
Hello,

I tried editing my /etc/fstab to configure for SSD. I made a backup file in case things went wrong (fstab.bak). When I tried to reboot i got a screen saying:

```

An error occured while mounting /
press S to skip mounting or M for Manual recovery

```

I press M and get a terminal with:

```

Root filesystem check failed.
A maintenance shell will now be started
Control-D will terminate this shell and reboot again

```

I then try:
```

root@bgWorkLaptop:~#sudo cp /etc/ftsab.bal /etc/fstab
cp: cannot creat regular file '/etc/fstab' Read-only file system

```

Trying to edit my fstab in VI gives me the same issue.

Below is a copy of my backup fstab:

```

...
proc /proc proc nodev,noexec,nosuid 0 0 
/dev/sda1 / ext4 errors=remoint-ro,user_xattr 0 1
#swap was on /dev/sda5 during installation
UUID=37c3ccea-c895-4437-8b62-706521474187b none swap sw o o 

```

I've searched around and while I've seen this issue with others I have not found a reliable solution to it. Is there anyway that I can just copy my backup fstab file?

Thanks,

bg

---

### Post by nothingspecial on 2011-08-17
Boot a live cd and copy it back from that.

---

### Post by beenny on 2011-08-17
i don't have a live CD (no cd drive) only USB - i'm assuming that will also work. 

My understanding is that i then need to mount my partition but that it's fstab specific. i followed this thread:

[http://ubuntuforums.org/showthread.php?t=258874&page=3](http://ubuntuforums.org/showthread.php?t=258874&page=3)

I was wondering what partition i mount?

bg

---

### Post by aeiah on 2011-08-17
mount all of them whilst in your live usb environment until you find the one that's root. it'll probably be /dev/sda1 so id start there
```

mkdir one
sudo mount /dev/sd1 one
```

you should be able to identify which one it is because there'll be /etc/fstab and /etc/fstab.bak

---

### Post by beenny on 2011-08-17
Thank you that worked - that's a good trick to know...

I'm starting to get a better understanding of mount points. I believe I read that you do not want to mount into root (/) - is that true? would it be advisable to change the mount point? I have a SSD drive if that makes a difference.

Thanks,

bg

---

### Post by nothingspecial on 2011-08-17
Mount stuff that you (or other users) would like permissions for in /media /mnt or $HOME

You don't have to though. What are you trying to mount and where would you like it? What is your objective?

---

### Post by beenny on 2011-08-17
This is a personal/work laptop so there aren't other users - or at least shouldn't be ;) I do mount other network drives when logging into my office if that makes a difference.

I moved to Ubuntu b/c I do a bit of programming for work so need/like the command line. I'm slowly starting to play more with the other half of linux (customization) though that is ultimately less important to me. So I would say my objective is to do what is best/safest as I mess around with advanced configurations like fstab...

so would you change:

> 
/dev/sda1 / ext4 errors=remoint-ro,user_xattr 0 1
to
/dev/sda1 /mnt/ ext4 errors=remoint-ro,user_xattr 0 1


does any of the three make a difference. I have seen the suggestion that is better to mount into home for doing clean updates on future versions...

Thanks,

bg

---

### Post by Wim Sturkenboom on 2011-08-17
This might be what caused the problem.
```

...
proc /proc proc nodev,noexec,nosuid 0 0 
/dev/sda1 / ext4 errors=remo**[COLOR="Red"]i[/COLOR]**nt-ro,user_xattr 0 1
#swap was on /dev/sda5 during installation
UUID=37c3ccea-c895-4437-8b62-706521474187b none swap sw o o

```

And no, you don't mount on '/'. It will hide everything under the mountpoint so the system doesn't have access to all normal stuff and you render your system (more or less) useless :D

---

### Post by beenny on 2011-08-17
yeah that was just a typo as i manually copied my fstab...

so then you would change the second column to /mnt/ ? does it make a difference between /mnt /media or $HOME

---

### Post by dave01945 on 2011-08-17
whenever you change things in fstab you should always run

```
mount -a
```

this will try to mount everything in fstab and give you any errors.

this is easier than finding the errors on your next reboot and having to use a live cd or usb

---

### Post by nothingspecial on 2011-08-18
> **beenny said:**
> yeah that was just a typo as i manually copied my fstab...

so then you would change the second column to /mnt/ ? does it make a difference between /mnt /media or $HOME


Put it in any, again depending what it is you are mounting.

Don't put $USER in your fstab, that is bash shorthand for /home/username and will not work in fstab

My fault sorry.

---

### Post by beenny on 2011-08-18
> **nothingspecial said:**
> Put it in any, again depending what it is you are mounting.


So I guess that is what I'm trying to get some intuition for. My understanding is that there is no difference between /mnt and /media but it's more of a bookkeeping thing (like Music, Pictures etc. in home). So you would typically put a cdrom in /media and a network drive in /mnt - but you don't need to. is that correct? I actually tend to put my network drives in $HOME b/c it makes for a slightly easier path when I need to refer to it. 

Where I'm less clear is what about your actual hard drive. What I was mounting here is my SSD drive. When I mount that in a folder  (e.g. /mnt) what is that folder under since there is no physical space that it's directed to? Even more so, what does it mean to mount that in $HOME when $HOME doesn't even exist before the drive itself is mounted. Is there not something circular in that?

That all being said, what is the advantage (& disadvantage) to mounting at one point or another? I've seen debate wrt doing upgrades but haven't fully followed the arguments.

Perhaps this is a more philosophical question but it would be great to get some deeper understanding of some these issues for when i make mistakes in the future...

thanks,

bg

---

### Post by Wim Sturkenboom on 2011-08-18
/media is for automount (as far as I know). If you mount on there, you have the chance that you can't mount an external HD anymore automatically.

If you mount it on $home, your home directory will be 'hidden'; also not something that you want unless the ssd is for that

The best way is to create a dedicated directory somewhere; e.g. /mnt/myssd or /myssd. Just don't use dedicated directories.

I've created a directory /photos and mounted my second HD on there. My alternative was to create /mnt/photos and mount on there.

---

