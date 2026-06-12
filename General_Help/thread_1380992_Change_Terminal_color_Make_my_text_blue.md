---
title: "Change Terminal color: Make my text blue"
date: 2010-01-14
forum: General Help
---

### Post by pstein on 2010-01-14
When I use a terminal then everything is currently black text on white bachground.
 
That is fine except one thing: I would like to have all commands I type in blue.
 
How can I achieve this (permanently) with minimum configuration change?
 
I found no special option for "your text" in 
 
Terminal->Edit->Profile Preferences->Color
 
Peter

---

### Post by Saiko Berry on 2010-01-14
Depends on the terminal you use. Which terminal are you using?

If its gnome-terminal

Edit > Profile Preferences > Colors > Text - change it.

If its urxvt, or other equivilants you will need to change/make .xdefaults and xrdb merge it.. but we'll get to that if thats your issue.

---

### Post by pstein on 2010-01-14
> **Saiko Berry said:**
> Depends on the terminal you use. Which terminal are you using?
 
If its gnome-terminal
 
Edit > Profile Preferences > Colors > Text - change it.
 
If its urxvt, or other equivilants you will need to change/make .xdefaults and xrdb merge it.. but we'll get to that if thats your issue.
 
Yes its a gnome-terminal, BUT:
 
When I go to the suggested menu and
- disable "Use colors from system them" and
- select "Built-in schemes" = Custom and
- click "Text color" and
- select blue from the palette and
- hit OK
 
then the color is still black. 
 
Why?
 
Do I have to switch to root to change this setting?
 
How can I do this with "sudo"?
 
Furthermore it seems to me that with that setting the color of all text is changed.
I want another color just for all the text I am entering in a terminal.
The output from the commands should stay in black.
 
How can I achieve this?
 
Peter

---

### Post by drs305 on 2010-01-14
> **pstein said:**
> Yes its a gnome-terminal, BUT:
 
When I go to the suggested menu and
- disable "Use colors from system them" and
- select "Built-in schemes" = Custom and
- click "Text color" and
- **select blue from the palette** and
- hit OK
 
then the color is still black. 
 
Why?

Peter,

You don't have to use "sudo". When you select "blue", are you just clicking on the outside circle? There is a small circle inside the triangle that needs to move to the color shade you want. And in the color box it should be blue before you click on OK.  Is this what you are doing?  You can also type the color name (blue) in the "Color name" window. press ENTER, and it will automatically convert it for you.

---

### Post by Saiko Berry on 2010-01-14
> **pstein said:**
> Yes its a gnome-terminal, BUT:
 
When I go to the suggested menu and
- disable "Use colors from system them" and
- select "Built-in schemes" = Custom and
- click "Text color" and
- select blue from the palette and
- hit OK
 
then the color is still black. 
 
Why?
 
Do I have to switch to root to change this setting?
 
How can I do this with "sudo"?
 
Furthermore it seems to me that with that setting the color of all text is changed.
I want another color just for all the text I am entering in a terminal.
The output from the commands should stay in black.
 
How can I achieve this?
 
Peter

You do that by making your own theme under Pallete, but Im quite unsure how to be that specific.. I don't think you can without writing your own terminal.

---

### Post by pstein on 2010-01-14
> **drs305 said:**
> When you select "blue", are you just clicking on the outside circle? There is a small circle inside the triangle that needs to move to the color shade you want. And in the color box it should be blue before you click on OK. Is this what you are doing? You can also type the color name (blue) in the "Color name" window. press ENTER, and it will automatically convert it for you.
 
Oh, you are right :-)
 
However this trick changes all text. I want to change only MY text.
Is this possible as well?

---

### Post by Saiko Berry on 2010-01-14
I don't think it is possible to be that percise without writing your own terminal life I said above.. your text doesn't have its own flag on the pallete.

---

