---
title: "Tovid, Devede, Qdvdauthor, DvdStyler frustrations!!!"
date: 2006-06-20
forum: General Help
---

### Post by PapaWiskas on 2006-06-20
I am not sure where to start or where I went wrong.

I have tried DVDStyler, Qdvdauthor, Tovid, Devede, etc.

All have had the same results.  The avi files get encoded into DVD
compliant mpg without a problem, the dvd structure gets created without
any issues... .ifo .bup .vob etc... So then I go to burn the disc
using K3b like I always do, in fact I even copied the files over
to a windows machine to test to see if it was a burning issue.

The DVDs wont play, they wont load the menu on a PC or stand alone
home DVD player.
I have researched my issue through wiki, and various software forums
with regards to each software I use, and I can not find a solution.

When I put the DVD in my linux laptop it gives me the standard 
encryption error, but yet I can open up the .vob files in Totem,
Xine, VLC, Mplayer just fine.

I really like Tovid, the command line interface is easy enough to use
since they implemented the todisc script.

I am at a loss, can anyone guide me in troubleshooting this issue?

Any help would be greatly appreciated.

---

### Post by PapaWiskas on 2006-06-20
Ok I did another test.

I created a DVD using 2 mpgs I created using the TOVID command line.  I transferred those files to a Windows PC that had Neros program on it that creates DVDs (menus, backgrounds, buttons, etc....).

I then copied the files back to my linux laptop and burned with K3B.  Took the DVD out and put it back into a Windows PC and it played fine, menu came up, I could select the episode I wanted by clicking the individual buttons etc....sooooooo....

I then take the DVD back to my Linux laptop, and totem opens up and it wont play due to the encryption error....so frustrated I then put a commercial DVD in my Linux laptop and it plays just fine!

I dont get it!!!!](*,) ](*,) ](*,)

---

### Post by PapaWiskas on 2006-06-20
polite bump

---

### Post by PapaWiskas on 2006-06-22
Well it appears that my problem might be with K3B or one of its dependencies?

I used Tovid to convert the .avi files to .mpg, use Nero Vision Express on a Windows machine to create the menus and convert to DVD format.  Burned the Disc and was able to play the movies on a standalone DVD player and windows PC, but my linux laptop will not play it.  I took the same files and burned them to disc with K3B and the disc would not play in a stand alone player or PC.

Could someone please help me understand what might be wrong?

Thank you.

---

### Post by PapaWiskas on 2006-06-23
bumping again

---

### Post by eth on 2006-06-23
have you tried building up the DVD structure with one of these programmes and then burn the DVD running Windows? It may be trial

---

### Post by PapaWiskas on 2006-06-23
Yes, I have done that as well and they did not work.

The only way I can get things to work now is to use Tovid to encode the .avi to .mpg then use a Windows machine that has Nero Vision Express and create my DVD menu, layout, burn etc.  Then the movie will play on my stand alone home DVD player.

I am truly at a loss as to how to further trouble shoot this, I never had this problem before on Breezy.  And when I switched to Dapper I never had a problem but it seems that since I have done some of the Ubuntu system upgrades something has changed and I am not sure what.  I ususally just install whatever the update notifier tells me to.

---

### Post by joshrobinson on 2006-06-23
use tovid to encode, then use makexml to create the xml file(sometimes tovid does it for you sometimes it fails due to filenames), then makedvd mydisc.xml

then makedvd -burn mydisc

works every time for me.. dont use k3b to burn it.. let all the tovid apps do the work

make sure you have all the needed dependencies or this wont work


and devede gives bad audio sync for me.. tovid works perfect

---

### Post by PapaWiskas on 2006-06-23
I will try that, the only thing that irks me about burning with Tovid is it burns at 1x and I have no idea how to bump that up to at least 4x which is my normal burn speed.

(edit = I am doing this now as I speak and it appears that the command line version of Tovid IS indeed burning at 4x, however the Tovid GUI, which is what I used before, only burned at 1x)

---

### Post by joshrobinson on 2006-06-23
[QUOTE=PapaWiskas]I will try that, the only thing that irks me about burning with Tovid is it burns at 1x and I have no idea how to bump that up to at least 4x which is my normal burn speed.

(edit = I am doing this now as I speak and it appears that the command line version of Tovid IS indeed burning at 4x, however the Tovid GUI, which is what I used before, only burned at 1x)[/QUOTE]

i always burn from a terminal, not actually in tovid.. hope it works for you

---

### Post by PapaWiskas on 2006-06-26
This worked without a hitch, THANK YOU so much!

K3B appears to be working again as well, not sure what the problem was, maybe the last upgrades I did fixed something?

---

### Post by brennydoogles on 2007-06-17
> **joshrobinson said:**
> use tovid to encode, then use makexml to create the xml file(sometimes tovid does it for you sometimes it fails due to filenames), then makedvd mydisc.xml

then makedvd -burn mydisc

works every time for me.. dont use k3b to burn it.. let all the tovid apps do the work

make sure you have all the needed dependencies or this wont work


and devede gives bad audio sync for me.. tovid works perfect

Are these all Tovid tools?? I have been having alot of trouble making a DVD of my favorite show, so this might help!

---

