---
title: "Pro/E 5 anybody?"
date: 2010-09-23
forum: General Help
---

### Post by x C0MMAND0 x on 2010-09-23
Couldn't find much information on this in Wine.  Short version: I need to install Pro/Engineer version 5 for my college courses (majoring in mechanical engineering).  I need to get this installed in Wine, otherwise I will be forced to install it on my Windows partition (yuck).  I have been able to get Linux versions for all of the advanced math programs I use (Maple, Mathematica and Maple), but unfortunately there is no native version of Pro/E for Linux, only winodows.

I have the .exe downloaded, and I ran the installer in Wine, and it looks like everything worked, but there is no .exe to run.  It should be located in "wine "C:\Program Files\ProENGINEER Schools Edition\bin\proe.exe" ", but there is no proe.exe. 

I am wondering if anybody has used/installed this program and any tips you can provide on how to get it to work?  It seems from googling around a bit that people have gotten previous versions of this to work.

Any ideas/tips/suggestions are appreciated, thank you!

---

### Post by x C0MMAND0 x on 2010-09-23
*bump*  Any other Engineers out there using Linux?

---

### Post by betterthanjordan79 on 2010-09-28
I would also like some help with this...something tells me tho that wine wont run it and if it does it would b horrible...

---

### Post by ronnielsen1 on 2010-09-28
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17101](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17101)

Pro Engineer 4 , yes Pro/E 5 Not yet

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20990](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20990)

---

### Post by x C0MMAND0 x on 2010-09-30
I was able to obtain a copy of Pro/E 4 through my school, and it *seems* to have installed in Wine just fine.  When I try to run the program, it *seems* to load, (I get a splash screen), and then the program goes to full screen but it is just black.  The only way out is to go to a different terminal (ctrl-alt-f2), run TOP and then kill the process.  I can't run the program via terminal to see what the error is.  Any ideas at all?  Am I missing something obvious?  I also tried telling Wine to run in a windowed mode as to avoid the full screen, but that did not work.

---

### Post by ronnielsen1 on 2010-10-03
Which version of windows are you trying to emulate (Yes, I know wine is not an emulator)? You might choose a different one (XP - 98)
Why can't you run from the command line? What errors are you getting? If you have the program installed it should be in the vicinity of /home/commando/.wine/drive_c/Program\ Files/

Substitute commando for your user names. Add whatever extra folders. An example would be if the next folder is Pro Engineer you would type it in

cd /home/commando/.wine/drive_c/Program\ Files/Pro\ Engineer/

The \ and space are only used if the folder has 2 or more words in the name as in Program Files

---

### Post by skorvkalle on 2011-10-03
Sorry for bumping an old thread, but how did you do? Did you get Pro engineer to work in ubuntu? I'm using Ubuntu 11.04 and have the same problem with black screen when I'm trying to launch Pro engineer. Does anyone know how to solve this and get pro engineer to work in Ubuntu 11.04?

---

### Post by x C0MMAND0 x on 2011-10-05
I ended up just installing virtualbox and then installing TinyXP (do a google search because it's not technically a legal installation of Windows and I don't want to violate the forum terms of use), and then I installed Pro/E 5 (and many other Engineering programs, Matlab w/ Simulink, Mathematica, Maple) in the Virtual machine and ran it that way.

---

