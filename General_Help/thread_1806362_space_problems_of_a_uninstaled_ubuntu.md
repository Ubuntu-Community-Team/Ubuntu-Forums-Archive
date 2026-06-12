---
title: "space problems of a uninstaled ubuntu"
date: 2011-07-17
forum: General Help
---

### Post by enteunbuntu on 2011-07-17
after my laptop crashed out a month ago, a friend of mine, who is kind of an expert in informatic, temporarily solved my problem (the pc wouldn't start, and i'd lost my instalation cd). So, im using ubuntu (not installed), while my files on vista can still be accessed (even though, sometimes, it wil crash). Thing is, i wanted to install a game (call of duty), but none of the folders i can choose have enough space to install ( requires a little less that 5 GiB). Odd thing is I have 18 GIB unused in Vista partition and 87 GiB unused in another partition called Data. Then, how can i use some of this free space (at least 5 GIB so i can install the game)? do i have to create a new partition? if so, how can i do it?

thanks

---

### Post by jon zendatta on 2011-07-17
I don't understand, your title states Ubuntu uninstalled yest you say you're using Ubuntu and you've lost the cd. If you have Ubuntu go to a terminal and enter
[PHP]sudo apt-get install gpart[/PHP]
have a play with this to reformat your partitions

---

### Post by enteunbuntu on 2011-07-17
jon, im using ubuntu without installing it (don't know how its possible, but it is so), and the cd i mention is the one for vista that came with my laptop.
I did what you suggested, but when i open Gparted  (where we can see and, i guess, modify the partitions) i don't see any thing different. i would like to know if its possible to create a new partition with 5 GiB free and then use it to locate the game files. i know very little about computers, much less ubuntu, so i'm not that tempted to be criative (plus, i have all the things on the vista disk that didn't want to loose). 

please ubuntu people, please help me. besides books, cinema and law, im not a competent nerd. could you computer nerds help out an equal in need? cheers

---

### Post by ajgreeny on 2011-07-17
If you are running from a live CD you can't install anything, as it will be lost when you reboot.  I have no idea about Call of Duty that you want to install, but if it is a windows game, installing wine could help you run it.  However as I said, you can not really install wine in a live CD version of ubuntu, and you most definitley can not install a game into windows from ubuntu.

I think you may have to bite the bullet and get windows running again for the game, or install ubuntu over part of the vista space and try running your game in wine.  If I have got it wrong, and this is not what you are asking about, I don't see what you mean, so please explain more fully.

---

### Post by enteunbuntu on 2011-07-17
i know it won't really be installed (when i restart the computer it's gone), but until i shut down it should work, right? this is, if it can be installed. im probably limited to the space of the pen i use with ubuntu (not even one GiB), but i was  assuming i could use space from the disk to install the game. the first seems more likely, but i really can't say.
i've already installed Wine.

edit: I would install ubuntu over part of Vista if i could do it without  loosing things i care about, and i don't know how to do that.. was just trying a temporary way of playing the game, before handing the pc to someone who knows what he's doing lol.
thanks for your help

---

