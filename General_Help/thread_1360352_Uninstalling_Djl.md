---
title: "Uninstalling Djl"
date: 2009-12-20
forum: General Help
---

### Post by Bootydancechamp on 2009-12-20
I installed djl to play some games using these instructions from going linux.
Installing DJL
You can follow the instructions in the article referenced above, or follow Tom's instructions, below. Here is how Tom got started with DJL:

Step 1. I downloaded the script and save it in your home directory. This is the command line:
  wget [http://en.djl-linux.org/maj_djl/archives/djl-1.2.20.tar.gz](http://en.djl-linux.org/maj_djl/archives/djl-1.2.20.tar.gz)
Of course that's a tarball (a type of archive file) containing the script. The archive contains one folder with several files. 

Step 2. I used "extract here" in Nautilus. That worked. 

Step 3. Now to install Python. If you are using Ubuntu 9.10 or later you already have it and can skip this step.
  sudo apt-get install python-qt4
I already had it, but the exercise proved that the command is right. At first this command didn't install Python at all on Larry's older machine running Ubuntu 8.10, but that may have been because it had not been updaed in a while. After running the updater, it installed without a hitch. 

Step 4. Now give the script permission to run. 
  chmod +x ~/djl/djl.sh

Step 5. Now run the script; 
  sh ~/djl/djl.sh

It worked and djl ran.  However, none of the games it downloads will run.  I would like to uninstall djl but it is not in synaptic and I dont know any command lines to get it to uninstall.  Does anyone know how I would do this?

---

### Post by louis_mallow on 2010-01-13
Hi, I was wondering if you ever got an answer to this as I have the same issue.

---

### Post by lucidbuddha on 2010-01-19
Bump. Same problem.

---

### Post by Mercenary410 on 2010-04-19
Hey guys. All djl does, is run from whatever folder you downloaded and installed it from, the only directory it creates, is the directory it uses to install games. 

so to uninstall, simply find the location of where djl install games to 
(Menu > Settings) 

delete the given directory, and then find where you downloaded and extracted djl to (presumably your Downloads folder) 

and then delete it. To remove the icon from your applications menu;

go to System > Preferences > Main Menu, and delete the djl key from the Games tab

:)

---

### Post by joshklewis on 2010-05-14
I am not quite ready to give up on DJL yet, but does anyone know how to get the games to run once you download them? I am using Ubuntu 10.04.

---

### Post by joshklewis on 2010-05-14
I don't know if this will help anyone or not, but it is worth a shot. I was having trouble using DJL just like the person who started this thread. I could not get the game to play after I downloaded it. Instead of right clicking on the game and hitting play or going to the games tab and hitting play, I went to the Repository tab. I clicked on the play button above Remove and Update. The game loaded just fine when doing it that way. Trying to run the game only worked for me if I did it by hitting that button.

---

