---
title: "cant see file extensions"
date: 2010-04-05
forum: General Help
---

### Post by andrew_a72 on 2010-04-05
Installed Ubuntu just awhile ago, downloaded songbird and did a search for media files, and it only picked up half of my music files.

While all the files are MP3's, only half of them have ".mp3" at the end of their name. So in order to get Songbird to pick up all the files I have to go through the half that doesn't have .mp3 at the end of the name and manually right click, change name, then add .mp3, problem is, I have a LOT of music.

Is there an easier way around this?

Thanks in advance,

---

### Post by NightwishFan on 2010-04-05
Try Easytag. It is in the repositories. [Click here and hit ok to install]("apt://easytag") or run: ```
sudo aptitude install easytag
```
[http://en.wikipedia.org/wiki/EasyTag](http://en.wikipedia.org/wiki/EasyTag)

---

### Post by lovinglinux on 2010-04-05
If you have them all on the same directories, then use [pyrenamer](apt:pyrenamer) [apt-get] to add the extension to all files at once.

BTW, Songbird will no longer support the Linux version.

> While our Linux users are some of the most passionate, do some killer development, and always provide tremendous input as to whether we’re on the right path or not, we simply can’t continue to support a Linux version as we have in the past.[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"]Songbird Singing A New Tune[/color]]("http://blog.songbirdnest.com/2010/04/02/songbird-singing-a-new-tune/")

[*]**Tags:** [[color="DarkSlateGray"]songbird linux support[/color]]("http://www.google.com/search?q=songbird+linux+support+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by andrew_a72 on 2010-04-05
Awesome, problem solved, much faster than right click ->rename -> ect


Thanks for the help

---

