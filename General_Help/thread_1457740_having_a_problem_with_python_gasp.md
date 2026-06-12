---
title: "having a problem with python gasp"
date: 2010-04-19
forum: General Help
---

### Post by purdurabo on 2010-04-19
i have been going through a tutorial book called:How to Think Like a Computer Scientist. [http://openbookproject.net/thinkcs/python/english2e/ch04.html](http://openbookproject.net/thinkcs/python/english2e/ch04.html)
it is a very good book, i have managed to learn a lot from it. but now i have run into bit of a problem. in chapter 4:conditionals the he introduces python gasp. so i followed the instruction in the appendix about how to install the gasp lib. i used the synaptic package manager to install gasp. everything came back clean, no errors, no fails.(by the way i am running the python in IDLE 2.6 and i have the 2.6 interpreter) 

normally i just copy/paste or write my code in the edit window then run it in the shell. the gasp code examples that he give in the book have a funny (not ha ha funny) result when i try to run them. ex:

```
from gasp import *          # import everything from the gasp library

begin_graphics()            # open the graphics canvas

Box((20, 20), 100, 100)     # the house
Box((55, 20), 30, 50)       # the door
Box((40, 80), 20, 20)       # the left window
Box((80, 80), 20, 20)       # the right window
Line((20, 120), (70, 160))  # the left roof
Line((70, 160), (120, 120)) # the right roof

update_when('key_pressed')  # keep the canvas open until a key is pressed
end_graphics()              # close the canvas (which would happen
                            # anyway, since the script ends here, but it
                            # is better to be explicit).
```when i try to run this code (and other gasp code) i get a small dialog 
box come up named "kill" and a big one named "gasp". the problem  is that
the close button on the kill box does not respond. there is no way to 
close this box. i have to log-out and back in to stop it. here are some
screen shots of what i am talking about. (please see attachments)

ps. it is not only the gasp code that acts fuuny. when ever i type 
something like "raw_input()" when i go to press the shift+9 keys(to create " ( "  )a small
blank dialog box pops up in the corner of my screen with the title
"idle".

any help would be greatly appreciated. thanks.

---

### Post by Pvt Helmet on 2010-06-15
I had this same problem. The problem only happened when I ran the script through IDLE by pressing f5.

The problem did not happen when I opened a terminal and ran the script by typing:

python script_with_gasp_import.py

You can avoid the problem by running the scripts in a terminal instead of IDLE.

---

### Post by Warnock881 on 2010-07-03
I have the same problem. I ran gasp using terminal, but the same thing still happens where my cpu starts running at 100% and my fan starts going crazy the only way to stop it is to log off then log back in. I have gone to system monitor and i cant see any processes that are causing it to run that high. Any ideas on how to fix this?

---

### Post by a7mad3abed on 2011-04-12
> **Pvt Helmet said:**
> I had this same problem. The problem only happened when I ran the script through IDLE by pressing f5.

The problem did not happen when I opened a terminal and ran the script by typing:

python script_with_gasp_import.py

You can avoid the problem by running the scripts in a terminal instead of IDLE.
 
Thank you >> you solved the problem for me

---

