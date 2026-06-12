---
title: "Screenshot Programs"
date: 2010-11-22
forum: General Help
---

### Post by COKEDUDE on 2010-11-22
What is everyone's favorite screenshot programs? I really don't like the gnome one. A timer feature is very important to me and the gnome one doesn't have it. 

I found the Xfce4 Screenshooter and it has a timer. Are there any other good ones that other people like? If there was a way to copy the picture to your clipboard that would make me even happier. I almost always edit my screenshots after I take them so that would be even more helpful. 
[http://www.linux-magazine.com/Online/News/Screenshots-with-Xfce?category=13439](http://www.linux-magazine.com/Online/News/Screenshots-with-Xfce?category=13439)
[http://goodies.xfce.org/projects/applications/xfce4-screenshooter](http://goodies.xfce.org/projects/applications/xfce4-screenshooter)

---

### Post by Toz on 2010-11-22
How about scrot? It's a console-based screenshot program available in the repositories. You can open a terminal window and issues something like:

```
scrot pic.png -c -d 5 -e 'gimp $f'
```
which will take a full screen shot after a delay of 5 seconds (displaying a countdown) and open the resulting image in gimp.

Have a look at at:```
man scrot
``` or 

[http://linux.die.net/man/1/scrot](http://linux.die.net/man/1/scrot)

---

### Post by COKEDUDE on 2010-11-24
You read my mind :). Gimp is usually my program of choice to edit my screenshots.

---

### Post by Quackers on 2010-11-24
In the default screenshot program one of the lines says 
Grab after a delay of ____ seconds. Doesn't that constitute a timer?

---

### Post by WorMzy on 2010-11-24
Scrot is my preferred screenshotter. Shutter has some nice features, but it's so damn slow to start up, so you have to have it loaded before you want to take the screenshot, and even then it takes a second or so to figure out that you wanted to take a screenshot when you pressed the print screen button. :x

---

### Post by COKEDUDE on 2010-11-24
> **Quackers said:**
> In the default screenshot program one of the lines says 
Grab after a delay of ____ seconds. Doesn't that constitute a timer?

When I press the print screen button this what I see. 

[IMG]http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/SaveScreenshot_008.png[/IMG]

I want to see something like this when I hit the screen shot button. 

[IMG]http://forums.linuxmint.com/download/file.php?id=5295[/IMG]

I also prefer to use the terminal whenever possible so I will be probably be using scrot whenever possible.

---

### Post by Keypel on 2010-11-24
**_Instead_** of pressing the print screen button on your keyboard, go to Applications->Accessories->Take Screenshot

Then you will see the options you are asking for.

[IMG]http://img263.imageshack.us/img263/3255/screenshottakescreensho.png[/IMG]

---

### Post by Quackers on 2010-11-24
> **Keypel said:**
> Instead of pressing the print screen button on your keyboard, go to App->Accessories->Take Screenshoot

Then you will see the options you are asking for.

Yes, that's what I do :-)

---

