---
title: "Wine not liking game (4 star rating on winehq)"
date: 2011-03-30
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-03-30
i attached a scan of the cd cover
it gives a few red/green/blue squares in the lower left corner and crashes
have  tried wine 1.2 and 1.3 same result

---

### Post by mattgyver83 on 2011-03-30
I may be stating the obvious though try changing your default 'windows version' or setup a custom configuration for the *.exe explicitly.  Both of these actions can be done via winecfg.

[LIST]
[*]To change default make sure "Default Application"  is selected and change the Windows version in the bottom right.

[*]To add the application itself click "Add Application" locate the executable (generally in ~/.wine/drive_c) and specify the Windows version you wish to use.  *Note* global settings will have the application use your default application settings.
[/LIST]

Generally doing one of the above clears up some issues.

---

### Post by pqwoerituytrueiwoq on 2011-03-30
this is the only wine app installed in wine
i am trying to install a virtual machine but the cd keeps crashing on it

---

### Post by flipper T on 2011-03-30
you are dual booting with win 7 ?


i think i see a solution...

---

### Post by pqwoerituytrueiwoq on 2011-03-30
on a p4 with 1.5gb ram integrated video no-thanks
---edit---
installed xp and put the game on startup 
the game lags on that video card
it seems to open with a video like entry and it looks like that crashes it

---

