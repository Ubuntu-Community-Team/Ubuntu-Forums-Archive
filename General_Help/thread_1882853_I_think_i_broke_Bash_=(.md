---
title: "I think i broke Bash =("
date: 2011-11-18
forum: General Help
---

### Post by elite4seth on 2011-11-18
Hiya, I'm a newbie at linux, i recently installed xubuntu and have been trying to learn the command line. I needed to get past " cd, ls, mv, rm". I was searching some sites to get me started on writing some scripts and this is what i was told to do: 

***Aliases***

*Now, before you become too confused about what I just said, let's make an alias. Make sure you are in your home directory. Using your favorite text editor, open the file .bash_profile and add this line to the end of the file:*

[I] alias l='ls -l';

[/I]So i try this, and it doesn't work. no big deal. I research a bit and find out that
Ubuntu doesn't use .bash_profile, and instead uses .profile.
So i assumed it would all be the same, i opened up nano in the command line.
I pull up .profile, which i think is something like .bashsrh and i add the alias line to it
i hit ^x to exit and save. at the save prompt i hit M-A to append, it asks for a file name and i said .profile

Now when i open my terminal it's just blank and accepts no commands =(((

Please and thank you! 

tl;dr: edited .profile, saved by appending to .profile, terminal broken


Edit 2: Is there a way that i can edit .profile not using the command line? i know using the GUI is a really....basic approach to this, but i'd really hate having to reboot Xubuntu on this computer. It was a pain to get it installed right on this computer as it is.

---

### Post by nixblog on 2011-11-18
ALT + F2 and type,

gedit

click on run button. That opens up gedit - open the file you want to edit within gedit, make changes and save.

Failing that, boot a Live CD of Ubuntu and you can browse and open the file on the hard drive that way too.

When you edit any type of config file, please make sure you create a backup of the file before you edit it.

---

### Post by nothingspecial on 2011-11-18
There is a default .profile in /etc/skel that you can replace your broken one with.

---

### Post by Lars Noodén on 2011-11-18
You can get a pristine copy of .profile from the location /etc/skel/.profle   Copy that onto your broken one using Nautilus or another file manager.

---

### Post by elite4seth on 2011-11-18
Thanks! i tried this, but gedit doesn't show .profile. Did you mean for me to run it in terminal? or the GUI, because there is an option for it, i ran the GUI and when i click open it just shows me all of my non-hidden files =\



To the other 2 replies, when i open terminal, it's just blank with a cursor. i type cd mystuff, nothign happens. i type ls, nothing happens. idk what to do at this point. am i hopeless?

---

### Post by nothingspecial on 2011-11-18
press H to see the hidden .profile in /etc/skel then overwrite the one in your home.

---

### Post by elite4seth on 2011-11-18
> **nothingspecial said:**
> press H to see the hidden .profile in /etc/skel then overwrite the one in your home.

My command line is just blank though. idk how to navigate to /etc/skel without a command line that says Seth-computer$:. Sorry for being so noobie =\

---

### Post by elite4seth on 2011-11-18
Solved it!

I had to run through the GUI's file manager and display the hidden files, then right click it to run through gedit. after that it was as simple as copy and paste through the /etc/skel directories the others were kind enough to point out to me. THANK  YOU SO MUCH 

<3 linux when i figure it out.

ps. idk how to change the tag to solved but imma try to figure that out XD i don't usually do forums, this is really my only exception.

---

### Post by MG&amp;TL on 2011-11-18
It's under thread tools, at the top.

---

### Post by nothingspecial on 2011-11-18
> **elite4seth said:**
> 

ps. idk how to change the tag to solved but imma try to figure that out XD i don't usually do forums, this is really my only exception.

Done :)

---

