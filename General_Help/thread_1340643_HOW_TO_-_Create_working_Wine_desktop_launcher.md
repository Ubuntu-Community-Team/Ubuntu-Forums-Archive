---
title: "HOW TO - Create working Wine desktop launcher"
date: 2009-11-28
forum: General Help
---

### Post by ed-koala on 2009-11-28
Ok, some hard earned info for all you folks that like those pretty desktop icons to click and play :)

Are your Wine menu items not working right?  Have you tried to make a desktop launcher for a Wine program but can't seem to make it work?  Here's the answer, step by easy step.

First, the reason you have a problem.  Two reasons really, not related. First, I've found some games' launcher exe files just don't work right, and you have to use the main exe file to get the program to run. 

Second, Windows and/or Wine (not sure which is to blame) is picky ... it wants to BE in the directory the file is in WHEN you run the exe. Normal menu items point to the program using the path, i.e. /home/ed/.wine/la la la .exe. That won't cut it.

So, you have to create a script that will change to the proper directory, then run the right file.  Here is how you do that. We are going to create a launcher for World of Warcraft. Commands you type are in color. Important things are in bold.

Open a terminal.

Type [COLOR="Red"]sudo gedit[/COLOR] (or gkedit or whatever editing program you use).

Type in your password.

Add the following lines to the file:

```
[COLOR="Red"]#!/bin/bash
cd ~/.wine/drive_c/World\ of\ Warcraft/
wine Wow.exe[/COLOR]
```

The first line is for the bash script.

The second line changes to the World of Warcraft directory. If your WoW is installed somewhere else, edit this line to match your path. *The \ **MUST** be used after any word that has a space after it.*

The third line runs the program.

Time to save the file. I personally like to put script files in my **/bin** directory, which is located under File System.  Browse to the **bin** directory.

Save the file as **wow.sh**

Close gedit.

In the terminal, type the following command:

[COLOR="Red"]chmod a+x /bin/wow.sh[/COLOR]

This makes the script an executable file.

Close the terminal.

Now to make the desktop launcher ... right click on the desktop and choose **Create Launcher**.

Under **Name**, type [COLOR="Red"]World of Warcraft[/COLOR] (unless you want to call it something else).

Under **Command**, type [COLOR="Red"]/bin/wow.sh[/COLOR]

Leave Comment blank, or put whatever pleases you there, like the date or Ubuntu rocks!

Click OK.

The default icon sucks, so if you want to change it, right click on your new launcher, choose Properties, then left click on the icon and choose a different one and click Open.  I personally download icons from the web and save them in an icon folder in my home directory.

Presto!  You can now run World of Warcraft flawlessly from your desktop icon.

This info can be changed to suit any Wine program. Pass on what you've learned, and do tell me if this does not work for you so I can update the instructions.

---

### Post by ed-koala on 2009-11-28
Tip:  The last line of the script, line 3, can be changed if you use special commands to run WoW, like [COLOR="Red"]wine wow.exe -opengl[/COLOR] or [COLOR="Red"]padsp wine wow.exe[/COLOR]

---

### Post by Sirusdark on 2009-12-18
You fellow Ubuntu user, you deserve an award:

How many freakin dumb posts (and Google searches) have I browsed before finding a how-to, EXPLAINED!!
Dam I hate *****[EDIT : My apologizes, it was rude of me] people that think they're too smart to explain what they do!

So thank you very much for the detailed explanation! This should be a sticky on the forum : "How to explain something; the awesome way...". Hahaha!

Anyway, in my opinion, I think that that we shouldn't have to be making all these kind of silly tweaks to get Ubuntu to work like we want it to.

A+

---

### Post by Sirusdark on 2009-12-18
After MANY tries, I finally made a working Custom Application Launcher for Fallout 2!!!! Wahoo! (It's just missing the icon, but it's 3h30 a.m. and I now feel a bit tired...Zzzz)


So here are my own recommendations, along with the problems I've encountered :

1. Do NOT put your custom bash file in /**bin** : it's your File System Directory! It's a nightmare trying to understand if you are running or not with admin rights... and it didn't want to work with me at all. I couldn't even use ***chmod*** on the bash file in there.

2. Do not type your command line starting with** */***. It didn't work with it.

3. For no reason, while I was typing this reply, I was also doing tests with the bash file, launching the game in terminal, etc. After a successful game launch, when I exited the game, I got kicked out of my Ubuntu session! When I logged back in, I had "lost" everything : all programs had closed, along with Firefox and this long reply!! (this is my third version)... Very strange...

4. Tell me how to delete the file in /**bin**, please! Thanks in advance!


I use this command line in my Custom Application Launcher and it works perfectly:

```
Downloads/fallout2.sh
```And here is the content of my fallout2.sh bash file (located in **Downloads**):

```
#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/Interplay/Fallout\ 2
wine FALLOUT2.exe
``` Notice the use of the backslash "\" before every space. Thanks for pointing this out!

Thank you so much! I consider this "How-To" contribution as my Christmas gift!! :D

A+

---

### Post by frereonline on 2011-03-13
After reinstalling CrossOver Linux 10.00 on Ubuntu Lucid, the default menu shortcuts were all messed up, and it took me a lot of fiddling (newbie ;o) to find the proper command and create manual shortcuts... Here it goes:

/opt/cxoffice/bin/wine --bottle "[BOTTLE NAME]" --cx-app [APPLICATION NAME]
Example:
/opt/cxoffice/bin/wine --bottle "Microsoft Office 2000" --cx-app WINWORD.EXE

The icons are normally under
~/.cxoffice/[BOTTLE NAME]/windata/Associations

To get a list of all Crossover Win applications, run this in a terminal:
find ~/.cxoffice -iname "*.exe"
___
I hope this helps...

---

