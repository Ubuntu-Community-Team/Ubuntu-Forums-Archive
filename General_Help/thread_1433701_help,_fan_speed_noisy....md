---
title: "help, fan speed noisy..."
date: 2010-03-19
forum: General Help
---

### Post by noveevon on 2010-03-19
ah what a mess, ive got a problem with a really noisy fan going at 63% and driving me crazy...

i did use the ati catalyst drivers for a while, but it messes up my system everytime and this is the second reinstall ive had to do due to the problems i get see this thread: [http://kubuntuforums.net/forums/inde...opic=3110567.0]("http://kubuntuforums.net/forums/index.php?topic=3110567.0")

i found the solution or atleast i think i did here: 
[http://ubuntuforums.org/showthread.php?t=1313828](http://ubuntuforums.org/showthread.php?t=1313828)


but now i am unable to control the fan as that requires the fglrx drivers which gave me the problem in the first place....

so, if anyone knows how to control the drivers using another method then ati catalyst based scripts i would really be happy and would probably do a victory little dance in my living room...


i am using kubuntu 9.10 and have a HD 4850 card with a psycho fan...and my motherbord is asus p45q pro and has no options for gpu fan control..

---

### Post by no2498 on 2010-03-19
this worked for me on a dell 6400 desk top 910 karmic
open a terminal type gstreamer-properties click enter
click video set the plug in to, x window system (no xv)
write down what its set to first so you can set it back if this does not work for you

you do need to restart the computer
you can see what is making it do this
if you install htop or top they tell you how to install in the terminal

hope this works for you

---

### Post by noveevon on 2010-03-19
> **no2498 said:**
> this worked for me on a dell 6400 desk top 910 karmic
open a terminal type gstreamer-properties click enter
click video set the plug in to, x window system (no xv)
write down what its set to first so you can set it back if this does not work for you

you do need to restart the computer
you can see what is making it do this
if you install htop or top they tell you how to install in the terminal

hope this works for you

thanx for the reply...i have however reinstalled and gone with the proprietary ati driver, as now i got to turn my fan speed to 25% which isnt that loud, although i will probably end up buying a new fan for my GPU as its still noisy..

it seems that the gestreamer program is for Gnome, i will check it out tomorrow...

also, now my system does not give me the option of multiple screens, and it seem stable...but i do need multiple screens.....so i will try and work on it tomorrow...

---

### Post by no2498 on 2010-03-19
from what ive been reading you need to let the fan run at what its running at an get the temp down first
gstreamer-properties is what they/ubuntu test the webcams with so should work on all distos

---

### Post by linden940 on 2010-03-19
first thing first....clean your fan out....

and or ....buy a computer fan thats not loud...how old is this fan?

---

### Post by noveevon on 2010-03-20
> **linden940 said:**
> first thing first....clean your fan out....

and or ....buy a computer fan thats not loud...how old is this fan?


the fan is default Asus fan that cae with the 4850 graphicscard...there is no need to clean it as ive checked and also its not so loud in 25% where its running now...still loud but i can live with that...the problem is how can i control it, without using fglrx? as that is what i am using now...also its a new card only a few months old...

i might buy a zalman fan if i dont get a solution to this, but thats money and i was hoping for a free solution...

anyways, thanx for the reply..

---

