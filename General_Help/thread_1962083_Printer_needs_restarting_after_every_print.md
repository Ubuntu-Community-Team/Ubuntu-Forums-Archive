---
title: "Printer needs restarting after every print"
date: 2012-04-20
forum: General Help
---

### Post by OliverHaslam on 2012-04-20
Hi guys,

I am trying to get a Kodak 3250 to work with Ubuntu, and to an extent, it does.

The problem I have is that after every print, I need to restart the printer or the next job simply sits as 'processing.' Restarting the printer and restarting the job makes it work.

Any ideas?

---

### Post by tmaranets on 2012-04-20
I have learned from my Ubuntu experiences with my Cannon MP620 printer that Ubuntu doesn't get along well with printers, Try printing off another OS.

---

### Post by OliverHaslam on 2012-04-20
> **tmaranets said:**
> I have learned from my Ubuntu experiences with my Cannon MP620 printer that Ubuntu doesn't get along well with printers, Try printing off another OS.

This is the problem. I've got a couple of Windows VMs I could try, but the XP one won't show up as a share anywhere even though it's set properly (as far as I can tell) and the Windows 7 VM just refuses to install it.

Apart from that, I've had a great day :D

---

### Post by agillator on 2012-04-20
My experience with Ubuntu and printers is primarily with HP printers and HPLIP where there seems to be no problem. However, does this happen with every program or with just one or two? How are you set up for printing - through CUPS or some other way? If CUPS or if you don't know, try opening your browser and going to localhost:631. Go through the maintenance and administrative menus, see if there is a hint there. Try printing a test page and see if it does the same. If so, you might try deleting the printer there and then reinstalling it there and see if that accomplishes anything. It sounds as if there is a glitch in the driver that is simply not telling the printer it is done. Taking the time to go through these exercises may well give enough information to figure out what the real problem is. Post the results of the above and it may ring a bell with someone.

---

### Post by OliverHaslam on 2012-04-20
> **agillator said:**
> My experience with Ubuntu and printers is primarily with HP printers and HPLIP where there seems to be no problem. However, does this happen with every program or with just one or two? How are you set up for printing - through CUPS or some other way? If CUPS or if you don't know, try opening your browser and going to localhost:631. Go through the maintenance and administrative menus, see if there is a hint there. Try printing a test page and see if it does the same. If so, you might try deleting the printer there and then reinstalling it there and see if that accomplishes anything. It sounds as if there is a glitch in the driver that is simply not telling the printer it is done. Taking the time to go through these exercises may well give enough information to figure out what the real problem is. Post the results of the above and it may ring a bell with someone.

Hi.

I'm using CUPS, yes. The problem happens no matter the source. Test pages will only print once, pages from Chrome etc are the same. Even printing over the network from a Mac has the same result.

A restart of the printer clears whatever the jam is.

---

### Post by agillator on 2012-04-20
This sounds more and more like a driver problem. My guess is that for some reason the code to tell the printer it is done is not being sent. I would suggest you check with Kodak customer support and see what they say. Also try googling your problem, sometimes that will lead you to the solution. Do you happen to have another printer of a different brand you can test and see if the same thing happens? If, in fact, you can borrow an HP printer, install HPLIP (a fairly easy process) and that one works, then it is probably a driver problem. In that case, your solution most likely lies with Kodak. 

Perhaps someone else with more experience with Kodak printers can help more.

---

### Post by paulnewall on 2012-04-22
Try installing the latest version of the driver c2esp24 which you get here
[http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)
You should use the version c2esp24
download the file c2esp24.tar.gz
extract it
then read the file install to get detailed installation instructions.

Or, if you want to try a slightly more automated installation:
download c2espinstaller.sh
change it's properties to make it executeable
then execute it by opening a terminal and typing ./c2espinstaller.sh

---

### Post by paulnewall on 2012-04-22
I forgot to say. There's no point in contacting kodak for support. c2esp is a cups filter / ppd file written by me because I had the same problem: I bought a kodak printer and found there were no linux drivers for it.

---

