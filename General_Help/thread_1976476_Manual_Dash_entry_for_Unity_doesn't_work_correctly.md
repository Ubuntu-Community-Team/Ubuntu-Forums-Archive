---
title: "Manual Dash entry for Unity doesn't work correctly"
date: 2012-05-08
forum: General Help
---

### Post by Henne91 on 2012-05-08
Hi!

I would like to have the flash game Machinarium appear in Unity's Dash so I can run it from there.

I copied the game files to /usr/games to make them globally accessible (because I want to have all my games in one place that's outside my home folder) and set file permissions to "root:games" with read-write-permissions only for root and read-only-permissions for group and others and marked the binary as executable (because these are the permissions other files in the games-folder also have).

Output from ls -l:
```

drwxr-xr-x 2 root games    4096 Nov 22 17:10 00
drwxr-xr-x 2 root games    4096 Nov 22 17:10 01
drwxr-xr-x 2 root games    4096 Nov 22 17:10 10
drwxr-xr-x 2 root games    4096 Nov 22 17:10 11
-rwxr-xr-x 1 root games 9696482 Okt 11  2009 Machinarium
-rw-r-xr-x 1 root games  109935 Mai  8 21:40 Machinarium-1-icon.png

```

I then created a .desktop-file in /usr/share/applications with same permissions but didn't mark it as executable (like the other files in there weren't neither).

Now I can see an entry for Machinarium in Unity's Dash. However, if I try to start the game using this entry it just gives me a black fullscreen with the mouse courser on it saying "Press ESC to exit fullscreen mode" (although I changed game settings from fullscreen to windowed mode). Therefore, I assume, flash player actually tries to run the game but for whatever reason cannot get the content displayed.

When I start the game from terminal using ```
cd /usr/games/Machinarium
``````
./Machinarium
``` it starts in windowed mode (like I set in game before) and works perfectly.

It shouldn't be a problem with wrong permissions therefore, should it?

Why does my entry not start the game right? Can you give me any hints on where to look for the error?

This is what my .desktop-file looks like:

```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[de_DE]=/usr/games/Machinarium/Machinarium-1-icon.png
Name[de_DE]=Machinarium
Exec=/usr/games/Machinarium/Machinarium
Name=Machinarium
Icon=/usr/games/Machinarium/Machinarium-1-icon.png
```

Thanks in advance!

Hendrik

---

### Post by efflandt on 2012-05-08
Maybe there is something wrong with the way you created the .desktop file.

The easiest way is to open **Dash**, search for **Main Menu**, and use that to make a launcher.  Then if you get it to properly launch from Dash, you can make it stick in the Unity bar if you want to keep it there.

Note that when you manually run it you cd to the proper directory first, but your launcher does not. So it probably cannot find its other files. So you might want to have the launcher run a script in a terminal, so you can see what is happening when you have it cd and then run the game. Put the script in a ~/bin directory, and once you log out and log back in that bin would be in in your $PATH.

---

### Post by Henne91 on 2012-05-09
Hey!

Thanks, that was the first problem.

When running ```
cd /usr/games/Machinarium ./Machinarium
``` the games starts like it's suppposed to but when using ```
/usr/games/Machinarium/Machinarium
``` without changing directory it doesn't work.

In the mean time I was trying out some things. I set ```
PATH="/usr/games/Machinarium"
``` in my .desktop-file so now the game content shows up when starting from Dash. However, the game is still in fullscreen mode and I cannot load saved games.

I'm not even sure where the game stores these data since I couldn't find any hidden directory in my home folder.

Nevertheless, do you know of any other parameters I may have to set in my .desktop-file? If possible, I would like it to work without an additional script.

Or is there a way to do something like "cd" in the .desktop-file? Actually this should be what "PATH" does, shouldn't it?

Thanks so far,

Hendrik

---

### Post by Henne91 on 2012-05-10
I'm still not sure why I cannot see my old saved games but if I change settings now they are kept till the next start of the game, so problem SOLVED.

I also found the following tutorial on the internet which explains how to create a Dash entry (in case somebody else is still looking for this):

[http://amanita-design.net/forum/index.php?topic=1259.0;wap2](http://amanita-design.net/forum/index.php?topic=1259.0;wap2)

Nevertheless, the way I ended up also works but it's probably still the better option to create a script so you can fix the mouse issues in fullscreen mode.

Thanks efflandt!

Hendrik

---

