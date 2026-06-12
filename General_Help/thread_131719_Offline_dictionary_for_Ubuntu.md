---
title: "Offline dictionary for Ubuntu"
date: 2006-02-17
forum: General Help
---

### Post by rkakkar on 2006-02-17
Although I'm now 100% ubuntu, when I had windows on my machine I had this great software called WordWeb. Particular I like the feature that when the program is in the tray you can look up a word in almost any program by pressing Ctrl+Alt+W or clicking on the icon.

Are there any alternatives for Ubuntu?

---

### Post by Bakerconspiracy on 2006-02-17
You could write an alternative using a free dictionary...

---

### Post by rkakkar on 2006-02-17
okay.. any tips on getting started? I'm a Java programmer.

---

### Post by nanotube on 2006-02-17
although you are welcome to code something up if you really want to :), i would recommend trying wordnet. here is a link:
[http://wordnet.princeton.edu/](http://wordnet.princeton.edu/)
it is available from the repositories as package "wordnet".

---

### Post by rkakkar on 2006-02-17
[QUOTE=nanotube]although you are welcome to code something up if you really want to :), i would recommend trying wordnet. here is a link:
[http://wordnet.princeton.edu/](http://wordnet.princeton.edu/)
it is available from the repositories as package "wordnet".[/QUOTE]


okay i downloaded the package, but you gotta use it on the command line? that sucks!! i wanted something where i could just highlight the word and look it up or worse some gui panel where i paste the word and look it up.

---

### Post by engla on 2006-02-17
Hey, why are you not mentioning gnome-dictionary? 

Try Applications > Accessories > Dictionary

Should be in any Ubuntu install


That's a screenshot.. kind of lame, but the dictionary only supports english words but the interface is in my language (swedish)

---

### Post by rkakkar on 2006-02-17
[QUOTE=engla]Hey, why are you not mentioning gnome-dictionary? 

Try Applications > Accessories > Dictionary

Should be in any Ubuntu install


That's a screenshot.. kind of lame, but the dictionary only supports english words but the interface is in my language (swedish)[/QUOTE]
keyword = **offline** :)

---

### Post by frühstück on 2006-02-17
i use "ding", i think thats exactly what you want

---

### Post by engla on 2006-02-17
[QUOTE=rkakkar]keyword = **offline** :)[/QUOTE]
Whoa. I'm sorry but the fact that gnome-dictionary used the web to get the data was totally unknown to me; the process to fetch the words does that wholly transparently.

---

### Post by rkakkar on 2006-02-17
[QUOTE=frühstück]i use "ding", i think thats exactly what you want[/QUOTE]
I installed ding; but by default its in german!! how can i change the language to english? Also, how can I assign a dictionary to it?

---

### Post by Starchild on 2006-02-17
I heartily recommend Longman's new [dictionary]("http://www.longman.com/ldoce/about_cd.html"). I was really stoked to see they started supporting Linux at last. Check it out!

---

### Post by Q65 on 2006-02-17
stardict is what you're looking for, its multilingual

---

### Post by nanotube on 2006-02-17
dude, wordnet has a gui.
just run command "wnb" from a terminal, and the gui will come up. you probably ran "wn", which is their cli interface.
(and of course you can add an entry for wnb in your applications menu so you dont have to open a terminal at all).

---

### Post by jetpeach on 2006-03-12
I too missed WordWeb a lot after coming to linux - I found this thread looking for a replacement.  For me, Starnet was definitely the best of the ones I tested.

The steps I took set it up were simple (though I would've liked them to be even simpler).  Basically, run synaptic -> search starnet, install...  It showed right up under Utilities for me, so I didn't have to worry about any command line junk.

But the part that was still simple but got me, was there was no dictionary installed for it by default.  I needed to go to 
[http://stardict.sourceforge.net/Dictionaries.php](http://stardict.sourceforge.net/Dictionaries.php)
and download a dictionary (Longman looked good/big for English).  Just put it in the starnet directory as stated on that page, restart starnet (if you had it running) and bam, you're set.  I'm running Kubuntu, maybe in Gnome a default dictionary is found?  I'm not sure, but not that big a deal.

I have to say, I think I'm going to like this even more than WordWeb - it's slick, I configured it so I can just press the Win key anytime a word is highlighted and the definition just shows up without any delay/loading of junk.  Definitely slick.

Anybody know if their is a KDE widget that does something like Starnet?  Maybe I could free some memory if I found something that was native for Kubuntu instead of Gnome...

---

### Post by pranav on 2006-04-18
[QUOTE=nanotube]dude, wordnet has a gui.
just run command "wnb" from a terminal, and the gui will come up. you probably ran "wn", which is their cli interface.
(and of course you can add an entry for wnb in your applications menu so you dont have to open a terminal at all).[/QUOTE]


I hit wnb n the gui does come out. Please tell me how do i add an entry. 
I am using KDE.

---

### Post by nanotube on 2006-04-18
[QUOTE=pranav]I hit wnb n the gui does come out. Please tell me how do i add an entry. 
I am using KDE.[/QUOTE]

hmm, well, i am using gnome, and i haven't laid my hands on kde in many years, so i don't recall off hand. but if you just look around in the menu of kde, i bet there is some kind of a menu editor? 

either that, or just wait for someone who uses kde to answer, or search these forums for editing kde menus...

---

### Post by kenati on 2006-09-26
Kenneth from Kalinga, Philippine. - Is it possible to have multiple dictionary files within /usr/share/stardict/dic (or in windows - c:\program files\stardict\dic)? Plz reply...

---

### Post by kenati on 2006-09-26
Excellent!!! Yeah it is possible to have multiple dictionary files. I just downloaded the dictionaries I wanted and extracted them to /usr/share/stardict/dic

---

