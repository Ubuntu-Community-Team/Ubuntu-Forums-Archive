---
title: "Ripping CDs with Kaffeine 0.8"
date: 2006-06-23
forum: General Help
---

### Post by Daiver on 2006-06-23
So, I finally found the debs to Kaffeine 0.8 and installed it.  So far, it's working fine but I have one problem: I can't rip CDs.  It's really a bummer since this is what I wanted Kaffeine 0.8 in the first place, otherwise I would have just stuck with 0.7.

Anyway, when I click "Rip CD", Kaffeine says that there are no audio encoders installed.  I thought that was why you needed LAME, which is something I already have since apt-get just told me so.  I went in the xine configuration in Kaffeine, but I was unable to find where to set the audio encoder.  I also went into Systems Settings -- Sound & Multimedia and couldn't find anything there either.

Can anyone help me out?

---

### Post by nixternal on 2006-06-23
I havent' tried Kaffeine for ripping. I have been using KAudioCreator to rip my music and it has done a great job. I will admit that the .ogg rips are kind of slow, but other then that it does what it is supposed to. You might want to give that a shot unless you are totally into Kaffeine. Good luck!!!

---

### Post by Daiver on 2006-06-23
Yep, but this is what happened when I used KAudioCreator:

[http://ubuntuforums.org/showthread.php?t=199187](http://ubuntuforums.org/showthread.php?t=199187)

---

### Post by nixternal on 2006-06-23
in KAudioCreator, select lame, and then configure, and after the --preset standard add

-b 192

---

### Post by Daiver on 2006-06-23
Thanks for your reply.  Unfortunately, it didn't work.  Here's the line I have:

lame --preset standard -b 192 --tt %{title} --ta %{artist} --tl %{albumtitle} --ty %{year} --tn %{number} --tg %{genre} %f %o

It still created the track at over 200kbps.  Did I place it correctly?

---

### Post by nixternal on 2006-06-23
im sorry, I did that wrong. You want to replace 'standard' with 192...so after --preset add the 192

lame --present 192

get rid of standard. My appologies once again.

---

### Post by Daiver on 2006-06-24
Here's what I used and finally worked:

lame --preset cbr 160 --tt %{title} --ta %{artist} --tl %{albumtitle} --ty %{year} --tn %{number} --tg %{genre} %f %o

Also, for those who search, please see this thread: [http://ubuntuforums.org/showthread.php?t=199187](http://ubuntuforums.org/showthread.php?t=199187)

---

### Post by Daiver on 2006-06-24
On a side note, would you know why it takes KAudioCreator like an hour to rip and encode a single CD?

---

### Post by gingermark on 2006-06-25
[QUOTE=Daiver]On a side note, would you know why it takes KAudioCreator like an hour to rip and encode a single CD?[/QUOTE]
Have you enabled dma?
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by Daiver on 2006-06-25
Sounds kind of dangerous.  How do I know if my drive supports it?

---

