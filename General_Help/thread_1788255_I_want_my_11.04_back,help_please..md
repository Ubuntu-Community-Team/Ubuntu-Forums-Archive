---
title: "I want my 11.04 back,help please."
date: 2011-06-22
forum: General Help
---

### Post by figigigi on 2011-06-22
I'll tell you how I came here and see how desperate I am now.I right clicked and chose the "change desktop background" and then clicked the "get more background online" so here my web browser came and i reached here.To sum up,I can't reach anything on my desktop except a few folders of mine.No sidebars,no terminal that i can write some codes.I tried the ctrl+alt+t short cut for terminal but didn't work.Well I can use my old classic ubuntu when I choose  it but I want to use new 11.04 ubuntu,I want it back but I don't know how to do it.Well I tried some codes like 
```
reset --unity
```

in the ubuntu classic terminal and it brought back the 11.04.However I have to write that code to terminal each time when i open ubuntu classic to turn back 11.04.I want it to be permenant.

Please,any suggestion would be appreciated.Thank you.

---

### Post by dino99 on 2011-06-22
either:
- logout/login
- unity --reset
- unity --replace &
- gnome-panel --replace &
- metacity --replace &

---

### Post by figigigi on 2011-06-22
Thanks but the problem is i can't find the terminal to write those codes.

---

### Post by Dave_L on 2011-06-22
Try Alt+Ctrl+F1

---

### Post by figigigi on 2011-06-29
> **Dave_L said:**
> Try Alt+Ctrl+F1

Thanks that brings terminal but what am i going to write here exactly i tried unity --reset but didn't work.Btw I don't know how to leave that terminal,too.How can i go back? I pressed on button to close computer.

---

### Post by figigigi on 2011-06-29
Come on guys,please...Give me a hand.

---

### Post by apollothethird on 2011-06-29
> **figigigi said:**
> Thanks but the problem is i can't find the terminal to write those codes.

Try right clicking on the desktop -> Create Launcher -> [create a gnome-terminal icon]

Run the reset commands in that terminal.  You'll need to run it from a terminal that has a properly set DISPLAY variable.

> **figigigi said:**
> Thanks that brings terminal but what am i going  to write here exactly i tried unity --reset but didn't work.Btw I don't  know how to leave that terminal,too.How can i go back? I pressed on  button to close computer.

You can go back to your X server by hitting the proper alt-F-key.  X servers start at F7.  So it might be alt-F7 or alt-F8.


-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by figigigi on 2011-06-29
> **apollothethird said:**
> Try right clicking on the desktop -> Create Launcher -> [create a gnome-terminal icon]

Run the reset commands in that terminal.  You'll need to run it from a terminal that has a properly set DISPLAY variable.



You can go back to your X server by hitting the proper alt-F-key.  X servers start at F7.  So it might be alt-F7 or alt-F8.


-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

You are such a wonderful person,James,you know that,right:)

---

