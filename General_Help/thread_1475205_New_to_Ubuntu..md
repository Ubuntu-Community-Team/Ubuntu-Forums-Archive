---
title: "New to Ubuntu."
date: 2010-05-06
forum: General Help
---

### Post by ChrisBradford on 2010-05-06
Hello everyone. well a little back story. ive been a windows user sense i was around computers. more than 8 years. ive always had problems. ever sense the start. i wont lie i torrent things and i normally get my windows to the point of blue screening every 4 months. even tho i used registry cleaners. and good anti virus software and firewalls ( NOD32 )

i really started getting into gaming and i went through a few GPUs from ATI due to their ATI 5xxx cards not working with windows vista/7 correctly. tho they worked on xp fine. sense then i built a new rig ( in my sig on the forums is the specs ) and i had windows xp installed. everything was working great until a few days ago. ugh i installed halo 1 to just play around with before the halo reach beta came out. and i guess it was corrupted. because i started getting random restarts. blue screens and other problems. 

i did some research about ubuntu before and other linux OS. but i was always let down by the poor support for gaming. but with my frustration with windows peaking i found all my windows disks and destroyed them. and downloaded ubuntu 10.04 and installed it. 

after doing some homework i found that playing games on ubuntu is alot more supported than i thought. i read the Steam is going to soon support linux. for the moment ive installed WINE. and installed the windows version of steam. i will downloading a game tonight to test it out.

- - QUESTIONS - -
i moved my music over from my external HD to PC HD. the mp3 files worked fine. and the itunes files worked also after rhythimbox told me to download a plugin but it cant find a plugin to play my windows songs. it needs Windows media decoder plugin does anyone know where i can find that?


i do like the pre installed themes that came on ubuntu but is their a ( safe ) place i can easily find new themes to install? i remember messing around with new themes on windows and it always seemed to damage the .dll files =\

also does anyone recommend any cool programs they seem to cant live without on linux? 

thanks for reading. awaiting replies. loving being in the ubuntu world =)

---

### Post by UCSBGauchosRock on 2010-05-06
Welcome to Ubuntu! It is nice to hear that your experience is enjoyable :)

Going back to your questions....

Question: "i moved my music over from my external HD to PC HD. the mp3 files worked  fine. and the itunes files worked also after rhythimbox told me to  download a plugin but it cant find a plugin to play my windows songs. it  needs Windows media decoder plugin does anyone know where i can find  that?"

Answer: Open Terminal--> Type in "sudo apt-get install ubuntu-restricted-extras" without quotations
--> Try playing media again or if it doesn't work, restart your computer and try again... If the problem persists feel free to ask me again but it should be solved.

Question: i do like the pre installed themes that came on ubuntu but is their a (  safe ) place i can easily find new themes to install? i remember messing  around with new themes on windows and it always seemed to damage the  .dll files =\

Answer: [www.gnome-look.org](www.gnome-look.org) is probably the best ubuntu themed website out there.

Question:  also does anyone recommend any cool programs they seem to cant live  without on linux?

Answer: 1. GIMP- Photoshop-like image editor
              2. Adobe Flash Player- just about any website uses this nowadays

If you want more.... Open up Ubuntu Software Center and examine the thousands of free programs available from there :)

Hope you have a pleasant Ubuntu experience 

Cheers

---

### Post by finlost on 2010-05-06
> **ChrisBradford said:**
> 
also does anyone recommend any cool programs they seem to cant live without on linux? 

There is a thread somewhere about the top 10 apps you need/use.  I cannot remember where it is though.

I like:
Ubuntu Tweak
OGMRip
Gwibber (very buggy and needs more functionality to filter)
DropBox
Ubuntu One
GMNotify
Cairo Dock
CompizConfig Settings Manager
Gnome Color Chooser
Samba

I reference these sites quite often to tweak and pimp my distros:
[Make Tech Easier]("http://maketecheasier.com/category/linux-tips")
[OMG Ubuntu]("http://www.omgubuntu.co.uk/")
[YouTube Channel]("http://www.youtube.com/user/gotbletu")

---

### Post by Bradj47 on 2010-05-06
> **ChrisBradford said:**
> 
i do like the pre installed themes that came on ubuntu but is their a ( safe ) place i can easily find new themes to install? i remember messing around with new themes on windows and it always seemed to damage the .dll files =\

[http://gnome-look.org/](http://gnome-look.org/)

> **ChrisBradford said:**
> 
also does anyone recommend any cool programs they seem to cant live without on linux? 

The Ubuntu Software Center makes it really easy to browse software. Go through there and try out stuff that seems to interest you.

---

### Post by Tamalin on 2010-05-06
Well, lets see:
what format are your "windows files"?
I have never had a problem playing any codec, so I am interested to see what is not working for you.  You may also be able to use an online converter to convert those files to mp3 or something if you can't find a suitable plugin...

---

### Post by sandyd on 2010-05-06
> **ChrisBradford said:**
> Hello everyone. well a little back story. ive been a windows user sense i was around computers. more than 8 years. ive always had problems. ever sense the start. i wont lie i torrent things and i normally get my windows to the point of blue screening every 4 months. even tho i used registry cleaners. and good anti virus software and firewalls ( NOD32 )

i really started getting into gaming and i went through a few GPUs from ATI due to their ATI 5xxx cards not working with windows vista/7 correctly. tho they worked on xp fine. sense then i built a new rig ( in my sig on the forums is the specs ) and i had windows xp installed. everything was working great until a few days ago. ugh i installed halo 1 to just play around with before the halo reach beta came out. and i guess it was corrupted. because i started getting random restarts. blue screens and other problems. 

i did some research about ubuntu before and other linux OS. but i was always let down by the poor support for gaming. but with my frustration with windows peaking i found all my windows disks and destroyed them. and downloaded ubuntu 10.04 and installed it. 

after doing some homework i found that playing games on ubuntu is alot more supported than i thought. i read the Steam is going to soon support linux. for the moment ive installed WINE. and installed the windows version of steam. i will downloading a game tonight to test it out.

- - QUESTIONS - -
i moved my music over from my external HD to PC HD. the mp3 files worked fine. and the itunes files worked also after rhythimbox told me to download a plugin but it cant find a plugin to play my windows songs. it needs Windows media decoder plugin does anyone know where i can find that?
[B]```


```[/B]```
[B]sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
[/B]
```[B]
if you installed 32bit ubuntu
```

sudo apt-get install w32codecs
```if 64bit ubuntu
```

sudo apt-get install w64codecs
```and if your worried about wether its illigal or not, [http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/](http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/)

[/B] 

i do like the pre installed themes that came on ubuntu but is their a ( safe ) place i can easily find new themes to install? i remember messing around with new themes on windows and it always seemed to damage the .dll files =\
**gnome-look.org**

also does anyone recommend any cool programs they seem to cant live without on linux? 

thanks for reading. awaiting replies. loving being in the ubuntu world =).

oh, and you also might want to go to System -> Administration -> Hardware drivers
and activate the dirvers for your video card if you haven't done so already ;)

---

