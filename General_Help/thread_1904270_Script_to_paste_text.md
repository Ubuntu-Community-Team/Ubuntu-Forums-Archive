---
title: "Script to paste text"
date: 2012-01-04
forum: General Help
---

### Post by J V on 2012-01-04
I want to attach a script to a keybind to paste some text, I can do the keybind just fine but I need a script that will stick this text onto the clipboard and paste it into the program that I'm running. How do I do that?

---

### Post by Vaphell on 2012-01-04
where do you get the text from?
either way check this thread, OP had similar problem
[http://ubuntuforums.org/showthread.php?t=1789578](http://ubuntuforums.org/showthread.php?t=1789578)

you can do cool things with xclip/xsel/xdotool

---

### Post by J V on 2012-01-04
All well and good but I'm pasting into a windows program in wine that only knows Ctrl V, and I can't find something that works properly

---

### Post by Vaphell on 2012-01-04
so emulate 'ctrl+v' instead of sending 'middleclick' signal
```
xdotool key ctrl+v
```
xdotool can send any key combo

if that doesn't work you may need to test which kind of copypaste buffer is used by ctrl+v (there are 3: primary, secondary and clipboard). replace **xclip -i** with the proper one from the list below
primary: **xsel -pi**,
secondary: **xsel -si**,
clipboard: **xsel -bi**
my tests indicate that if i use clipboard and send ctrl+shift+v in terminal i get the desired result (ctrl+v in terminal requires additional shift to work)
```
$ echo p | xsel -pi
$ echo s | xsel -si
$ **echo b | xsel -bi**
$ xdotool key ctrl+shift+v
$ **b**

```
 so most likely xsel -bi is the one you need

```
cat file.txt | xsel -bi
xdotool key ctrl+v
```

---

### Post by J V on 2012-01-04
Awesome, that works great :P [SOLVED]

---

