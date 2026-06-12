---
title: "search for all but MP3"
date: 2010-03-03
forum: General Help
---

### Post by ffxigotenks on 2010-03-03
I have a large music collection and I want them all to be in one format, but it is in several at the moment, I want to look for all files in a given folder (/media/music/) and look for all files that are not MP3, is there an easy way to do this?

---

### Post by Bradj47 on 2010-03-03
I know how to display ONLY .mp3 files. Open a Terminal, type **cd /media/music**. Then **ls *.mp3***. So maybe you want the inverse of that. If you know the format of the audio file that you do want to display, you could try that instead of mp3. For example **ls *.ogg* *.wav* *.foo* *.bar***

---

### Post by ajgreeny on 2010-03-03
I don't wish to mention the obvious, but I presume you are aware that in the gnome desktop you can use nautilus in *List View* rather than *icon* or *compact*, and click on the "Type" column to sort by file type.

---

### Post by andrew.46 on 2010-03-04
Hi ffxigotenks,

> **ffxigotenks said:**
> I have a large music collection and I want them all to be in one format, but it is in several at the moment, I want to look for all files in a given folder (/media/music/) and look for all files that are not MP3, is there an easy way to do this?

Not sure if you have given the *full* path there but the syntax could be something like:

```
find /media/music -type f '!' -iname '*.mp3'
```

If the path is actually in your home directory you would need to change the search path to $HOME/media/music and if not in your home directory you would need to run the command as sudo...

All the best,

Andrew

---

### Post by ffxigotenks on 2010-03-13
> **andrew.46 said:**
> Hi ffxigotenks,



Not sure if you have given the *full* path there but the syntax could be something like:

```
find /media/music -type f '!' -iname '*.mp3'
```

If the path is actually in your home directory you would need to change the search path to $HOME/media/music and if not in your home directory you would need to run the command as sudo...

All the best,

Andrew

thank you so much, that command helped me alot!

---

### Post by andrew.46 on 2010-03-13
Hi ffxigotenks,

> **ffxigotenks said:**
> thank you so much, that command helped me alot!

Great news :). If you were interested in learning a little more about 'find' there is a nice Ubuntu page here:

find: Ubuntu Community Documentation
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

All the best,

Andrew

---

