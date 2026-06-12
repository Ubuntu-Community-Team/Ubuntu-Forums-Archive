---
title: "downverter link persist in unity after being uninstalled help please"
date: 2012-09-24
forum: General Help
---

### Post by VideoRustler on 2012-09-24
I have a sony vaio laptop with 12.04 installed.The other day I downloaded a program called Downverter, but didn't like it so I uninstalled it...now theres an icon in the dash home that won't go away.I have rebooted several times to no avail..Could use some help please, and thank you.

---

### Post by jerrrys on 2012-09-24
One way is to open up nautilus and do a search for Downverter and remove any leftover files.  You probably need root access to do this.  So [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

gksudo nautilus

And in the future you may want to use the [purge command]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=purge+command&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F") :)

---

### Post by VideoRustler on 2012-09-25
Thank you so much it worked.Sorry I didn't respond sooner but I don't have internet at home so had to wait till I got back to work to see your reply.

P.S.: I just started using Ubuntu regularly this month even though I have had it installed for some time.I have a dual boot system...Windows Vista (ugh...) and Ubuntu 12.04.I must say I wish I had started sooner.

---

### Post by jerrrys on 2012-09-25
No problem, glad you got it sorted out.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forum :)

---

### Post by fra2rizla on 2013-09-08
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]helloguys, I am a new happy ubuntu user after 15 years or so on windows..I kind of have the same problem but I don&#8217;t want to uninistalldownverter because its just the software I was looking for ( othersdont let you choose the quality of the file you are downloading). Iwas just thinking of uninstalling downverter  because it doesn&#8217;tstart and couldn&#8217;t find anyone else with the same problem. [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Ihave a dell inspiron 6400 laptop, 32 bit, 2gb ram, cpu intel T21301.86 GHZ x 2, and I have installed ubuntu 12.04, kernel linux3.8.0-30-generic, gnome 3.4.2.[/FONT][/COLOR]

[COLOR=#222222] [/COLOR][COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Itworks beautifully and so far no problem, but I have installeddownverter  and I see it in dash  but when I click on itnothing happens. I tried to unistall and install back, restartlaptop, get the deb file from different source but this problem isstill there. So the weird things are this: [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]1)when I click on it on the dash, the software doesn&#8217;t start.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]2)I tried to uninstall it and realised that I can only do it fromterminal ( sudo apt-get remove downverter ), if I open it in softwarecenter, the software centre allows me to reinstall it but not touninstall it (and I can open it in software center just clicking onthe deb file I downloaded and not looking through the installedsoftware) [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]3)even after having installed downverter from terminal ( sudo apt-getremove downverter and then, just to make sure everything is cleanedup sudo apt-get autoremove and sudo apt-get update I still see thesoftware link on the dash[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]whatshall I check? please specify step by step, I am quite new to dothings in the terminal.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]OR can any of you suggest another graphic video dowanloader software that lets you chose not only the output format filebut also the quality of the file you are downloading ( I mean 1080 por 720 p, or 480 p), I tried all video downloader but this one justlet me chose the output file but not the quality of the download andit doesn&#8217;t chose automatically the best quality. I know you can doit with the terminal, but being new to ubuntu I prefer to have agraphic version software. Also I know there are plug in for firefoxbut I use chrome ( not chormium and apparently all the plug in forchorme have been removed from the chorme web store and the browserdoesn&#8217;t allow me to install extension that are not in their webstore) Thank you so much.[/FONT][/COLOR]

---

### Post by fra2rizla on 2013-09-08
I wrote here because I dont know how to open a new thread.. :-(

---

### Post by fra2rizla on 2013-09-08
I found ClipGrap and it works. Probably the .deb package for 32 bit is corrupted because there's a missing file. (/opt/downverter/downverter )

---

