---
title: "Put a script in Applications menu"
date: 2011-01-03
forum: General Help
---

### Post by 3602 on 2011-01-03
I just downloaded the most recent SuperTuxKart from SourceForge. It is ready-to-run (no compiling, no making).
The script that runs the whole thing contains this single line:
```
LD_LIBRARY_PATH=./bin/: bin/supertuxkart
```
Of course, when I double-click on it, I select Run and I'm off racing Tux.
But I'd like this to be in the Applications > Games menu. I tried adding a launcher and for the command I just browsed to that script and clicked OK. But when I click the launcher, nothing starts.
So what to do? The script has no shebang line, do I put one in? Granted I can just create a desktop shortcut, but I'd really like it to be up there with my other games.
Thank you.

---

### Post by 3602 on 2011-01-04
Bump.

---

### Post by Dans564 on 2011-01-04
if u right click on the gnome menu and click edit menus you can add launchers to any category u want

---

### Post by 3602 on 2011-01-04
Well if you read my post, you'd have known that I created a launcher linking directly to the script, but it won't start.

---

### Post by KJ KJ KJ on 2011-01-04
I guess that when you run the script by hand, you do so from the directory of SuperTuxKart. 

If you look at the script contents, the path  'bin/supertuxkart' is relative to some directory. Also, the LD_LIBRARY_PATH is relative './bin' 

If you tweak both of these to be the absolute path to supertuxkart and its libraries, you may have more luck when you run your launcher.

---

### Post by mc4man on 2011-01-04
There are probably multiple ways here, one easy way - 
For the command in your Applications/games launcher use a small script thats runs "run_game.sh" based on cd /path/to/folder and run "run_game.sh"

Ex.
The tuxracer folder is in home directory so path is just _cd supertuxkart-0.7-linux-i386_, elsewhere would need full path

so the script would be
```
#!/bin/bash
cd supertuxkart-0.7-linux-i386 && ./run_game.sh

```
Then make script executable and in the launcher command box just browse to it

Here I have a bin that's in my home folder so in this case I put the script there and named it something simple (tuxr). Then in the launcher i just need to use the script name instead of path, either way would work

---

### Post by 3602 on 2011-01-04
The launcher still does nothing. No game, no errors, nothing.

---

### Post by mc4man on 2011-01-04
> The launcher still does nothing. No game, no errors, nothing. 
works perfectly here - Applications > Games > click on the entry and it opens.

Can you post the command you used  in your menu launcher, location of the game folder and script to launch

---

### Post by KJ KJ KJ on 2011-01-04
> **3602 said:**
> The launcher still does nothing. No game, no errors, nothing.

Can you post the modified script please? Let's get that right first, so that you can run the script from anywhere, then we'll try to fix your launcher.

---

### Post by 3602 on 2011-01-04
Yes the code in the new file is:
```
#!/bin/bash
cd my_name/Games/supertuxkart-0.7-linux-i386 && ./game.sh
```
The command in the launcher is:
```
/home/my_name/Games/supertuxkart-0.7-linux-i386/Run
```
As you can see, the original start file has been renamed to game.sh and my new file name is Run.

---

### Post by mc4man on 2011-01-04
> elsewhere would need full path
Use this (~ means /home/your_user_name

```
#!/bin/bash
cd ~/Games/supertuxkart-0.7-linux-i386 && ./game.sh
```

Not sure why you renamed the .sh, no matter I guess
Assuming the above script is named Run, and you made executable, then should work

---

### Post by 3602 on 2011-01-04
Excellent, that worked. Thank you!

---

