---
title: "Digikam photo slideshow as screensaver?"
date: 2010-04-03
forum: General Help
---

### Post by JugglinPhil on 2010-04-03
In F-Spot there's this nice function that shows a slideshow of all your photos as a screensaver. Since I've abandoned F-Spot in favor of Digikam ([http://ubuntuforums.org/showthread.php?p=9068961#post9068961](http://ubuntuforums.org/showthread.php?p=9068961#post9068961)) I was wondering if there is a way to do something similar in Digikam.

---

### Post by nothingspecial on 2010-04-03
I don`t know a thing about Digikam (or F-Spot for that matter) but to do a fullscreen, random slide show of photos I use feh

```
sudo apt-get install feh
```

Then ```
feh -rzF -D 5 ~/photos
```

r = recursive (it will use any images in any subdirectories of the directory specified)

z = random

F = fullscreen

-D 5 means show each picture for 5 seconds (change the number for any amount of seconds)

~/photos are where my photos are.

If you just want a slide show of your recent holiday without everything else then

```
feh -rzF -D 5 ~/photos/recent_holiday
```

If you want them in order leave out the z, in the same way if you just want the photos from that specific directory leave out the r.

There are loads more options, like making a collage and stuff, type ```
man feh
```
for full instructions.

I have made a launcher for my wife on her desktop with that command in it. She clicks the launcher and the slideshow starts.

---

### Post by JugglinPhil on 2010-04-03
That's pretty good, thanks a lot for the advice, but do you know if there's a way to set this as a screensaver?

---

### Post by nothingspecial on 2010-04-03
That`s a good question.

Google (and yahoo) don`t help.

You`ve got me thinking :p

There must be a way to script a feh command to execute after a certain amount of {keyboard, mouse}less  activity.

I`m not that good though.

---

### Post by JugglinPhil on 2010-04-04
Alright thanks, hope somebody's gonna help with this one.

---

### Post by JugglinPhil on 2010-04-06
Bump

---

### Post by motorcity909 on 2010-04-06
In System>Preferences>Screensaver, there is an option called Pictures folder which by-passes F-Spot or DigiKam and simply displays random pictures from the entire Pictures folder and it's sub-folders.

Cheers
Dave

---

### Post by JugglinPhil on 2010-04-06
Cool thanks, that solved it. :)

---

