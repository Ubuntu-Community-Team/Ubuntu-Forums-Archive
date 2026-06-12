---
title: "Planetpenguin racer - arrow keys"
date: 2006-01-21
forum: General Help
---

### Post by poiuytr on 2006-01-21
For some reason the Keyboard Configuration of the game Planet Penguin Racer (which is the replacement for TuxRacer) has lost the ability to use the keyboard arrow keys, and I can't figure out how to correct it.

I could assign "Left" and "Right" etcetera to other obvious keybaord keys (such as "a" or "d") but I hate that - I like using the arrow keys, and my kids do, too.

I'm just not sure what to type in on the GUI "Keyboard Configuration" screen so that I can, for example, use the left arrow key to turn Tux left.  Simply pressing the arrow key while I am trying to configure it, doesn't work.  I can press the "a" key or any other knon key and make that ork for "left", but I can't press the arrow key and make it work.

I tried figuring out this game's terminal-based config file (~/.ppenguinracer/options, or something like that) but I couldn't figure it out, and I couldn't find any helpful game documentation, either, during an Internet search.

This is a trivial little problem, I know, but can anyone help me figure it out?  Thanks in advance.

---

### Post by gitfiddler on 2006-01-23
*bump*

I'm interested in finding this out, too. The game is just not as much fun using the alphabet keys!

(Should this thread be posted elsewhere?)

---

### Post by midwinter on 2006-01-23
I know some people have solved this by simply deleting the 'options' file from their .ppracer directory. 

I just started using wasd instead..

---

### Post by MighMoS on 2006-01-24
Has anyone filed a bug on launchpad?

---

### Post by poiuytr on 2006-01-25
Thanks for all of your suggestions but, Hey, I fixed it!  Here's how...

[First, here is an aside.  I went to the ppracer website ([http://projects.planetpenguin.de/index.php](http://projects.planetpenguin.de/index.php)) and saw in the forums there that the developer was aware of this issue and said he was going to work on it when he has time - so, no need to report a bug].

Some of the postings here and elsewhere on the 'Net and even the developer's own quick fix said to try, for now, deleting the local "options" file (presumably in its entirety) from your system.  But I have found a better way...

Go to your home directory, cd into the .ppracer hidden directory, edit the options file (using gedit or vi or emacs or your favorite editor).  Where it says "set turn_left_key 4" simply delete the "4".  And where it says "set turn_right_key 6" simply delete the "6".  Now save the revised options file and exit, and restart ppracer.

Now, the arrow keys work!  If you go and look at the options file with the cat command or whatever, you will see that the restart automagically inserted these values instead, which work:

set turn_left_key 276    and

set turn_right_key 275

So, no need to delete your whole options file.  Simply delete the turning settings and then the correct ones will appear in that file when you save the options file and restart the game.  Presumably, now that we know what the correct settings are, one could simply edit the options file and replace the "4" with a "276" and the "6" with a "275" to save a step or two.

PS:  How do I insert a box in here like the other posters do with their replies so I can insert my exact code used?

---

### Post by poiuytr on 2006-01-25
Oh, yeah, I just saw that the solution is here, too, on the ppracer website:

[http://projects.planetpenguin.de/forums/viewtopic.php?id=68](http://projects.planetpenguin.de/forums/viewtopic.php?id=68)

I hope these posts are helpful to others.

---

### Post by poiuytr on 2006-01-25
One other hint (sorry to be so verbose)...

If you disable the joystick in the GUI configuration settings (which I just did, figuring I don't have a joystick, so why would I need it set?) then that will once again trash your /home/xxxxx/.ppracer options file settings for set turn_left_key and set turn_right_key, and you will have to fix those all over again.

---

