---
title: "Home partition full"
date: 2011-02-24
forum: General Help
---

### Post by rocker9455 on 2011-02-24
Hello,
Ubuntu shows that I have 9.9gb empty on my 217gb partition and that 196gb has been used however when I go into /home and right click properties it shows that that only 120gb(ish) has been used, .trash seems to be empty and lost-found is empty, can someone enlighten me as to where all this space has gone?
Thanks

---

### Post by dobri on 2011-02-24
Try installing Baobab (a.k.a. Disk Usage Analyzer). It's a great application that will show you where your hard disk space has gone.

---

### Post by rocker9455 on 2011-02-24
> **dobri said:**
> Try installing Baobab (a.k.a. Disk Usage Analyzer). It's a great application that will show you where your hard disk space has gone.
Hmmm, it comes up with 116gb used, still missing ~100gb

---

### Post by thefasterblueone on 2011-02-24
This will show used disk space in all directories.

```
sudo du -h / --max-depth=1 | sort -h
```

---

### Post by drs305 on 2011-02-24
Take a look at this thead. It will help you track down what's taking up disk space via both GUI apps and the command line.

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by jocampo on 2011-07-29
> **drs305 said:**
> Take a look at this thead. It will help you track down what's taking up disk space via both GUI apps and the command line.

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

Fantastic post! I can tell there is a lot of hard work and time invested on that post.Thank you so much! This post was the 1st link that came with my Google search.

I just downloaded some updates on my Ubuntu headless server and now I have root directory almost full, don't know why.

I will follow this guide and I am confident will help or fix the issue.

---

### Post by drs305 on 2011-07-29
> **jocampo said:**
> I will follow this guide and I am confident will help or fix the issue.

If not just post here and we can help you. 

Normally we'd recommend starting your own post but since you are already here...  ;-)

---

### Post by jocampo on 2011-07-29
> **drs305 said:**
> If not just post here and we can help you. 

Normally we'd recommend starting your own post but since you are already here...  ;-)

Fixed! thanks to your guide, of course, thanks again! ;)  ...

But now I have another issue, for which I will probably open a new thread. The partition got full because my external passport USB drive did not mount properly. So the cron job that runs at midnight to backup my iTunes songs, ran ... but use /mnt/WD  , from root partition, not the passport USB drive. That's why / was almost full.

New issue is that it refuses to mount, it asks for partition type. Even when I provide that, does not mount. I will explain in a new post.

Thanks again!

---

