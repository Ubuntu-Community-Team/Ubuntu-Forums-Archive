---
title: "Software Center"
date: 2011-01-23
forum: General Help
---

### Post by yeklef on 2011-01-23
I am wondering if there is anyway to change the layout of the software center.  I have found a few programs by specifically searching for them by name, such as Glest.  That game says that it is in applications > games > strategy > Glest

So I am wondering how I can get to the strategy section.  The games section only shows arcade, board games, card games, puzzles, role playing, simulation, and sports.  No section for strategy

Thanks for any help

---

### Post by Spr0k3t on 2011-01-23
Interesting... possible bug perhaps?  You can pull up all the other games for strategy by using the search field.  Select games first, then search.

---

### Post by edhplus2 on 2011-01-23
> **yeklef said:**
>  That game says that it is in applications > games > strategy > Glest


I think that tells you how to start the game from the main menu if you install it. Like "Click on applications, then on games ....."

---

### Post by yeklef on 2011-01-23
Hmmm, edhplus2 is right with his answer.  The part with applications does turn out to be how you get to it.  

@ sprok3t - I am not so sure that it is a bug, so much as a setting that I can't find.  

I found a little more information.  Another reason that I think there should be more options in the Games field is because when I totaled arcade, board games, card games, puzzles, role playing, simulation, and sports I ended up at about 325, but selecting All says 504.

I did do a search for strategy, it just seems to be too small of a list (32) for what should be another 180 games.  

Thanks for the help

---

### Post by ubudog on 2011-01-23
If you know what you're doing, you could probably edit the source code...

[http://ubuntuforums.org/showthread.php?t=1400934](http://ubuntuforums.org/showthread.php?t=1400934)

---

### Post by yeklef on 2011-01-24
Thanks ubudog

While that is something that I will definitely look at, I wouldn't trust myself to not mess it up to badly right now (am still very new to linux).  I have been fiddling around with python though, so I will definitely go poking around in the source, just not sure I would want to compile it at this point and risk messing stuff up.

---

### Post by ubudog on 2011-01-24
> **yeklef said:**
> Thanks ubudog

While that is something that I will definitely look at, I wouldn't trust myself to not mess it up to badly right now (am still very new to linux).  I have been fiddling around with python though, so I will definitely go poking around in the source, just not sure I would want to compile it at this point and risk messing stuff up.

I don't think it would mess anything up, I think you can just run it from the directory, without installing the modified version onto your system.  But I'm not sure.

---

### Post by yeklef on 2011-01-25
It is hard to dig around in a program when you know so little about how it works.  I have been looking in the folder for a while, and  have only been able to figure out little bits and pieces of it.  Can anyone recommend a smaller program that I can poke around in to learn some more python stuff before sticking my nose back in the software center source?  Or pointing me in the general direction of which files might help me out.  

As per ubudog's info, I ended up just copying my software_center files from /usr/share/software-center to a new location to play with.  

(that is one thing I learned, how to figure out where items in the applications menu are pointing to; hmmm, maybe some of those applications are in python)

---

### Post by ubudog on 2011-01-26
When I was first learning Python, I created a little game.  It is open-source, and you can get it and edit the code from here:

[http://guessie.sourceforge.net](http://guessie.sourceforge.net)

Hope that helps you.  It was a great learning experience for me.  (although the game may be kinda crappy)  

:p

PS: Make sure you get the 1.0 release (it is the one written in Python)

---

