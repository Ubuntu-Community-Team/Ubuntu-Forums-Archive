---
title: "I Have Some Issues (ePSXe, WINE, &amp; others)"
date: 2011-07-24
forum: General Help
---

### Post by Sehtey on 2011-07-24
[FONT="Comic Sans MS"]If this is in the wrong forum, please let me know. :)

Okay, I installed Ubuntu about two weeks ago instead of Windows, and I have some problems installing a lot of necessary programs, first of all, using the Terminal is weird for me, I love using it but I'm not used to it so please bear with me. 

Installing Wine got a weird issue but it did succesfully install, I might reinstall it though. 

Now, ePSXe, I've searched for hours on end and found no clear way of installing it, can anyone help please?

Also Vuze (For the client for streaming things) I have problems with that too, since trying to install I keep getting this when the terminal opens
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Also, I'm interested in game development, but I don't know where to start, anyone got any advice?

Thanks, sorry if this seems like a lot.  [/FONT]

---

### Post by wildmanne39 on 2011-07-25
Hi, until you fix this E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem, I do not think you can install anything.

Run these commands in terminal
```
sudo dpkg --configure -a
```
```
sudo apt-get clean
```
```
sudo apt-get update && sudo apt-get upgrade
```
and if you get errors post the complete thing back here by clicking on new reply and click # and paste the information between the brackets.

Please use normal fonts and characters.
Thank you

---

### Post by Sehtey on 2011-07-25
After running the commands, the first one ran perfectly, then sudo apt-get install clean didn't do anything, just kept returning me to the standard terminal (When you first open it if that makes sense) then your next two worked fine except when it came to what I think was Wine asking me to agree to something, I couldn't click or do anything.

thanks btw :)

---

### Post by wildmanne39 on 2011-07-25
> **Sehtey said:**
> After running the commands, the first one ran perfectly, then sudo apt-get install clean didn't do anything, just kept returning me to the standard terminal (When you first open it if that makes sense) then your next two worked fine except when it came to what I think was Wine asking me to agree to something, I couldn't click or do anything.

thanks btw :)Hi, if there is an agreement you can agree to it by using the arrow keys to high light it then hit enter. Do that and see what happens.

The clean command does not show any thing on the screen it just does its work with out being seen as many commands do.

---

### Post by Sehtey on 2011-07-25
> **wildmanne39 said:**
> Hi, if there is an agreement you can agree to it by using the arrow keys to high light it then hit enter. Do that and see what happens.

The clean command does not show any thing on the screen it just does its work with out being seen as many commands do.


Ah okay thanks for your help. :)


[QUOTE=lovewithyou8808;11083397]thanks to the forum to have a post
this is a wrong forum for you]/QUOTE]


By that you mean what exactly?

---

### Post by wildmanne39 on 2011-07-25
Hi, let us know how it goes.

Where did you see that quote about the wrong forum?

---

