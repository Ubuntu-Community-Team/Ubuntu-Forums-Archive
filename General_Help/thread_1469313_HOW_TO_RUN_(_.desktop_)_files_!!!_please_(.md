---
title: "HOW TO RUN ( .desktop ) files !!! please :("
date: 2010-05-02
forum: General Help
---

### Post by spayman on 2010-05-02
i have lately installed **planeshift** , a game for ubuntu wich u have to have **playdeb** first (**messed**) lol!
any way , at first , i had difficults to install it , as everyone do , coz it was on ( **.bin** ) , but finally : woop installed :)
(**messed again**) !
when it asks me for the repertory where to install the game , i did choose my home folder **home/user/opt/(the game)**
a shortcut created on desktop automaticly :)
there we go , i can't run this hortcut :( double clicked , opened , ... it just won't open :(
its in ( **.desktop** ) file , so , how we run these files ? 
coz i already have some problems with them !


when i run the game i get this error :

> **Untrusted application launcher**
The application launcher "planeshift.desktop" has not been
marked as trusted, if you do not know the source of this
file, launching it may be unsafe.

and as i know , i right clicked on the shortcut > properties >
permissions tab > (here i activate the allow executing the file as program)
but when i try the game , nothing happens this time , and i mean nothing , it just won't run :( won' open , nothing !
i have ubuntu 10.04 lucid lynx (the great one) ! 
so , please help me :)
please :)

---

### Post by Kunzem on 2010-05-15
I'm also quite new to Ubuntu and i'm also running Lucid Lynx :) (great os btw ) i also got the same error when trying to run planeshift , and noticed when installing planeshift there is a option at the end of the installation where it asks you permission for the game and it has two options yes or no , you have to change it to yes otherwise only root will have permission to run the game 

i uninstalled PlaneShift first to do this you have to get root access ( this is not a recommended option as it gives you access to the whole system , it's very dangerous like everyone says (whatever )) 
type in terminal > gksudo nautilus type in your password it should open a nautilus window where you have root access, now just navigate to planeshift and uninstall 

after that just install the game as you did before and select the yes option when asking for permission ( i think it's the last installation option of planeshift ) 

you should then be able to run planeshift

---

