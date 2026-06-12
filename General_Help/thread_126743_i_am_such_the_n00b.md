---
title: "i am such the n00b"
date: 2006-02-07
forum: General Help
---

### Post by rock lobster on 2006-02-07
Ok so here is my deal. I have wanted to switch windows to since i started college 2 years ago.... so i finnally took the time to find an OS i liked, Also as you can see im new to the forum, so here i am with Gnome ver. of Ubuntu Breezy Bager and it is awesome, i love it. i have Ubuntu installed on my laptop i had used ndiswrapper for my broadcom drivers. but being a windows user for so long i never had to compile programs, so i have no idea what im doing... so basically i have a few questions for anyone who wants to help me...
first i dont dont know how to compile programs from tarballs, also i was hoping some one could send me in the right direction as far as a good wifi sniffer. (ie to find access points)

thanks in advanced  :confused:  :confused:  :-k

---

### Post by kaamos on 2006-02-07
Hello and welcome to the forums!

What program are you trying to compile? Or did I misunderstand and you are trying to get ndiswrapper going?

---

### Post by infoseeker on 2006-02-07
This site could be useful

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by cotcot on 2006-02-07
Many tars are installed as follows :

tar zxvf newprogram
cd  newprogram
./confirgure
make
sudo make install

For this you need to install built-essentials

---

### Post by stoffe on 2006-02-07
[QUOTE=cotcot]Many tars are installed as follows :

tar zxvf newprogram
cd  newprogram
./confirgure
make
sudo make install

For this you need to install built-essentials[/QUOTE]
That would be "./configure" ;)

You can also install [FONT="Courier New"]checkinstall[/FONT] and exchange that last row for:

sudo checkinstall

That way, the program will be listed in the internal databse and can be uninstalled later via synaptic.

For the most part, you usually don't need to compile much - or anything. Try to find it in Synaptic first or ask in these forums if someone has a version already for Ubuntu. Most things except bleeding edge is available one way or the other.

---

### Post by rock lobster on 2006-02-07
im trying to compile prismstumbler.. but if anyone has a better program im open to sugestions. Thank you for all your help guys

---

### Post by nanotube on 2006-02-07
hey
you dont need to compile prismstumbler - it is available in the synaptic repositories!
just enable the universe repository (in synaptic, Settings>Repositories>Add, and check the checkbox next to universe [might as well add multiverse too, while you are here]). 
and then click "reload" button to load all the info up in synaptic, and then click "search" and search for prismstumbler, and it will show up. you can just mark it for installation, hit apply, and it will be installed, no pain. :)
see my repositories walkthrough for more info on repositories:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Ubuntu_Repositories_and_sources.list](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Ubuntu_Repositories_and_sources.list)

---

### Post by rock lobster on 2006-02-07
i got the repositories down path pretty well..  for example i have another computer running the server end of ubuntu its a file/web server and i had to edit and all that stuff dealing with repositories.. the only thing is when im on my laptop and i  download and install prismstumber i get and error for some reason. its not only the fact that i want to get the sniffer running but i want to know how to compile for future software. i guess im too set in my windows ways :-# you guys are a great help though, i have been reading through some of those links you gave me and they are very helpful... the only thing is that i didnt see much info on dvd playing software that is another problem i cant find a decoder that works for me. i know im asking alot for a first timer, but any suggestions on that too? :???: 

thanks guys

---

