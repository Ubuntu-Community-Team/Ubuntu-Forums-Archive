---
title: "ATI Catalyst 10.2 - Power states fail"
date: 2010-03-08
forum: General Help
---

### Post by shockandawe on 2010-03-08
My video card runs hotter in Ubuntu 9.10 than in Windows.

This is because it is always set to 3D powerstate. In Windows it is always set to 2D powerstate, and it will switch to 3D once a 3D application is launched (like a game).

I've tried the command:

>aticonfig --set-powerstate=1

but I get this error:

>aticonfig: unrecognized option '--set-powerstate=1'
>aticonfig: parsing the command-line failed.

How can I get his command working?! Or is there a workaround I can use? 

This is driving me nuts. My card is sitting very hot for no reason. 


Cheers.

---

### Post by shockandawe on 2010-03-09
Can anyone help? Or tell me where I can go to get help?

This is a pretty serious issue, I don't want to burn my card.

Cheers

---

### Post by shockandawe on 2010-03-09
Bumpage!

---

### Post by shockandawe on 2010-03-10
Bump!

Are these powerstate commands removed from the latest ATI drivers or something?

---

### Post by Mark Phelps on 2010-03-11
Link below is to Phoronix forum discussion of powerstates:  

[http://www.phoronix.com/forums/showthread.php?t=20107]("http://www.phoronix.com/forums/showthread.php?t=20107")

Realize that it's for an older Catalyst version, but maybe it will help or lead to other Phoronix threads that will.

---

### Post by prodigy_ on 2010-03-11
This problem isn't really exclusive to Linux. In Windows, ATI driver automatically switches between 3D mode (full-screen 3D application) and 2D mode (everything else). For example, if you play a game in windowed mode, you'll still be in 2D mode with lowered clocks and disabled CF.

Linux driver considers Compiz a 3D application and switches to 3D mode whenever you enable "Visual Effects" in Gnome. So make sure that visual effects are completely turned off and reboot. After that you should be in 2D low-power mode.

It certainly works this way for my 4870x2, even though I can't manage powerstates manually either.

---

