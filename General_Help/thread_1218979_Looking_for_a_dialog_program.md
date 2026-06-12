---
title: "Looking for a dialog program"
date: 2009-07-21
forum: General Help
---

### Post by MaximB on 2009-07-21
Hello !
I'm not sure where to put this, but this place can also suite it.

I'm thinking of making a heavy dialog game.
It's still in very early concept steps and I can't promise anything right now...

Currently I am looking for a dialog program.
Let me explain what I mean...

NPC1 says "...something" , the player then can chose 5 options A,B,C,D,E - if the player chooses C then he will have F,G,H,I options ... then if he chooses H he will have J,K,L,M options ...

I've tried to use dia which is a program for diagrams and work-flaw but it's way too much work then it should be for my purpose.

I've searched sourceforge but didn't find anything suitable.

I need something that will show all the options for that NPC, like if you chose B what options you have, and what the NPC will tell you after each choice.

What can you suggest ?

P.S
I am not a programmer and currently I am not interested in "programmers" stuff that I have a no idea about.

---

### Post by MaximB on 2009-08-05
Some updates :

About 2 weeks ago I've started to learn python as I think this simple (much easier then C++ and Java) language will suite my game.
Then a few days ago someone directed me to a dialog tool called Dlgedit -which is exactly what I need.
But there where some issues...

That dlgedit tool is part of a free (open source) game called Adonthell :  [http://adonthell.linuxgames.com](http://adonthell.linuxgames.com)
Dlgedit is only available in version 0.4 which is just few source files that needed to be compiled. (version 0.3 however which doesn't have those tools is available as packages for 3 major OS's).

I've tried to compile those packages but there where many errors and unmentioned deps, with a lot of help from the project's IRC channel at freenodes server (adonthell channel), I've managed to add those additional deps and the devs fixed the bugs in their sources so I've finally manage to compile the game and the dialog tool and run it !
In the end they updated their dep's page and fixed the bugs in their source code which is good for everyone, they where extremely helpful.

The drawbacks (at this state) on the Dlgedit tool (which is part of several other tools including quest and map editors) is that it's bound to the game - you must compile the game engine first (but you can skip on the data files).
But it can be still used outside the game engine as Dlgedit has conversion tools to python .py files.

Dlgedit itself it a wonderful tool for making dialog trees without the need to know programing (for basic stuff), moreover it has the option on adding python code attached to the dialogs.
It's exactly what I need and much more.

Off course there is another minor problem which I will only start worrying about after (or IF) I'll finish all the dialogs and see that it's all good.
The problem is getting all this stuff run on "my non-existing" engine (which originally was supposed to be just python command lines), the devs said it's very possible to do without too much programing knowledge so I'm calm ... I can always bug them with my stupid (to programmers) questions about how to get it to work.
The reason I do not want to use their game engine is that it's 2d tile based simple looking engine - not what I have in mind.
Moreover if I can't get the art done right , I should concentrate on the main theme of the game which are dialogs.

Now the creative part begins, I've already many a short prologue and started my dialog with the first NPC, which should be very long.

Dlgedit :  [http://adonthell.berlios.de/doc/index.php/Tools:Dlgedit:Contents](http://adonthell.berlios.de/doc/index.php/Tools:Dlgedit:Contents)
Small simple tool tutorial to get the idea : [http://adonthell.berlios.de/doc/index.php/Tools:Dlgedit:Tutorial](http://adonthell.berlios.de/doc/index.php/Tools:Dlgedit:Tutorial)

Anyway, if you are planing on making an heavy dialog RPG game I highly suggest looking at this excellent tool.

---

