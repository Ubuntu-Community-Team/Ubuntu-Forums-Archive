---
title: "Can't open the top folders under the places menu..."
date: 2010-10-21
forum: General Help
---

### Post by Vanillalite on 2010-10-21
I'm running 10.10 64 bit, and just starting today I found I can't open the folders under places. I can click on the computer icon and get that to open, but all the folders above that like home, desktop, music etc... won't open when I click on them.

Quite frankly nothing happens. I don't even get an error. It's as if I never clicked on any of them at all. I can click computer and navigate to my home folder and get to them that way, but it's annoying I can't just click places and then on my photos folder.

I swear this just started today (Oct. 21st) after I booted up post work and installed all the updates. Anyone else have this problem or know of a fix? :(

---

### Post by plucky on 2010-10-22
> **Vanillalite said:**
> I'm running 10.10 64 bit, and just starting today I found I can't open the folders under places. I can click on the computer icon and get that to open, but all the folders above that like home, desktop, music etc... won't open when I click on them.

Quite frankly nothing happens. I don't even get an error. It's as if I never clicked on any of them at all. I can click computer and navigate to my home folder and get to them that way, but it's annoying I can't just click places and then on my photos folder.

I swear this just started today (Oct. 21st) after I booted up post work and installed all the updates. Anyone else have this problem or know of a fix? :(

Open a terminal and type ```
nautilus
``` 

If that opens,then right click on any folder and select "Open with Other Application" and select "File Browser".

If Nautilus doesn't open post any errors shown in the terminal.

Good Luck

---

### Post by Vanillalite on 2010-10-25
Sorry I went on vacation over the weekend, but that fixed me issue! Mad thanks on that. Simple fix, but it totally worked!

---

### Post by ububooboo on 2010-10-25
I have a post about the same issue but no one answered it.  I am on my third install of 10.10 now because of that very issue.  I refused to let update manager upgrade my kernel to new version, or the headers or anything to do with the kernel, and so far my Places Menu has allowed me to access Home as should be.  I tried the nautilus thing, but it didn't work for me using my mouse.  I didn't get an option to open with when I right clicked.  So frustrating.  Going to put this post in Kate or something so I can find it if this happens for the third time.

---

### Post by joerow on 2010-12-01
> **plucky said:**
> Open a terminal and type ```
nautilus
``` 

If that opens,then right click on any folder and select "Open with Other Application" and select "File Browser".

If Nautilus doesn't open post any errors shown in the terminal.

Good Luck
Worked great for me thanks!

---

### Post by ecosseman on 2011-01-22
> **plucky said:**
> Open a terminal and type ```
nautilus
``` 

If that opens,then right click on any folder and select "Open with Other Application" and select "File Browser".

If Nautilus doesn't open post any errors shown in the terminal.

Good Luck

Running 10.10 64bit. Must have 'tweaked' something today.
Solved.
Thanks Plucky. Keep up the good work.

---

### Post by betterhands on 2011-04-24
this worked for me as well--thank you!

---

### Post by LNBN on 2011-05-26
I am on Toshiba Satellite L505D-GS6000  64bit 11.04 (natty) switched over to Ubuntu Classic desktop. I am running compiz, but this happened before compiz pretty sure. I noticed this about the same time I was first using wine. Had not turned any compiz settings on yet.

This is happening with the drop down menu  top tool bar..Applications/(''Places'')/System

 I opened up nautilus I did all the right click on the folders opened them with file browser. 

Nothing changed.. I even deleted the drop down places/menu folders and made new ones I right clicked on them as well etc. I cannot open up Home, Desktop, documents, Music ,Videos any of them. I create a new folder they do not work as well. This is folders I have the problem with.


If I go to My Computer I can open folders and get to everything. All the folders for conveniences so to speak (''places'') just do not open.  

Also do not know if this is related but when I click on the trash can icon to open it I get Movie Player. I can right click on the can and empty the trash tho. Ha Ha
 

I read about this for about a week now have not found anything that works yet. Or I just have not asked Google where to look yet lol.


So far been enjoying the new  distro my graphics and Audio are much improoved!  just not sure how to sort these to problems out. Thanks for any help:)

---

### Post by LNBN on 2011-06-09
Bump..:D

---

### Post by RodneyLee on 2012-01-21
nautilus: error while loading shared libraries: libunity.so.6: cannot open shared object file: No such file or directory

had installed Deepin Software center to try it out, did a couple minor update and now I cannot open folders from unity or nautilus

---

### Post by Krytarik on 2012-01-21
> **RodneyLee said:**
> nautilus: error while loading shared libraries: libunity.so.6: cannot open shared object file: No such file or directory

... did a couple minor update and now I cannot open folders from unity or nautilus
Try this:
```
sudo ln -s /usr/lib/libunity.so.9 /usr/lib/libunity.so.6
```
Regards.

---

### Post by stinkeye on 2012-02-06
Thanks Krytarik,
I was getting the same error when trying to run Brasero
and this fixed it.

---

### Post by philinux on 2012-02-06
Since this is an old thread that is solved for the OP and has drifted to other areas I'm closing it and marking it Solved.

Please start new threads for new problems.

---

