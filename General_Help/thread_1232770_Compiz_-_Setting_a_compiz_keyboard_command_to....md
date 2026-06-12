---
title: "Compiz - Setting a compiz keyboard command to..."
date: 2009-08-05
forum: General Help
---

### Post by noremac3000 on 2009-08-05
I want a Compiz keyboard command to type "é". Something like <super>+"e" would be fine. Anyone know how I would do that? I've already tried putting "é" (with quotes) into the commandline0 textbox in the commands tab, but that didnt work(i wasent expecting it to). Any help would be appriciated.

---

### Post by P4man on 2009-08-06
Have a look at xdotool. Its in the repo's I think, I use it to map mouse buttons to control volume, but it seems flexible.

here is some documentation
[http://www.semicomplete.com/projects/xdotool/xdotool](http://www.semicomplete.com/projects/xdotool/xdotool)

I tried for 2 minutes but couldn't make it work either, but it should be possible I think :)

---

### Post by noremac3000 on 2009-08-06
> **P4man said:**
> Have a look at xdotool. Its in the repo's I think, I use it to map mouse buttons to control volume, but it seems flexible.

here is some documentation
[http://www.semicomplete.com/projects/xdotool/xdotool](http://www.semicomplete.com/projects/xdotool/xdotool)

I tried for 2 minutes but couldn't make it work either, but it should be possible I think :)


hmm.. i got the xdotoll thingy,  but it doesent seem to type in the active window.
i made a shell script and put it in /bin the script is :
```

echo Typing é...
xdotool type é

``` 

the echo command was just to test it to see if it was working.

---

### Post by P4man on 2009-08-07
im  not sure how you type é on your keyboard, but you should use the key modifiers like:

xdotool key ctrl+alt+n

to use altgr you have to use:

xdotool key ISO_Level3_Shift+e

(which give me the €uro sign)

---

### Post by noremac3000 on 2009-08-12
well, i mean what i did ws i put that shell script in and then went to the compiz commands and made the command run the script... yes, yes i know this was stupid, i could of just tried putting the xdotool command directly into the compiz commands, i wasent thinking at the time....... but when i realized this, i tried it, but it still didnt work.........

---

### Post by P4man on 2009-08-13
it should work, if you put in the right command :)
did you notice I used xdotool **key** ctrl+alt+n, and not "type" like you used ?

Tell me how you get then é sign with your keyboard layout (does it require shift, alt, alt+gr ?)

Finally, just to make sure; in compiz you have to define a command, like command line 0 (for instance I got here "xdotool key XF86AudioLowerVolume", and then assign it a keybinding or mouse click (eg, I got run command 0 bound to mouse button6).

---

### Post by CatKiller on 2009-08-13
This may sound like a stupid question, but why are you trying to run a command to type a letter? Why not just type the letter? Compose ' e gives you the é character. You'd have to type a pretty significant number of them for the time taken to press the extra button to add up to the amount of time you've already spent trying to get a command that will type a letter for you.

---

### Post by noremac3000 on 2009-08-14
eh, im tired of this, thanks anyway for the quick responses :D

---

