---
title: "i have many questions"
date: 2010-08-05
forum: General Help
---

### Post by EpicFailGuy on 2010-08-05
first sorry for poor english 
  im new ubuntu user.. 
  i was triying to use ubuntu about 2 weeks.. 
  and have got lots of questions


  1. im not extreme game player.. just was playing casual WoW, League of Legends (LoL) some midnights  but i think cant play WoW on here, and frozen my account.. i searched  on google ppl plays "LoL" on linux i tried sooooo much time but couldnt  play .. 
  Q: i cant run installer with wine when i tried to run wine says all time "loading"... is that possible?
  
  i said "ok..nvm.. i couldnt play game.. but i can do different things.. maybe twitter, forums, reading newspaper, gimp etc.. 
  
  2. when i use scrollbar or mouse middle button graphics sux as that
  [http://img823.imageshack.us/img823/3448/ekrangrnts.png](http://img823.imageshack.us/img823/3448/ekrangrnts.png)
  Q: how can i fix?
  
  i said "nvm..lets watch some facebook videos when bored"
  
  3. hmm so hard to explain that 
  for example 
  when i click play video.. video starts streaming
  [======> ] 6% 
  omg! instant %100 now
  [===========================] 100% 
  %1 %2 %3 %4 %5 %6 %100  such as this
  so video stops when try to play more than %6 
  
  i can watch when refreshed page more than %6 but it stops %X again 
  i can watch when i refresh , refresh for just a video with 20 times repeating. i had give up
 (%6 was only example on my mind :P )
  
  i said "nvm" again just tried online backgammon etc.
  
  4. but i fail again cuz game says need java 6 but i have open java's last version.. how can i install sun java..
  
  i said "nvm" again cuz i was thinking can watch movie
  
  5.  i tried to watch movie.. but i sux again
  cuz all of ppl looks as "avatar"
 not epic.. only blue
 for example;
 [http://img43.imageshack.us/img43/658/ekrangrnts2e.png](http://img43.imageshack.us/img43/658/ekrangrnts2e.png)
 [http://img228.imageshack.us/img228/4897/ekrangrnts3k.png](http://img228.imageshack.us/img228/4897/ekrangrnts3k.png)
 
 i said "nvm" again..and tried pornograpic pages but i dont interest blue girls.. they re not for me 
 
 using: ubuntu x64
 my computer:
 amd x64
 8gb ddr3 1333ghz ram
 500WD HDD
 512mb graphic card
 
 and result : epic fail
 
 now.. what can i do on my computer?
 how can i fix that

THX for HELPS

---

### Post by J V on 2010-08-05
> **EpicFailGuy said:**
>  i cant run installer with wine when i tried to run wine says all time "loading"... is that possible?Install playonlinux, it makes wine much more easy> 2. when i use scrollbar or mouse middle button graphics sux as that
  [http://img823.imageshack.us/img823/3448/ekrangrnts.png](http://img823.imageshack.us/img823/3448/ekrangrnts.png)
  Q: how can i fix?Did you Install the drivers?> 3. hmm so hard to explain that 
  for example 
  when i click play video.. video starts streaming
  [======> ] 6% 
  omg! instant %100 now
  [===========================] 100% 
  %1 %2 %3 %4 %5 %6 %100  such as this
  so video stops when try to play more than %6 
  
  i can watch when refreshed page more than %6 but it stops %X again 
  i can watch when i refresh , refresh for just a video with 20 times repeating. i had give up
 (%6 was only example on my mind :P )What type of videos, where are you watching, have you considered that your internet just isn't fast enough to load the videos that quickly?> 4. but i fail again cuz game says need java 6 but i have open java's last version.. how can i install sun java..Did you install ubuntu-restricted-extras? OpenJDK is more compatible than sun java atm, ignore whatever "Advice" a program is giving you> 5.  i tried to watch movie.. but i sux again
  cuz all of ppl looks as "avatar"
 not epic.. only blue
 for example;
 [http://img43.imageshack.us/img43/658/ekrangrnts2e.png](http://img43.imageshack.us/img43/658/ekrangrnts2e.png)
 [http://img228.imageshack.us/img228/4897/ekrangrnts3k.png](http://img228.imageshack.us/img228/4897/ekrangrnts3k.png)
 
 i said "nvm" again..and tried pornograpic pages but i dont interest blue girls.. they re not for me Yes I've seen this before :)

Also related to driver, try installing it first, if it's still like this, try the other driver, lastly go to totem > edit > prefs > display > hue and move it all the way to either side

---

### Post by EpicFailGuy on 2010-08-06
5. Solved Thanks a lot!!1!one
4. Solved Thanks a lot!!!!!11


3. My connection stabilty bad... its so slow (it wasnt slow on windows as that.. i have dsl 4mbps..) 
2.sorry dunno..but there is a program on system which name "nvidia x server settings"
1. when i click most of programs exe or run with playonlinux wine says  "The program ******.exe has encountered a serious problem and needs to  close. We re sorry for the inconvenience.

---

### Post by EpicFailGuy on 2010-08-08
hmm i think i have to up my thread

---

### Post by EpicFailGuy on 2010-08-11
another up for my thread

---

### Post by EpicFailGuy on 2010-08-11
another up for my thread

---

### Post by Vaphell on 2010-08-11
if you try to run something with wine and for some reason it fails, do it from command line. I guess it's more scary than clicking stuff, but you get some feedback, meaningful error messages, whatever.

wine /path/to/the/exe/file.exe

to make things easier you can install **nautilus-open-terminal** - you will be able to open the terminal window in a proper location directly from context menu in file browser (right click). So navigate to the dir, open in terminal from context menu and run **wine filename.exe**
when app is installed in c: you need to navigate to a hidden folder in your home (.wine) ctrl+h to show hidden stuff.
**C:\** = **~/.wine/drive_c** so for example 
**C:\Program Files\SomeApp\App.exe** can be found in **/home/<yourname>/.wine/drive_c/Program Files/SomeApp**

---

### Post by Zorgoth on 2010-08-11
a) you are bumping too often
b) The latest version of wine is wine 1.3.  I recommend you get it.

To do this open a terminal (Applications > Accessories > Terminal)

Type the following cammands

sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo apt-get install wine1.3 

(if the second command fails, look for wine 1.3 in the Ubuntu Software Center - *after* running the first command and reloading the package lists)

Also, regarding WoW, what graphics card are you using?

Please post the output of the following commands (in the terminal):

glxinfo | grep direct
glxinfo | grep -i opengl
-ideally, the first should say something like:
Direct Rendering: Yes
and the second should say your openGL version is at least 2.0.

Finally, for running WoW, you should run it using the command-line switch -opengl, or else by adding the like
 
gxApi "opengl"

to

~/.wine/drive_c/Program Files/World of Warcraft/WTF/Config.wtf
(~ just means your home folder - to see .wine in your home folder, hit Ctrl-H to view hidden files)

Also, if you are using an ATI or nVidia card get the proprietary drivers - to do that, first try System>Administration>Hardware Drivers and if those don't work well enough you can try getting a newer one from the manufacturer's website.

---

### Post by EpicFailGuy on 2010-08-16
vaphell:

i wrote..and meaningful error here:
wine /home/username/games/LeagueofLegends/lol.launcher.exe

wine: Unhandled page fault on read access to 0x00007a58 at address 0x4010ee (thread 0009), starting debugger...
Usage:
    winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]

---

### Post by EpicFailGuy on 2010-08-16
Zorgoth:
thx i installed 1.3.

direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8200/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 173.14.22
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:

---

