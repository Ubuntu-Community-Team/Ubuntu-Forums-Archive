---
title: "Create a Shortcut/Alias?"
date: 2012-06-22
forum: General Help
---

### Post by LinXNut on 2012-06-22
Hey guys I play this game called Ace of Spades, and I really need a faster way of starting it. 
Originally, I type
```
cd .wine/dri*/blah/blah/blach...etc.
``` After navigating to the client, I then have to type:
```
wine client.exe -aos://#########
```The server is "aos" followed by a sequence of numbers that I usually just copy and paste.
So instead of typing all of this, is there a faster way of starting this?

Thanks

---

### Post by adam22 on 2012-06-22
This may or may not help...

Right click the menu or panel (well I guess if you're using that garbage called Unity, there's a way to add something to that dock) and edit menu or add new item/shortcut. It will ask for a command, comment, picture, etc.

You may or may not be able to combine these commands, but first let's see what you have here...

The first command is simply changing directories to your wine directory in your home folder. Apparently it is a hidden folder. The second command is launching wine.exe with the option aos (as indicated by the - character).

I've attached an image showing how I would add an item to the menu. You can play around with that and enter your two commands in to create one shortcut.

I believe this would work:

```

cd .wine/dri*/blah/blah/blach...etc. **;** wine client.exe -aos://#########
```

---

### Post by lechien73 on 2012-06-22
Well, I guess you could create a shell script that would have the following content:

```
#!/bin/bash

wine ~/.wine/drive_c/path_to_client/client.exe -aos://$1
```

Call it something like spades.sh and save it to your home folder. Then type:

```
chmod +x ~/spades.sh
```

Which makes it executable. Then to start the client, open a terminal window and type:

```
~/spades.sh ########
```

where you replace ######## with the numbers of the server you wish to use.

---

### Post by bab1 on 2012-06-22
> **lechien73 said:**
> Well, I guess you could create a shell script that would have the following content:

```
#!/bin/bash

wine ~/.wine/drive_c/path_to_client/client.exe -aos://$1
```

Call it something like spades.sh and save it to your home folder.

Then type:

```
chmod +x ~/spades.sh
```

To start the client, open a terminal window and type:

```
~/spades.sh ########
```

where you replace ######## with the numbers of the server you wish to use.

I keep all my personal executables in ~/bin (home/me/bin) for neatness.  Then you can use the GUI (panel/dock) to create a launcher start it.

FYI you don't need to use any extension (.sh) on the script.  If I run perl scripts I keep them in ~/bin/perl with a sym-link from the ~/bin directory.  But that's for my own organisation I suppose.

---

### Post by ajgreeny on 2012-06-22
At least three ways of doing what you want, and probably other ways I can't think of.

1.  An alias eg ```
alias aos='cd .wine/drive*blah/blah && wine client.exe -aos://#########'
```which you add to the **.bash_aliases** file in your home.  The terminal command is then just **aos**

2.  Make a launcher, but it will have to point to a script with those commands rather than just use the command in the launcher.  I have no idea how you add launchers of your own making to the unity launchbar, I'm afraid, so will let you figure that out yourself.

3.  Write your own **aos.desktop** which is a simple text file which you then add to /usr/share/applications, which I think should add the item to the dash "menu" list.  You can see what a normal .desktop file looks like from ```
gedit /usr/share/applications/simple-scan.desktop
```which is a small one without too much *cruft* in the text.

---

### Post by LinXNut on 2012-07-05
Thanks guys! This answered pretty much ALL of my questions.

:popcorn:

---

