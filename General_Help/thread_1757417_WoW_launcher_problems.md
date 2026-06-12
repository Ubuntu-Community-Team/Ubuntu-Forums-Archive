---
title: "WoW launcher problems"
date: 2011-05-13
forum: General Help
---

### Post by born2ryde1990 on 2011-05-13
Someone told me in an ealier post that wow runs good on Ubuntu. so i watched some videos and read some threads and tried but the results im getting arent what these videos are showing. When they open their wow the launcher pops up in the middle of the screen. When i try to launch it a seprate small blue screen pops up and the launcher is in there. then when i click play, i start getting errors from wine and nothing happens but the blue screen stays there.

anyone have a good video or written tutorial on how to make this work with Ubuntu 11.04?
im still a noob to linux, got the vista and xp mindset still.

---

### Post by tredegar on 2011-05-13
Most of us do not use linux as our OS to play games. We have better things to spend our time with.

If you want to play games, then please choose an OS that is "game orientated". That probably means windows. So use it for that, you already paid good money for it. If you want to do more interesting things with your PC, then by all means run linux, but please do not ask linux to play games built for the windows / mac platforms.

It's like asking a racehorse to drag a cart: It's not appropriate and it would not be animal-friendly (but it *might* just work, in case of an emergency). 

Please choose the right tool for the problem you need solving:

Games = windows
Everything else = linux

Best wishes.

---

### Post by jcd29 on 2011-05-13
> **tredegar said:**
> Most of us do not use linux as our OS to play games. We have better things to spend our time with.

Oh come on.

---

### Post by tredegar on 2011-05-13
> Oh come on.
OK.

But please try to contibute something useful to this forum.

Perhaps you can better explain to born2ryde1990 how to run games which are designed to run on windows / mac, on linux, to his satisfaction.

If you cannot provide _any_ advice, perhaps you should move on to the next post?

Best wishes.

---

### Post by clhsharky on 2011-05-13
born2ryde1990

> anyone have a good video or written tutorial on how to make this work with Ubuntu 11.04?

1- Wine has a sub-forum here
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

2- WOW has large thread here

Howto: WOW with Wine (help.ubuntu.com/community/WorldofWarcraft)
[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)
+ many more threads in wine sub-forum.

3- use PlayOnLinux to install WOW and configure, 
easer for noobs.Its in software center.

4- WineHQ  the developers and has a forum also + much more.
[http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBYQFjAA&url=http%3A%2F%2Fwww.winehq.org%2F&rct=j&q=wine%20hq&ei=JOTNTbPRAcfngQev5Zm6DA&usg=AFQjCNG_GieVLJmWMq2dtLWRMyBttJA2Xw&sig2=vR2d0xipw2_u322F6i-TKg&cad=rja](http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBYQFjAA&url=http%3A%2F%2Fwww.winehq.org%2F&rct=j&q=wine%20hq&ei=JOTNTbPRAcfngQev5Zm6DA&usg=AFQjCNG_GieVLJmWMq2dtLWRMyBttJA2Xw&sig2=vR2d0xipw2_u322F6i-TKg&cad=rja)


Sharky

---

### Post by -=- Mr. Tux -=- on 2011-07-05
wow runs fine under wine... ill link some some to here sry ta hear your having problems... and ubuntu can easily run games and for people like me who do many things on the computer it is better to be able to play some games on ubuntu  while i do more interesting things with my machine on the same system... ubuntu can pretty much do anything your windows can... takes some work...  but its a MORE powerful system there killer.

you said to contribute stuff to the forum so im pretty sure slamming on gamers in not doing so... 

ok so open your terminal and type

sudo apt-get update

let that run down

next type sudo apt-get install wine

let that run and finish it will ask for a bit of user input



type wine cfg

click the graphics tab

set to emulation

(very important  hardware slows it down)

audio tab

set to emulation

(full sound gets choppy)


then follow this link

[http://www.dedoimedo.com/games/wine-directx.html](http://www.dedoimedo.com/games/wine-directx.html)

finally to install after all this is done

insert the wow disc

goto terminal

type winecfg

goto drives

add

then navigate that menu 

>>>>>>>media
            >>>>>>> (should find your cd name here)


let that be a drive named z



then again terminal

type 

wine "Z:\(setup file name).exe"  <<<<< some help on file names and cd name would be great input ... i use a blizzard launcher so im not sure of the names.

but u should be able to figure that out.


lemme know how it works ill subscribe to this thread so i can help you quicker

---

