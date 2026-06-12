---
title: "Conky"
date: 2010-09-20
forum: General Help
---

### Post by thefallofroy on 2010-09-20
Just installed it and I have it working fine, but I can't figure out for the life of me what/how to code to make it show my battery life. I'd prefer one with a picture that shows in bars exactly how much life I have left. Can anyone help me out?

---

### Post by eddier on 2010-09-20
I'm not to clever at explaining but check this thread and follow ons..

[http://ubuntuforums.org/showthread.php?t=867076&highlight=conky]("http://ubuntuforums.org/showthread.php?t=867076&highlight=conky")

Have fun!  I did!

eddie

---

### Post by ddnev45 on 2010-09-20
[Looks like you want the battery_bar variable.]("http://conky.sourceforge.net/variables.html")


[URL="http://ubuntuforums.org/showthread.php?t=281865&page=1398"]Plenty of examples in here.
[/URL]

---

### Post by thefallofroy on 2010-09-20
> **ddnev45 said:**
> [Looks like you want the battery_bar variable.]("http://conky.sourceforge.net/variables.html")


[URL="http://ubuntuforums.org/showthread.php?t=281865&page=1398"]Plenty of examples in here.
[/URL]

Ok, so I get that the variable I want is "battery_bar" but when I put that in the rc nothing comes up. What exactly do I have to put? Do I have to do like "${battery_bar%" or something of that sort?

---

### Post by ddnev45 on 2010-09-20
Use something like:

```
${battery BAT1}${alignr 4}${battery_time BAT1}
${battery_bar 4,240 BAT1}
```

The 4 and 240 are height and width. On my laptop, the battery is BAT1, yours might be BAT0

---

### Post by thefallofroy on 2010-09-21
Thanks a lot! I finally got it to work. Mine is BAT1 as well instead of BAT0. Sorry to keep asking a bunch of questions but I have two more things:
1. How do I make my clock read 12h time format instead of 24h?
2. What code will I need to have a visual presentation of what's playing in rhythmbox (complete with album art)?

Here is my RC

---

### Post by ddnev45 on 2010-09-21
For 12-hour time:

```
%l:%M %P

```

will look like: 9:42 PM or 9:42 AM depending on time of day.

For all options:

```
man date
```

in a terminal (console) will bring up the man page.

For the Rhythm Box options, go to the [conky mega-thread ]("http://ubuntuforums.org/showthread.php?t=281865&page=1400")in the Community Cafe and start asking questions and do a search (I don't use Rhythm Box); you'll get plenty of awesome examples. Remember to post a screenshot with your conkyrc in the mega-thread.

There is also:

[Conky Hardcore]("http://conkyhardcore.com/")

[Conky Pitstop ]("http://conky-pitstop.wikidot.com/start")

---

### Post by thefallofroy on 2010-09-21
Thanks again! Much obliged.

---

