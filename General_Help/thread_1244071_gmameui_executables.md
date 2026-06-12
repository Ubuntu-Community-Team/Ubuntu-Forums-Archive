---
title: "gmameui executables?"
date: 2009-08-19
forum: General Help
---

### Post by eekfonky on 2009-08-19
I have installed sdlmame and gmameui, but when I open it it asks for 'executables' what are these and where do i find them, I have downloaded some ROMs and unzipped them but I don't know what to do next? Please help

---

### Post by zvacet on 2009-08-19
Read **install** file in gmameui folder.

---

### Post by eekfonky on 2009-08-19
where is the folder kept?

---

### Post by zvacet on 2009-08-19
When you unpack tar.gz you will have folder.In that folder is install file.

---

### Post by paok4 on 2009-08-19
I have the easiest solution for you !!! Download this Ububntu based distro from Greece (dont worry everything is in English) which contains the MAME Arcade Games suite with 600 selected games and they play perfectly !!! 

[LEFT][IMG]http://www.monomaxos.host56.com/eng.files/image011.jpg[/IMG]  [IMG]http://www.monomaxos.host56.com/eng.files/image012.jpg[/IMG]   [IMG]http://www.monomaxos.host56.com/ver3.files/image021.jpg[/IMG]
[/LEFT]
 
The distro is called MONOMAXOS (its the Greek word for gladiator) It works as a live cd and has embbeded wubi support for installation inside windows.

The English version can be downloaded from [HERE]("http://ftp.ntua.gr/pub/linux/monomaxos/monomaxos-3.0.eng.iso") and more information about the hall project can find at [http://www.monomaxos.gr/eng.htm](http://www.monomaxos.gr/eng.htm)

Happy play !!!

---

### Post by eekfonky on 2009-08-19
I found the folder in home/myname/usr/games/sdlmame

Thanks, now all I need to do is download the games.
I got Ghouls n Ghosts but cannot seem to play it? What are the controls on the keyboard for gmamui?

---

### Post by Ralph Hinkley on 2011-11-22
Another solution is (for those who want one) Go to the Ubuntu software center and install kxmame frontend. It works a lot better (at least it does on 10.04.)

Also, to answer your earlier question: The "executable" file is "xmame" also available from the software center, but if you run kxmame, it seems to already know where to look for the file, whereas Gmameui wants to be told where to find it.

Hope this helps. If I'm misstating anything, I welcome corrections. I only just resolved these issues myself so I figured I'd share what I found.

---

### Post by Ralph Hinkley on 2011-11-24
Okay. I just tried to get mame working on my newer laptop running 11.10. Kxmame does not seem to be available in the software center. Instead I downloaded Gmameui and mame. 

The first time you run Gmameui, it will ask for "executables". click the "add" button and navigate to the filesystem/usr/games folder. The Mame executable file should be in that folder. to add the folder, navigate to usr/games, then select the folder ONCE and click add. 

Good luck!

---

