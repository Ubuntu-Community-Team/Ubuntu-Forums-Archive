---
title: "Macromedia Flash 8"
date: 2006-02-04
forum: General Help
---

### Post by Ben Stamper on 2006-02-04
I know this isn't gaming, but there aren't any other obvious places to post this. Would it be possible(Using Wine) to port over Flash and the rest of the Macromedia suite to Ubuntu? It's really the only reason I have Windows at this point. Thank you in advance!


*[size=1]Moved it - Artificial Intelligence*[/size]

---

### Post by mrlonely on 2006-02-05
there is a way to port macromedia studio mx to linux using crossover office but i am not sure whether flash 8 would run , pick up a trial and test it

---

### Post by stoffe on 2006-02-05
[http://appdb.winehq.org/appview.php?versionId=3673](http://appdb.winehq.org/appview.php?versionId=3673) - can't hurt to try?

---

### Post by Jammy4041 on 2007-11-25
[SIZE="5"]MACROMEDIA FLASH UBUNTU STYLE[/SIZE]

Today I have just installed Macromedia Flash 8.

First download the Flash 8 [here]("http://www.adobe.com/cfusion/tdrc/index.cfm?loc=en%5Fus&product=studio") (or Dreamweaver, Fireworks and Contribute).
Download the Windows version, (this is the version which I can get to work in WINE)

To do this, you will need a (free) Macromedia ID

Now the rest is assuming you have already a code, but you can still try Studio 8 for 30 days.

Now in a Terminal/Konsole put:

wine /BLAH

(where BLAH is the exe file. For Flash, this will probably be,  Flash8-en.exe.) 

I found that you have to put in the full path of the exe file: this will be probably easiest to burn the .exe files to a disc and install it from there.

In a terminal, if you have burned it to a disc, put in the disc in the drive and the path will be:

wine /media/cdrom0/BLAH

(where BLAH is again the exe file)

It should then install under wine.
Hopefully you should find your new file under Applications>Wine>Programs>Macromedia>Macromedia Flash.

I found out that I had to repair the installation of Flash, but if you encounter problems, feel free to post

A few pictures are attached of me running, in Ubuntu, studio 8:  


James

---

### Post by Jammy4041 on 2007-11-29
:( I can use Studio well but I cannot use Flash CS3 trial. does anybody know how to cure this?

Thanks

---

