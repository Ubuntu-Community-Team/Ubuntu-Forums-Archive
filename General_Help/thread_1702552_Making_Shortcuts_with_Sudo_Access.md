---
title: "Making Shortcuts with Sudo Access"
date: 2011-03-07
forum: General Help
---

### Post by Nasair on 2011-03-07
Sorry if this is on the forums some where but I couldn't find what I needed, and not even with Google's mighty help.
Basically I have a game, called Age of Conquest III, which I got working just fine, but it won't save any setup or game files unless I run it as sudo from the terminal, example in terminal:
Sudo /bin/sh "/opt/age_of_conquest_iii/Age of Conquest III"
Now I created a short cut with the command being just:
/bin/sh "/opt/age_of_conquest_iii/Age of Conquest III"

What command do I put in my shortcut command to get it to open up like in my terminal command? I tried:
Sudo /bin/sh "/opt/age_of_conquest_iii/Age of Conquest III"
but this won't open anything.

Thank you for your help in advanced.

---

### Post by Serpher on 2011-03-08
Try adding a "She-Bang" line to the top of your script and running it:

```
#!/bin/bash
```

This will tell the shell what program to run the file through. Other than that you should just have to include what you use to get the file to open in a terminal.

---

### Post by Nasair on 2011-03-08
so I tried each of the following:

```

sudo #!/bin/bash "/opt/age_of_conquest_iii/Age of Conquest III"
#!/bin/bash sudo /bin/sh "/opt/age_of_conquest_iii/Age of Conquest III"
sudo #!/bin/bash /bin/sh "/opt/age_of_conquest_iii/Age of Conquest III"

```
Sorry for being stupid about this, but what am I doing wrong? I'm using Ubuntu 10.10 with most recent updates, if that is any help :confused:

Thank you again for any help.

...

When I was trying a few more combinations I found using my code below and setting the "type" from application to application in terminal I get it to work, I have to enter in my password for sudo, but I figure that makes sense and is a small price to pay for it to work. Sorry for the trouble.
```

sudo /bin/sh "/opt/age_of_conquest_iii/Age of Conquest III"
```

---

### Post by dionysius on 2011-03-08
OK, here's what I've done:

I've downloaded the game, the .sh installer - saved it to Downloads, ran the installer, told it to install to 'Downloads', created the Sym link also in 'Downloads', and ran the program from the folder it installed under 'Downloads'. No need for root, and no messing around with privileges. 

I keep my games from the interwebs in a folder called 'Games' - /home/myname/Games 

It really shouldn't need to run as root, and in this case it's not necessary either. 

You can manually create a menu entry in the main menu, just right click on the main menu, click 'Edit Menus', go to the Games section, click on new, at command browse to the location of the game and there you go. 

If at all possible try to avoid running stuff as root, there really is no need for it.

---

### Post by Nasair on 2011-03-08
I installed it through the Ubuntu Software Center and didn't have that option. I haven't needed to run a program as sudo after installing it through the software center before, so I didn't think to install it any other way. I used the .deb with Java already in it because the one that didn't have java in it gave me issues with my sound.
[HTML]http://www.ageofconquest.com/download.html[/HTML]

---

### Post by I&#9829;HTML5 on 2011-03-08
If you set it as ```
gksudo /bin/sh "/opt/age_of_conquest_iii/Age of Conquest III"
``` rather than ```
sudo /bin/sh "/opt/age_of_conquest_iii/Age of Conquest III"
``` you shouldn't need to open the terminal

---

### Post by Nasair on 2011-03-08
Thank you! using the gksudo instead of sudo does let me use the type as application and not application in terminal and it just prompts me for my password like I'm used to when things security permissions. It at least feels cleaner :)

---

