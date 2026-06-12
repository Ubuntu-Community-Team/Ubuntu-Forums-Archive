---
title: "cloning drive speed problem with dd or ddrescue"
date: 2010-04-22
forum: General Help
---

### Post by peyu on 2010-04-22
Hi everybody,

I'm trying to make an image of my whole hard drive (320 GB) to save on an external hard drive. I'm using Ubuntu Jaunty Live CD to do it, with this command
```

sudo dd if=/dev/sda | gzip -c  > /media/ExpansionDrive/imagedd.img

```

At the beginning everything is going fine, but after few hours the transfer rate is incredibly low. After 1/2 hour, 20 Gb have been copied.
After 1 hour, 27 GB
After 2 hours, 40 GB
After 4 hours, 54 GB
After 8 hours, 71 GB
And so on...

Is it normal?
I've also tried to use ddrescue, but I have the same problem.
Is there any other tool to clone hard drive with a constant transfer rate?

¡Thanks in advance!

---

### Post by peyu on 2010-04-22
Well, I continue this thread here:
[http://ubuntuforums.org/showthread.php?t=1459853](http://ubuntuforums.org/showthread.php?t=1459853)

---

