---
title: "direct 3d help"
date: 2010-01-27
forum: General Help
---

### Post by panterus on 2010-01-27
ive been having trouble getting eve online to run properly on ubuntu 9.10 and wine 1.137 seems to have trouble converting the direct 3d to open gl and i have to reinstall after each effort to get it to run otherwise i just get a splash screen then nothing. i have use the system moniter to get it to stop running as it says it is sleeping and shows it to be waiting in pipe. im unfamiliar with bash commands but one person on the eve forums suggested getting into the eve directory from the terminal and typing:

sudo iptables -A OUTPUT -j DROP -p udp --destination-port 53 ; wine ./eve.exe ; sudo iptables -F

now he warns about it potentially disabling firewall setting and also he mentions a timing issue in the loadout and some dns request coming in too early and this command blocks it and then reenables before the actual program starts.

i used this and it worked a few times to get the program up and running after that it didnt work. also it didnt run long when it did work. everytime i tried to change a setting and apply it something in the caching of those settings and/or the call on the direct3d-->opengl causes the program to fail with an exception. if i try to run the program without changing settings it will try to use shader model 3 something that my machine is incapable of using. although, i did run through the character creation process and when it went through it did have the model present but it was just a glowy wire frame that i could move but could not change any textures at least not visibly. after a short time it must have overloaded and crashed. 

i havent tried any other graphics based programs on wine yet, but i will to see if it is just this one or if it is wine's operation of the directx --> open gl crossover. any help in the meantime would be appreciated. was running the program with virtual desktop enabled btw.

p.s. sorry for the wall of text

tl;dr I NEED HELP WITH THIS *!@#$&$%!* DIRECT3D PROGRAM!!!!! :popcorn:

---

### Post by panterus on 2010-01-27
i have heard from the eve forums that there seems to be an issue directly related to 9.10 looking into maybe having duall boot with 9.04 need to figure out how to do that properly now

---

### Post by panterus on 2010-01-28
bump

---

### Post by panterus on 2010-01-28
bump

---

### Post by clhsharky on 2010-01-28
HI

Try looking for help in Wine section.
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)


Sharky

---

### Post by panterus on 2010-01-28
thanks trying there as well heheh

---

