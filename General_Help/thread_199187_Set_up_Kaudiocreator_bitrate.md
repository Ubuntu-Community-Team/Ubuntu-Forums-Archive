---
title: "Set up Kaudiocreator bitrate?"
date: 2006-06-18
forum: General Help
---

### Post by Daiver on 2006-06-18
How can I set up the kbps that it rips CDs to?  I just ripped a CD, but it's encoded at 230kbps.  I would like to rip to 192kbps, but I can't find the option to do that.

I've gone into the System Settings --> Sound & Mutimedia and tried to setup from there, but it didn't work.

I'm ripping to mp3 and it might be using LAME to do it.

---

### Post by Daiver on 2006-06-18
Bumpetty bump.

---

### Post by nixternal on 2006-06-23
in KAudioCreator select lame, then configure, and after the --preset standard add

-b 192

---

### Post by Daiver on 2006-06-24
Sorry for the late reply.  Here's the line I used to mantain a CBR of 160kbps:

lame --preset cbr 160 --tt %{title} --ta %{artist} --tl %{albumtitle} --ty %{year} --tn %{number} --tg %{genre} %f %o

For those who search the forum, please see:
lame --preset help

Thanks nixternal!

---

### Post by CGW on 2006-12-09
> **Daiver said:**
> Sorry for the late reply.  Here's the line I used to mantain a CBR of 160kbps:

lame --preset cbr 160 --tt %{title} --ta %{artist} --tl %{albumtitle} --ty %{year} --tn %{number} --tg %{genre} %f %o

For those who search the forum, please see:
lame --preset help

Thanks nixternal!

Thanks!!

---

