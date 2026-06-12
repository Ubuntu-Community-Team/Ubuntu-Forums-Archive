---
title: "Nautilus - how to mount disk images?"
date: 2011-04-13
forum: General Help
---

### Post by aneganov on 2011-04-13
Hi,

Sorry for starting this new thread, this question was asked several times, I read replies, still I didn't find any appropriate solution. 

I want to mount an arbitrary disk image (for simplicity - lets talk about Linux partition previously backed up in a file using `dd`) by clicking on it in Nautilus and selecting appropriate menu item. 

I don't want to type root password for that. I expect this should work natively. Why not?

---

### Post by mcduck on 2011-04-13
You can mount .iso images by right-clicking them and selecting "Open With Archive Mounter".

I doubt there's any easy solution for other types of disk images, though.

---

### Post by aneganov on 2011-04-13
> **mcduck said:**
> You can mount .iso images by right-clicking them and selecting "Open With Archive Mounter".

I doubt there's any easy solution for other types of disk images, though.

No, I don't mean .ISOs. I need to mount a dd'ed partition.

---

### Post by deathadder on 2011-04-13
As long as you know the filesystem used in the image you can use a loopback device to do it:
```
mount -t fs_type -o loop /path/to/image /path/to/mnt
```
If you've used dd to image an entire drive, I'm not sure how to do it...

---

### Post by deathadder on 2011-04-13
Hmm, looks like Google offers some good suggestions:

[http://wiki.edseek.com/guide:mount_loopback](http://wiki.edseek.com/guide:mount_loopback)

[http://www.google.co.uk/search?source=ig&hl=en&rlz=&=&q=linux+mount+dd+image&aq=0&aqi=g2&aql=&oq=linux+mount+dd+i](http://www.google.co.uk/search?source=ig&hl=en&rlz=&=&q=linux+mount+dd+image&aq=0&aqi=g2&aql=&oq=linux+mount+dd+i)

---

### Post by aneganov on 2011-04-13
> **deathadder said:**
> Hmm, looks like Google offers some good suggestions:

[http://wiki.edseek.com/guide:mount_loopback](http://wiki.edseek.com/guide:mount_loopback)

[http://www.google.co.uk/search?source=ig&hl=en&rlz=&=&q=linux+mount+dd+image&aq=0&aqi=g2&aql=&oq=linux+mount+dd+i](http://www.google.co.uk/search?source=ig&hl=en&rlz=&=&q=linux+mount+dd+image&aq=0&aqi=g2&aql=&oq=linux+mount+dd+i)

Thanks for the links. I'm looking for Nautilus solution. See the topic.

---

### Post by ~Plue on 2011-04-13
i'm not sure whether you could mount it without entering the password
pmount does allow regular users to mount but doesn't accept the options with the -o flag to use a loop device

so if you dont mind entering the password, this could be achieved by using a nautilus script similar to [this]("http://ubuntuforums.org/showthread.php?t=87369") (with a little modification)

---

### Post by deathadder on 2011-04-13
> **aneganov said:**
> Thanks for the links. I'm looking for Nautilus solution. See the topic.
AFAIK you can't using Nautilus alone. You need to do the actual mount from a terminal because dd images aren't excatly common desktop usage...

[EDIT]
Sorry missed the post by Plue, you'll need to use the script linked too with a combination of the commands I posted / from Google

---

### Post by yetiman64 on 2011-04-13
> **aneganov said:**
> Hi,

Sorry for starting this new thread, this question was asked several times, I read replies, still I didn't find any appropriate solution. 

I want to mount an arbitrary disk image (for simplicity - lets talk about Linux partition previously backed up in a file using `dd`) by clicking on it in Nautilus and selecting appropriate menu item. 

I don't want to type root password for that. I expect this should work natively. Why not?

If your images are a single partition image only (not a whole drive image) then loopmounting automatically at startup to a folder is possible using /etc/fstab entries, when not needed mounted simply comment out the line with a # or delete it.

See this thread post No.2 for info,
[http://ubuntuforums.org/showthread.php?t=1671370](http://ubuntuforums.org/showthread.php?t=1671370)

I use it to automount dd created image (.img) files of ext4 partitions as read only. You may need to experiment with mount options to write back to the file (don't know if that is a smart idea though- care would be needed.).

When mounted to a folder then nautilus has access to the contents of the image file.

---

### Post by kiyop on 2011-04-13
If you want to mount by clicking and do not want to mount automatically at startup, mount option "users,noauto" should be added in the line in /etc/fstab.
"users,noauto,exec,dev,suid" may be better.
Please type in terminal to refer to the manual:
```
man mount
```

---

