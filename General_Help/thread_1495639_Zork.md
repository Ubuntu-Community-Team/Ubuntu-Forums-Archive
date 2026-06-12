---
title: "Zork"
date: 2010-05-28
forum: General Help
---

### Post by subcook on 2010-05-28
Is there a free download for the first/original zork out there that would be able to be played through linux?



-cheers

---

### Post by jerrrys on 2010-05-29
you can play your DOS games on linux

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dos+emulator&as_qdr=all&sa=Google+Search&lang=en#863](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dos+emulator&as_qdr=all&sa=Google+Search&lang=en#863)

i have zork1, is that the original?

---

### Post by geirha on 2010-05-29
I believe you can find it on [abandonware](http://en.wikipedia.org/wiki/Abandonware) sites, but as the wikipedia article says, that doesn't necessarily mean it's legal to download. I'm no expert on copyright law, so you'll have to figure out the legality yourself.

---

### Post by srs5694 on 2010-05-30
Note that there are two issues here:


[list]
[*]Zork, and other titles from Infocom, were written in a virtual machine known as a [Z-machine.](http://en.wikipedia.org/wiki/Z-machine) The titles you could buy for MS-DOS, Commodore 64, Atari, etc., consisted of a Z-machine interpreter and a game file for the Z-machine interpreter. Several third-party Z-machine interpreters are available today, including several for Linux. I see that the frotz and xzip Z-machine interpreters are available for Ubuntu, and others may be as well. Many of these Z-machine interpreters are open source.
[*]The Zork title specifically is widely available in many forms, but I'm not sure if any are legal to redistribute freely. If you've got a legal copy for any platform, though, you should be able to use the story files themselves with a Linux-native Z-machine interpreter. I personally have run the stories from the "Lost Treasures of Infocom" compilation with a Linux Z-machine interpreter (frotz, IIRC), but it's been a while so I don't recall the details. You could always check eBay for a legal copy -- but you might have trouble reading the files from an obscure 1980s 5.25-inch floppy disk format!
[/list]

---

### Post by Ronok on 2010-10-28
I Played **ZORK** 1 on a **Commodore 64** in **1982**
and Have gotten ZORK 1, 2 & 3 to run on
Ubuntu 9.10 & 10.10

1) Go to: " [http://www.infocom-if.org/downloads/downloads.html]("http://www.infocom-if.org/downloads/downloads.html") "
2) Download the ".zip " of ZORK 1, 2 or 3 then unpack
3) I did right click the .DAT file, inside the DATA folder and mark as executable, but this may not be necessary?
4) System > Administration > Synaptic > **xzip** (synaptic will get and install file: "xzip_1.8.2-3_i386.deb" for you)
5) Go to the .DAT file, inside the DATA folder, inside of the ZORK version you want to play
6) Right click and open with other application,
7) use a custom command: xzip
8) Click Open

**West of House...**

ok... The **2**nd Time you Play ZORK
right click the .DAT file,
Chose open with xzip Now from in the list
Check the Box: "Remember this Application for "DAT document" files
Click Open

The **3**rd Time you Play ZORK
Just Double Lift Click the .DAT file, presto ! 

[SIZE="1"]To save a game, type "save" use Default
To load a game, type "restore" use Default
Default is and seems always will be:
/home/YourUserName/.infocom/ZORK1.sav
so if your thinking of Upgrading or Reinstalling the Operating System
be sure to copy this file out and save it some place like maybe:
/home/yourusername/Desktop/computer_game_save_files/ZORK1.sav
Later your backed-up file can be restored back in to:
/home/yourusername/.infocom/ZORK1.sav[/SIZE]

Be sure to Read the README.TXT and Visit some Links

[http://en.wikipedia.org/wiki/Zork]("http://en.wikipedia.org/wiki/Zork")

[http://www.infocom-if.org/authors/authors.html]("http://www.infocom-if.org/authors/authors.html")

[URL="http://www.gongkuo.com/linuxcli.htm"]Don't forget yer' Lantern
Ronok[/URL]

---

### Post by Bilderbikkel on 2010-11-20
I have ported the Zork C++ source code to a Qt Creator project: [http://richelbilderbeek.nl/GameZork.htm](http://richelbilderbeek.nl/GameZork.htm) . Compile it to play in a terminal. Have fun, Bilderbikkel

---

