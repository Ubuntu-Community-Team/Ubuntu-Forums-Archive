---
title: "Trouble with Wine"
date: 2005-02-11
forum: General Help
---

### Post by Mongol_Samurai on 2005-02-11
I'm having some trouble with installing Wine... I'm pretty well trained in the concepts of the command line and all, but as far as using actual linux boxes, my experience is limited, so bear with me... I downloaded Wine 20050111 from sourceforge, unzipped it, all that nice stuff... tried to configure it and found i had no compiler... so i installed the gcc package that was available in APT (3.3 i believe) and all the various other dependancies (like bison). Now i can do ./configure in the Wine directory, and make depend works, but after i do that and i go to run plain old make, it bounces around in directories for a little while, then spits out a huge number of syntax errors (all the same error: Error: syntax error; found `@' but expected `,' then something about junk at the end of the line) Then winegcc anounces that gcc failed and make coughs up a few more errors, then nothing.
What do i do to make this work? I'm trying to get World of Warcraft to run on my box (it's a Mac OS X 10.2.8/Ubuntu dual boot) so if there's an easier way to do this, please let me know!

---

### Post by YokoZar on 2005-02-17
[QUOTE=Mongol_Samurai]I'm having some trouble with installing Wine... I'm pretty well trained in the concepts of the command line and all, but as far as using actual linux boxes, my experience is limited, so bear with me... I downloaded Wine 20050111 from sourceforge, unzipped it, all that nice stuff... tried to configure it and found i had no compiler... so i installed the gcc package that was available in APT (3.3 i believe) and all the various other dependancies (like bison). Now i can do ./configure in the Wine directory, and make depend works, but after i do that and i go to run plain old make, it bounces around in directories for a little while, then spits out a huge number of syntax errors (all the same error: Error: syntax error; found `@' but expected `,' then something about junk at the end of the line) Then winegcc anounces that gcc failed and make coughs up a few more errors, then nothing.
What do i do to make this work? I'm trying to get World of Warcraft to run on my box (it's a Mac OS X 10.2.8/Ubuntu dual boot) so if there's an easier way to do this, please let me know![/QUOTE]There are Wine binary packages available, at the WineHQ website no less.  [http://www.winehq.org/](http://www.winehq.org/)  - check the downloads page, and click the Ubuntu icon.

---

