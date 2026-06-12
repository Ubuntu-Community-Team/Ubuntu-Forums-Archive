---
title: "filenames shortcut?"
date: 2010-09-19
forum: General Help
---

### Post by petrasflorin on 2010-09-19
hei, is there any way of abbreviating a filename ?

for example I wanna run a movie
 terminal: cd Downloads
           ls -l
           cd Dark.Island.720p.play-On
           mplayer Dark.Island.720p.play-On.avi


is there any way of just doing mplayer Dark.Island ?

I know I can do mplayer /Downloads/Dark.Island.720p.play-On/Dark.Island.720p.play-On.avi

but what I'm asking is abbreviating filenames with something like.... intuitive guessing ? typing maybe mplayer Dark.Island-- and the terminal guesses the rest of the filename ? sucks having to type all those numbers.

---

### Post by mikewhatever on 2010-09-19
You can type 'mplayer Dark.Island' and hit the 'Tab' key to autocomplete.

---

### Post by WorMzy on 2010-09-19
Press tab to autocomplete in a shell.

e.g.

cd Dark.[TAB]

will autocomplete to:

cd Dark.Island.720p.play-On

(assuming that there's no other filenames beginning with "Dark.", and you're using bash/zsh; I don't think it works in dash, and I haven't tried any other shells)

zsh has an amazing autocomplete system. I can type

cd /h/w/D/inc[TAB] and it'll autocomplete to:

cd /home/wormzy/Downloads/incomplete

(cd /h/w/D/in[TAB] matches incomplete and installers, and gives me the option to cycle between them with additional tab presses)

---

### Post by NFblaze on 2010-09-19
You can also file glob. Using wildcards and such


such as


*mplayer Dark*.avi*

"*" will match anything that begins with Dark and ends with .avi in that directory.

This is especially useful for seasons such as *totem Dexter.S01*.mkv*

---

### Post by petrasflorin on 2010-09-20
Thank you, Thank you, Thank you !

---

### Post by nothingspecial on 2010-09-20
Another good one is  Esc .

That will print the last argument to the last command

so ```
mkdir holiday_photos
```

Then ```
cd 'Esc .'
```

That means type cd then hold down escape and press the full stop/period button.

---

