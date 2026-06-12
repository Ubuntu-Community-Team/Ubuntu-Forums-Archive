---
title: "Can someone help me installing a game pls?"
date: 2010-08-24
forum: General Help
---

### Post by PinguLin on 2010-08-24
[COLOR="DarkOrchid"][FONT="Comic Sans MS"]Hello fellow Ubuntu's and Linux fans (:popcorn: someone?):p

I'm pretty new to Linux (since a week) and i discovered several problems with installing games, for example trials of my favorite style of games, Hidden objects, and today i downloaded the game ARX Fatalis. It's extracted in my folder but i can't seem to install the game. I opened every file but this is the answer i get (I deleted my name in that line): Could not display "/home/NAME/ARX_FATALIS (G)1/setup1.cab". There is no application installed for Microsoft Cabinet-archief files
Does anyone know how to install that game pls?

And If someone knows how to install my hidden objects games it would be a great pleasure for me!
Thx! 
PS: what's that deal with the prefix? No idea if i choose the right one :confused:[/FONT][/COLOR]

---

### Post by DrMelon on 2010-08-24
Is this a Windows game you're trying to run? 
Windows games will not work on Linux, unless you install "wine" first.

Go to Applications -> Accessories -> Terminal,
and type this:

```

sudo apt-get install wine

```
You'll be asked for your password, so put that in, and then wine will install.
It might work with your games, it might not - it's relatively experimental right now.

edit:
Apparently it works very well.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4676](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4676)

---

### Post by 3Miro on 2010-08-24
In order to play windows game sunder Linux you need to install wine. Not all games can be played and often times specific tweaking is required, however, hidden object games are simple enough. Install wine (as noted from above, or simply go to Ubuntu Software Center and search for wine) and then right click on the setup file and select "Run with wine".

WineHQ forums have specific information for different games. Always make sure to check with them before installing a game, this can save you a lot of trouble.

---

### Post by PinguLin on 2010-08-24
[COLOR="DarkOrchid"][FONT="Comic Sans MS"]@ DrMelon
I did what you said, typed that code in the terminal, everything seemed to work out well, reopened the ARX Fatalis file, but nothing is happening. Is there a specific file I need to look for to open it?

@ DrMelon & 3Miro
Thx a lot for you fast reply. 

Do you guys also know something about installing webcams? I have a VF0400 Creative instant webcam. Worked perfectly on my windows computer but can't get it installed on this Linux. Been looking online as well, got several sites but none of it is working. 

I feel soo stupid, I'm soo used to Windows and now I feel like a little child that needs to learn how to read and write :p[/FONT][/COLOR]

---

### Post by WorMzy on 2010-08-24
May I ask why you're trying to use Linux to play Windows games? Some games will work if you use Wine, but it's very hit and miss, and even if they do work, it's unlikely that they'll work as well as they do on Windows.

If you have Windows installed on your PC, it's better to use that for games. It's a lot less hassle, and there's more a of a guarantee that your games will work.

That said, if you still want to install games using wine, open a terminal, type (don't press enter)
```
wine
```
followed by a space, then drag and drop the installing exe or msi file into the terminal window from the file browser, then press return in the terminal.I don't think you can install from a cab file, it's just an archive (as far as I know).

---

### Post by PinguLin on 2010-08-24
[COLOR="DarkOrchid"][FONT="Comic Sans MS"]@WorMzy
The reason i'm using Linux is because while i was away in Crete for 4 months, some idiot who moved my computer dropped it from the stairs and broke everything inside it. He gave me his old computer in return, but the HD crashed, so my neighbour installed Linux halfway the HD. Believe me, it's not by choice i'm using Linux ;)
But you are right, why wasting my time on this, i just wait till i can buy myself that new laptop with Windows :D

Thx anyways all you guys for your help. I might return soon for some advice on using the office applications from Linux :p[/FONT][/COLOR]

---

