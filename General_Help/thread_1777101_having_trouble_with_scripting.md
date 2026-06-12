---
title: "having trouble with scripting"
date: 2011-06-07
forum: General Help
---

### Post by NERDMAN! on 2011-06-07
this is just me being a total newb at linux and trying to do something that i would consider more advanced than anything ive done so far :D

i'm an avid minecraft player and i play online alot, and i was hoping there would be a way for me to have a shortcut key combination (alt + home prefferably) to call a script that would emulate a set of keystrokes, (t/home <enter>), i know the basic principle of having a script and the key combination to call it, but i want to know how to actually program the script, i have absolutely no idea when it comes to scripting. if anyone could help me out by telling me what to do that would be epic.

---

### Post by dragonfly41 on 2011-06-07
Try installing [COLOR=Navy]autokey[/COLOR] through Synaptic Package Manager.

It is similar to autohotkey in windows.

---

### Post by NERDMAN! on 2011-06-08
autokey inserts the text but i cant find out how to make it emulate the <enter> keystroke.
what i need is something that will at the touch of a button type /home and then hit enter of its own accord in the active window. unless theres a way to make autokey do this, i'm guessing i need to rely on a script of some sort.

---

### Post by dragonfly41 on 2011-06-08
Create New Script .. not .. Create New Phrase (which is for fast typing).

It is a common mistake.

Look at Sample Scripts .. not .. My Phrases.

---

### Post by NERDMAN! on 2011-06-08
thanks. scuse me while i pretend i know what i'm doing :D
(no that wasnt sarcasm. seriously i dont have a clue about scripting, but this will help me learn. thanks :D)

---

### Post by NERDMAN! on 2011-06-08
ok i'm lost. i cannot seem to make this script work from within the minecraft game.
it works everywhere else. the following code is my failing script. i dont understand why it would work in everything except minecraft. has anyone successfully managed to create a script that does work?

```
text = clipboard.get_selection()
keyboard.send_keys("t/home")
keyboard.send_key("<enter>" )

```

---

### Post by Junkieman on 2011-06-08
If it works everywhere else then maybe Minecraft captures the keyboard events so that autokey can't detect your key presses.

Sorry I don't have a solution for you, I also haven't found one, but it would make sense to give keyboard control to games, don't you think? ;)

---

### Post by NERDMAN! on 2011-06-08
> **Junkieman said:**
> If it works everywhere else then maybe Minecraft captures the keyboard events so that autokey can't detect your key presses.

Sorry I don't have a solution for you, I also haven't found one, but it would make sense to give keyboard control to games, don't you think? ;)

indeed it would. and i should point out that it does indeed type t/home in minecraft. its only the final line of the script that doesnt want to register. perhaps java has a different name for the keystroke? like instead of <enter> maybe i should try <return> or find out the keystroke id for that key?

---

### Post by dragonfly41 on 2011-06-09
Have you tried the feature "record a keyboard/mouse macro" ?

Edit > Record Macro   (or the fat red button on top panel)

then record a minecraft session and use the script recorded?

---

### Post by NERDMAN! on 2011-06-09
recording a macro right out of the game itself...genius. epic idea. shame it gave me the same issue.
as minecraft is a java game i'm guessing java uses a different name for the key as autokey recorded it as <enter> when i performed the action in game, yet the macro refuses point blank to work properly in the game. i have the key code for the enter key (34) as told by x event viewer.
is there any way i can use keyboard.send_key  with a code instead of a key name? there would be no way java could avoid that, especially if my suspicion is correct and it uses its own key bindings.

---

### Post by dragonfly41 on 2011-06-10
Here is another experiment ..

install wine in ubuntu

through wine .. install autohotkey   ([http://www.autohotkey.com](http://www.autohotkey.com))

I guess you'll also need to install java .. through wine

try running minecraft .. through wine .. and record a macro in autohotkey (not autokey)

I have not tried this although I do have autohotkey running in wine.

There are autohotkey scripts for minecraft if you search.

[http://www.autohotkey.com/forum/topic64217.html](http://www.autohotkey.com/forum/topic64217.html)

---

### Post by Junkieman on 2011-06-11
Hmmm, usually Enter is key code 0x0d, or 13 decimal (not 34). I get that when I use xev to scan key presses.

The [autohotkey key list shows]("http://www.autohotkey.com/docs/KeyList.htm") you can use Enter, Return, or NumpadEnter.

In [this post]("http://www.autohotkey.com/forum/topic69770.html") they use {enter} as a keycode.

Does this help?

---

