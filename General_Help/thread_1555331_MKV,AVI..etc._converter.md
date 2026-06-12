---
title: "MKV,AVI..etc. converter"
date: 2010-08-17
forum: General Help
---

### Post by savafan on 2010-08-17
Something cool that I use a lot on my other system is ConvertX. This is a very easy program to use that converts almost any computer file to DVD format that can then be burned to a DVD that can play in any home system DVD player.

I know this can be done with Ubuntu, but it seems very complicated to do.

I'm hoping that someone can come up with a program that is as easy to use.

---

### Post by balaknair on 2010-08-18
Try DeVeDe(available in Ubuntu Software Centre)

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by kmccmk9 on 2010-08-18
> **savafan said:**
> Something cool that I use a lot on my other system is ConvertX. This is a very easy program to use that converts almost any computer file to DVD format that can then be burned to a DVD that can play in any home system DVD player.

I know this can be done with Ubuntu, but it seems very complicated to do.

I'm hoping that someone can come up with a program that is as easy to use.

Well I use Brasero Disc Burner. Also if it doesn't read the file you have then you can try to use ffmpeg terminal commands to convert it. If that doesn't appeal you could try searching the software center for a gui front end of ffmpeg like WinFF

---

### Post by savafan on 2010-08-18
I've experimented both with WinFF & DeVeDe & for some reason cannot figure them out...I'll keep trying but if anyone can help further, it would be appreciated

---

### Post by bodhi.zazen on 2010-08-18
Personally I use ffmpeg

It is command line and it does take a bit of reading to understand.

[http://linuxers.org/tutorial/ffmpeg-basics-beginners](http://linuxers.org/tutorial/ffmpeg-basics-beginners)

Another popular option is handbrake.

[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by nixonjust on 2010-10-29
Hi guys my 1st post,

DeVeDe is easy to use once you get the hang of it and pretty good, but i've found Arista Transcoder very good as well.

Again once you get he hang of it Arista proves to be a very capable video transcoder. And has presets for all mobile devices. You just need to define the "input" field or directory and then add to queue where you want it to save the file to.

Cheers team, hope you enjoy ubuntu as much as i do.

---

### Post by abdusamed on 2010-10-29
I was having similar problem and never found any good alternate to CONVERTXDVD.. I run it now on wine and runs perfectly fine.

---

### Post by rigger71 on 2010-12-29
hi guys brand new to ubuntu and loving it,again ive the same prob ive been using convertx on xvid avi ect but tryed to download devede but everytime i try and install it keeps saying theres no file???
anyone else experienced this??
thanks in advance rigger.

---

### Post by gordintoronto on 2010-12-30
> **rigger71 said:**
> hi guys brand new to ubuntu and loving it,again ive the same prob ive been using convertx on xvid avi ect but tryed to download devede but everytime i try and install it keeps saying theres no file???
anyone else experienced this??
thanks in advance rigger.

Use System/Administration/Synaptic Package Manager to install Devede. (Also use it to install any other program, if possible, except Virtualbox.)

---

### Post by gordintoronto on 2010-12-30
> **savafan said:**
> I've experimented both with WinFF & DeVeDe & for some reason cannot figure them out...I'll keep trying but if anyone can help further, it would be appreciated

Open up the help file for Devede, and spend 20 minutes reading, and perhaps making notes. Once you know how to work it, you'll love it.

---

### Post by rigger71 on 2010-12-30
thanks for that mate,ive just been tryin to burn with brasero??
but to no avail.every time i try and burn it just goes of screen and thats it no message sayin anything is wrong ect...??mmmm.
ill try what you suggest then feedback later,thanks again
rigger.

---

### Post by rigger71 on 2010-12-30
hi there opened the synaptic package ect.. but ive no idea how to use it ,i tryed to search for the devede install i did earlier,it told me a later version was installed but....its not showing in the installed software list??im stumped may try and get somat else!!
thanks rigger.

---

### Post by rigger71 on 2010-12-30
well not to be beaten at such an early stage lol,i went back in and ive sorted it!!!yep its quite easy when it cliks together!!??
thanks again dvd converting as i type!
rigger

---

### Post by rigger71 on 2010-12-30
ok so now im more confused??!!
it asked me what i wanted dvd/cd so i picked dvd everything ok??
no now after 2hours 20 mins (convertx takes bout 25 mins)im left with a 3.6 gig iso???????
dont know what to do now plz help
rigger.

---

### Post by perspectoff on 2010-12-30
Jeez, how old is your DVD player?

Mine plays AVIs, WMV, MPGs straight from a Data DVD, with folder navigation straight from the DVD player.

Of course, the DVD player uses embedded Linux, so it is more powerful than most older DVD players or those that don't use embedded Linux...

My HDTV uses embedded Linux, too...

Having said all that, I make DVDs (from MPGs, FLVs, etc) using QDVDAuthor, which allows me to use menus, etc. It converts into the VOB format used by most commercial DVD players.

As with anything, of course, you have to RTFM.

---

### Post by rigger71 on 2010-12-30
my dvd is quite capable of playing xvids ect but the point is i like to convert to dvd to burn as it clears up often dark/poor quality downloads.plus i like to play dvd in different  consoles such as 360 ect..
also as you mention i can add menus titles ect..
and when all said and done i should be able to do this regardless of the age of my dvd player lol.
rigger.

---

### Post by Mindswap1 on 2010-12-30
There are two awesome converters for Ubuntu, that I have used. The first being Arista Transcoder. And the other one is Transmageddon both can be found in the software center.

---

### Post by rigger71 on 2010-12-30
ok cheers ill give those a try,just to add,ive installed ubuntu 2 days ago and already finding a few probs brasero now wont open????
every other app round it does??
cant open it for love nor money,starts to boot up says opening/starting then just goes away??!!
oh dear.
rigger.

---

### Post by gordintoronto on 2010-12-30
There is a problem with your system if Brasero does that. I don't think you have mentioned what version of Ubuntu you have installed, or how it's installed. (Wubi, dual boot, etc.)

You could use Synaptic to install K3B. If you insert a blank DVD, a few seconds later a window pops up. Click cancel! Try starting Brasero, if it runs, select "burn ISO." If it doesn't run, try K3B, select "More actions," (near the bottom of the window) "burn image."

---

