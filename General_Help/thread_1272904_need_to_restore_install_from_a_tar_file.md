---
title: "need to restore install from a tar file"
date: 2009-09-22
forum: General Help
---

### Post by GMachine_24 on 2009-09-22
Here's the situation: I have used Ubuntu 8.04 for awhile and did regular back ups of the entire hard drive using "tar" to a separate hard drive. I have back ups going back two months. Not daily - but at least after every update.

Anyway, I started getting error messages when I booted the computer. To shorten the story, I ended up wiping the hard drive clean and have now formatted it as an ext3 partition.

So, now what I want to do is reinstall Ubuntu using one of my recent back ups - which, as I said, is on another drive.

I booted from a live Ubuntu CD. I can mount drive with the back up on it - but I am trying to figure out what I need to do with the main drive - i.e. the one I want to copy Ubuntu to. Call it

```


/dev/sda1


```

I think I need to mount the main drive also - but how do I do this? Do I need to create a mount point and then mount the drive and if so what should I call the mount point? Should it just be

```


/


```

Obviously I don't know. I have the command to restore the tar file to the main hard drive once I have figured out this mounting issue.

Thanks.

GM

---

### Post by bogdan.veringioiu on 2009-09-23
Hi.

I have a suggestion:
-make a fresh install from the live cd;
-reboot, start again from live cd, then overwrite the / (mount the root partition of the freshly installed system) with the contents of your tar archive. I would exclude /proc, /dev, /boot, /media
-reboot and enter the system, see if it works.

Bogdan

---

### Post by GMachine_24 on 2009-09-23
Bogdan:

Thanks for your prompt reply. I'll think about what you have said - I thought about doing a fresh install and then just restoring the home and documents and desktop files from  the tar file.

Are you really from Timosoara? I was there.... in... 1997... I believe, on my way to Suceava (pardon my bad spelling).

Very cool. Thanks again for your help.

GM

---

### Post by bogdan.veringioiu on 2009-09-24
Hi.
Yes, I am really from Timisoara.
:)
You should come back again.
Cheers.
Bogdan

---

