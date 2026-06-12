---
title: "vlc agony"
date: 2011-01-04
forum: General Help
---

### Post by flipper T on 2011-01-04
if i go to places / home, vlc auto boots and begins playing run dmc.

if i go to places / videos, vlc auto boots and begins playing shaun of the dead.

this is annoying.

problem only just started to occur. reboot has not resolved.

please help.

---

### Post by Rasa1111 on 2011-01-04
Should be a simple enough fix~

Go to your **"Places"** menu, and open up "Computer"
Go into your** "file system**" , find the **"Home**" folder, 
and right click it,
 then choose "Open with other application". 

When the list of applications comes up, 
Scroll down to **"Open Folder",** Select it, 
and at the bottom of the window,  you'll see a check box, that says** "remember this application for file folders".**
(make sure it's checked)

 Then simply click the "open" button at the bottom right,
and now whenever you open a folder..
 it should open correctly. 

Hope it helps.

---

### Post by MechaMechanism on 2011-01-04
EDIT: Nevermind.  Rasa1111 has the right answer.

Can you describe more clearly whats happening.  Do you mean that when you open the file manager that VLC starts up and begins playing music?  Have you tried to shutdown VLC.  What about uninstalling VLC and then seeing what happens.

---

### Post by flipper T on 2011-01-04
thank you very much.

worked as described.

any idea how the problem arose in the first place so i can avoid in future ?

i will mark as solved.

---

### Post by flipper T on 2011-01-04
hi mecha,

yes exactly as described.

whenever i selected any item from the places menu, vlc would start up and attempt to open the first file in that place

eg music....first mp3 would start playing in vlc

videos...first video,

posted solution worked, but cause unknown to me

---

### Post by flipper T on 2011-01-04
ps uninstalling vlc did also resolve, however problem returned as soon as i reinstalled it

---

### Post by Rasa1111 on 2011-01-04
> **flipper T said:**
> thank you very much.

worked as described.

any idea how the problem arose in the first place so i can avoid in future ?

i will mark as solved.


 Most welcome. 
Glad it helped. 

I really am not sure what causes it.
 But I think the majority rules that it is just a bug of some kind. 

It has happened to me twice, both times being months and months apart. 
and I cannot pinpoint what makes it happen. 

But yourself, myself..
and a handful of others here have also experienced this. 

 Sorry I couldnt be more insightful.  lol

---

### Post by flipper T on 2011-01-04
i forgive you :)

thx again

---

### Post by mc4man on 2011-01-04
It is caused simply from the 'Remember this...' option that is available whenever using the 'open with - other application' menu.

If enabled, (which it is by default), whatever app chosen will become the new default. 
This occurs on both files and folders, affects maverick and in some installs also lucid.

---

### Post by flipper T on 2011-01-04
thx mc4man

i had assumed that that option effected only the selected folder / file.

i do now recall setting this option for 1 saved movie.....doh!

is it possible to specify different preferred apps for different files / folders ?

---

### Post by mc4man on 2011-01-04
> is it possible to specify different preferred apps for different files / folders ?

folders - no, all folders (directories) are treated the same and the default should, as you've seen, be left with your file manager (nautilus usually.
for files you can set defaults per mimetype, either by leaving the box enabled from the other application menu or by r. click > properties > open with on one example of a particular type

When ever using the _other applicatio_n menu keep in mind that if you don't disable the option the default will be changed

---

### Post by flipper T on 2011-01-04
thx again & happy new year

---

### Post by garvinrick4 on 2011-01-04
There are times when you open a directory to play media
and the directory has both text files and music and or video files in sub-directories
so right click and open with vlc will set both types of directories to be opened in vlc.
So open directory to media sub-directory or open vlc and follow path to media and all
will be well.

---

### Post by mc4man on 2011-01-04
> open with vlc will set both types of directories 

The open with menu sets nothing, it simply does what's expected, open the file or folder in the app chosen

The aren't "types" of folders, a folder is a folder and can have only one default.
(you can have numerous choices in the open with menu, but only one default for all folders

---

### Post by BikeRich on 2011-01-06
RASA111 :

Thank you very much !  Even did a re-install of Maverick 10.10 , to no avail.

Thanks for the clear and simple fix.

                                                                BikeRich

---

### Post by carboniferous on 2011-03-21
THX a lot, had that problem for over three months, now i finally got rid of it!!!
:p

---

### Post by bnleez on 2011-08-19
It does...thanks!!

---

### Post by jamstir on 2012-02-02
Hi there,, i seem to have a problem with my home folder, it try,s to load after it opens then stops, i have to force quit.

I took a reading to see whats in there and got..  57,510 items, totalling 7.5 GB

Which i thought...  :popcorn:.. lol

I can understand why its not loading. anyone help please?

---

### Post by jamstir on 2012-02-02
NAUTILUS PROBLEM?

other alternative is trying Nautilus Elementary, a nice replacement  for nautilus, maybe it don't fall in the same problem, but I can't  promise you that.
  If the problem is on nautilus you can install nautilus elementary using the PPA @ ppa:am-monkeyd/nautilus-elementary-ppa
  to install it throw the ppa, use these commands:
  sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa sudo apt-get update && sudo apt-get upgrade


Seems to work great for me, at least now i can open home folder.:D

---

