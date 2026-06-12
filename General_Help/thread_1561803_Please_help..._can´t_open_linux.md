---
title: "Please help... can´t open linux"
date: 2010-08-26
forum: General Help
---

### Post by ulmule on 2010-08-26
Hey everybody

I have a bit of a problem, i´am extremly beginner in linux, and my problem is now that i can´t open linux and see my main desktop.

I think I know why, recently, I was in the place where you can change all the login window things, then I change some things, and now the terminal keep coming up when i login and I don´t how go around it?...

please help...

-ulmule

---

### Post by QIII on 2010-08-26
Welcome to Linux!  Seems like your introduction is not going well.  I'm sorry.

A couple of things: 

1.  Before you do anything new, please ask us for help and advice.  We might be able to help you avoid some pitfalls.

2.  Keep track of what you are doing -- take notes, even -- because it is terribly hard for us to help when we hear things like "I went to the thingy and changed some stuff".  We don't know what happened, so we can't begin to unwind the problem.

OK.

When you start and get to the prompt for your login, type your login name.

You will be prompted for your password.  Type it in.  You won't see anything happen on the screen.  That is normal.

When you get to the next prompt, type

```
sudo service gdm start
```

and tell us *exactly* what messages or behavior you get. What you are telling your machine to do is start the GNOME desktop. My guess is you won't get to the desktop... but we'll get some clues.

---

### Post by TwoEars on 2010-08-26
Alright, here's what you do. Start up your computer. When you're faced with the terminal, enter your username, press enter, then enter your password(this won't show on screen) and press enter. After doing this, type ```
startx
``` and if the graphical interface doesn't start, post what happens on the terminal here. If the graphical interface starts, go to Applications -> Accessoriers -> Terminal and type ```
rm -f $HOME/.initrc
```, press enter, enter your password(again, won't show on screen), and press enter again. Note, you need to be careful with command, as it deletes a file - you must type EXACTLY what I've written.
Reboot, and it should start as normal.

---

### Post by QIII on 2010-08-26
I would be terribly, terribly careful instructing someone new to Linux to use rm without some very, very strongly worded caveats.

---

### Post by TwoEars on 2010-08-26
> **QIII said:**
> I would be terribly, terribly careful instructing someone new to Linux to use rm without some very, very strongly worded caveats.

True, but this is in general help(I kinda forgot that he was a total newbie half way through writing)

---

