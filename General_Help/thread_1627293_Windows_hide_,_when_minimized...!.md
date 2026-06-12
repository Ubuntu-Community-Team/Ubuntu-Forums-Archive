---
title: "Windows hide , when minimized...!"
date: 2010-11-21
forum: General Help
---

### Post by tajiknomi on 2010-11-21
[SIZE=2]Its not my Problem....but one of my friend has text me to find the Solution...

He told me , whenever he minimize any Windows, it doesn't show Below(hide)..therefore the only way is to press Alt+tab to resume the Window.....
Moreover he is using Lucid...
[/SIZE]
Any help will be appreciated...

---

### Post by WorMzy on 2010-11-21
Tell him to right-click on the bottom panel, choose "Add to panel...", and drag a Window List applet onto the panel, where he wants it.

---

### Post by tajiknomi on 2010-11-21
[SIZE=2]Thanks for your Kind and Quick Reply...:p

i had told him,and problem solved but......when i add Win-applet and now i want to **remove** it from panel, and As-usual i right-click on it,it doesn't shows me the** Remove Option**..!!
Hows that...how to **remove it from panel now**...?


[/SIZE]

---

### Post by tajiknomi on 2010-11-21
[SIZE=2]Ok..i had Got this...
[/SIZE]

---

### Post by WorMzy on 2010-11-21
Did you find out how? There's a small handle (a few dots or lines, depending on your theme) just to the left of the applet. You have to right-click those to get the applet's options.

---

### Post by tajiknomi on 2010-11-22
[SIZE=2]Actually I had installed Mac-theme with a Blue and transparent Panel,therefore that Applet was not visible....then i had Right-Click on certain places over the panel and Remove it....[/SIZE]:P

the  problem is Solved,but i have a little question in my mind....

[B] [SIZE=2]is their a way to remove[/SIZE][SIZE=2] (Applets)[/SIZE][SIZE=2] it via C-L-I[/SIZE] ....[SIZE=2]?

[/SIZE][/B][SIZE=2]<**out of topic**> *I like your Signature...isn't that similar..!* ;)<>[/SIZE][B][SIZE=2]
[/SIZE][/B]

---

### Post by WorMzy on 2010-11-22
Haha, yes, very similar. :p

It is possible to remove applets with the command line, but it's not always easy to identify which is the right one to remove.

First, cd into ~/.gconf/apps/panel/applets and run ls
```
wormzy@sakura[pts/5]:~/.gconf/apps/panel/applets$ ls
applet_0   applet_3  applet_7       %gconf.xml
applet_1   applet_4  applet_8       notification_area_screen0
applet_10  applet_5  applet_9       window_list_screen0
applet_2   applet_6  clock_screen0  workspace_switcher_screen0
```

Obviously, in this case, the right applet would be window_list_screen0. But if it was one of the many "applet_#"s, then there's no immediate way to identify which is which; so you need to look inside each one with "cat applet_**#**/%gconf.xml". Piping cat into grep "Applet" generally works to find out the name of the applet, though there's no guarantee. e.g. ```
wormzy@sakura[pts/5]:~/.gconf/apps/panel/applets$ cat applet_4/%gconf.xml | grep "Applet"
		<stringvalue>OAFIID:SensorsApplet</stringvalue>

```

Once you know which is the right applet to delete, do so with rm -r, e.g.
```
wormzy@sakura[pts/5]:~/.gconf/apps/panel/applets$ rm -r applet_4
```
Then shutdown gconftool-2 with
```
gconftool-2 --shutdown
```
and then finally restart gnome-panel with
```
pkill gnome-panel
```

---

### Post by tajiknomi on 2010-11-22
[SIZE=2]*Thankx, I will try it sometime .... :p*[/SIZE]

---

