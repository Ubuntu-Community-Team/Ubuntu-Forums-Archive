---
title: "Window Buttons"
date: 2010-04-15
forum: General Help
---

### Post by Penguin Guy on 2010-04-15
Since Ubuntu 10.04, the window buttons have moved to the left. This was done to leave space for [window indicators]("http://www.markshuttleworth.com/archives/333") planned to be released in 10.10, but which have still failed to materialize as of 11.04. Below I have posted screenshots of various button layouts and the terminal command to change to that layout. To change layouts; copy the command, press Alt+F2, then paste the text into the box that appears and press Enter.

NOTE: Setting window buttons to the right may conflict with [('bork')]("http://ubuntuforums.org/showpost.php?p=9317392") the new window indicators when they eventually appear. If this becomes a problem, the window buttons can be switched back to the left side in the same way.


Ubuntu 9.10 and previous:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=153357&stc=1&d=1271347492[/IMG]
```
gconftool-2 --type string --set /apps/metacity/general/button_layout ':minimize,maximize,close'
```

Mac:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=153358&stc=1&d=1271347580[/IMG]
```
gconftool-2 --type string --set /apps/metacity/general/button_layout 'close,minimize,maximize:menu'
```

Ubuntu 10.04 onwards:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156074&stc=1&d=1273344255[/IMG]
```
gconftool-2 --type string --set /apps/metacity/general/button_layout 'close,minimize,maximize:'
```

Ubuntu 10.04 beta:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155905&stc=1&d=1273344255[/IMG]
```
gconftool-2 --type string --set /apps/metacity/general/button_layout 'minimize,maximize,close:'
```


The part of the command that changes is the [FONT="Courier New"]':minimize,maximize,close'[/FONT] bit. Commas represent spaces between buttons, the semicolon dictates which side the buttons go on. Button order is the same for Mac and Ubuntu 10.04, except Mac has a menu button on the right.


Links:
[LIST]
[*][Launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633")
[*][You can change the layout using Tweak]("http://ubuntuforums.org/showthread.php?t=1449321")
[*][Community Cafe discussion]("http://ubuntuforums.org/showthread.php?p=9134759")
[/LIST]

---

### Post by Rasa1111 on 2010-04-16
very niice penguin guy!

of all those screenshots..
Ubuntu is the one imo that certainly looks the best! 

much nicer than the mac "traffic light" buttons. lol

 thank you!

---

### Post by cariboo on 2010-05-07
A bump for the move.

---

### Post by Penguin Guy on 2010-10-26
I've just got a Mac and I've realized that I was wrong; the button order of 10.04 *is* the same as a Mac. 

Thinking about it, having the minimize button next to the close button makes a lot of sense.

---

### Post by trikster_x on 2010-10-26
It is not suggested you change the location of your buttons using gconftool, because of a future implementation of [windicators]("http://www.markshuttleworth.com/archives/333").  These will take up the space on the right of the title bar and there could be problems if using gconftool to force the buttons to the right.  Instead you should do the following:

> **ubunterooster said:**
> The buttons are in the old location on all default themes apart from  Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or  Dust theme but with buttons on the right, choose one of those other  themes and use the Customize button to achieve what you want. e.g.
1. System > Preferences > Appearance
2. Select the theme icon "New Wave"
3. Click the button "Customize.."
4. Select tab "Controls" and select "Ambiance"
5. Select tab "Window border" and select "Ambiance"
6. Select tab "Icons" and scroll down and select "Ubuntu-mono-dark"
7. Select "Save Theme" to your choice.
[B]Using gconf-editor is not the right approach as this could bork  future themes. This change makes it easier for themes to do interesting  things with window borders.  Unfortunately, if the wrong approach  spreads, they won't be able to do that.

The original post in it's entirety can be found here:
[http://ubuntuforums.org/showthread.php?t=1486404]("http://ubuntuforums.org/showthread.php?t=1486404")

---

### Post by Penguin Guy on 2011-06-12
> **trikster_x said:**
> It is not suggested you change the location of your buttons using gconftool, ... The original post in it's entirety can be found here: [http://ubuntuforums.org/showthread.php?t=1486404](http://ubuntuforums.org/showthread.php?t=1486404)

Thanks, I have added a note explaining the borking risk:
> NOTE: Setting window buttons to the right may conflict with [('bork')]("http://ubuntuforums.org/showpost.php?p=9317392") the new [window indicators]("http://www.markshuttleworth.com/archives/333"). If this becomes a problem, the window buttons can be switched back to the left side in the same way.

---

### Post by pqwoerituytrueiwoq on 2011-06-12
i know 9.04 had this
gconftool-2 --type string --set /apps/metacity/general/button_layout 'menu:minimize,maximize,close'

---

### Post by Penguin Guy on 2011-06-15
> **pqwoerituytrueiwoq said:**
> i know 9.04 had this
gconftool-2 --type string --set /apps/metacity/general/button_layout 'menu:minimize,maximize,close'
From memory, and from screenshots on the internet, it seems Ubuntu 9.04 did not have a window menu button by default. Please correct me if I am wrong.

---

