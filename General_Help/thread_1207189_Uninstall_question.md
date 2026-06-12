---
title: "Uninstall question"
date: 2009-07-07
forum: General Help
---

### Post by oomar on 2009-07-07
while im not a noob i still dont know how to do this. 

i installed ubuntustudio-video in synaptic. this installs multiple programs and later i determined i didnt want the entire group of programs. unfortunately when you mark ubuntustudio-video for removal it only removes ubuntustudio-video but not the programs that come with it (its dependencies like kino and dvgrab and dvgrab requires vvjgrab and it does on and on) anyways so i want to know how i could somehow in this case uninstall ALL of the programs installed by ubuntustudio-video.

oh and if your solution includes the possibility of removing a dependecy for a program i am keeping id appreciate a guide on restoring the dependancy too. i believe there is a command for it but i havnt used it in long enough to remember.

SIDE NOTE: if anyone has or does currently use Varkon, im having trouble running it and ive already tried everything i know.. its slightly frustrating. PM me if you do. 


ummmm thats it i think. thanks

---

### Post by wojox on 2009-07-07
Terminal

```
sudo apt-get remove ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-look ubuntustudio-menu ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-theme ubuntustudio-video ubuntustudio-wallpapers
```

---

### Post by akakingess on 2009-07-07
> **wojox said:**
> Terminal

```
sudo apt-get remove ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-look ubuntustudio-menu ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-theme ubuntustudio-video ubuntustudio-wallpapers
```
Just a question for my own information, isn't there a way to list all of the apps/dependencies that are installed for a particular package? I thought I had seen something somewhere, but a search didn't turn it up. Thanks if you have the time, if not, it is not urgent.

---

### Post by oomar on 2009-07-07
ok no thats not what im looking for but i understand why you said that..


i installed ONLY ubuntustudio-video

not any of the other studio packages. Ubuntustudio-video installed kino and dvgrab and such and i marked ubuntustudio-video for removal but it doesnt remove kino and dvgrab with it. now while in this case there were only like idk... 5 programs so i manually deleted them. i still need to delete the dependancies they install tho. one program can install many different parts while it only removes part of those installed. if one program installs 50 other parts, when i remove it i want it to take those other 50 parts with it. that potentially may delete a dependancy for another program. thats my second question, is there a command for reinstalling lost dependancies? 

idk if thats understandable.

EDIT: oh and akikingess i am pretty sure there is but i cant remember it either. lol 

if it isnt just tell me to rephrase it.

---

### Post by oomar on 2009-07-08
there has got to be something?

---

### Post by 3rdalbum on 2009-07-08
The command you want is:

```
sudo apt-get autoremove
```

From the apt-get *man* page:

> autoremove is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no longer needed.

Let's say package A pulls in package B as a dependency, then you remove package A. Package B will remain. If you type "sudo apt-get autoremove", then the system will remove Package B.

If you've discovered that Package B is useful on its own and you want it to stay, then you can "apt-get install" it. The package manager will know that it is already installed, and mark it as "manually installed" so that the autoremove command will not remove it.

Autoremove will show you a list of packages that it is planning to remove. Read this list carefully! If there's anything that it has wrongly suggested for removal, type "n" (for "no") and "apt-get install" the packages that need to stay on your system, or manually remove the packages that you don't want to keep.

---

