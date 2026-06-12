---
title: "when will xorg finally properly display any of my computers...?"
date: 2010-10-07
forum: General Help
---

### Post by PARO on 2010-10-07
[begin rant]
i've finally given up playing with xorg.. i've been with ubuntu since dapper, and wasted countless hours configuring ubuntu to properly display on 3 different computers. the old xorg configuration used to at least provide a functional xorg.conf to work with, but in lucid all i get is a bunch of gibber jabber (as Mr. T would say). why does my mouse need to load dri and xgl modules? this is just a mess.. the nouveau drivers don't display properly on 2 of the 3 computers and leaves all kinds of artifacts, nvidia drivers dont display proper resolutions on monitors that nv and nouveau do, and leaves artifacts at boot and shutdown, and nv doesn't display proper resolutions on 2 of the 3, and previous xorg.conf files that i've saved sometimes work with upgrades, and sometimes don't.. 
[end rant]

Anyway, i give up, it's too much pain and wasted time, so i'm wondering if i overlooked a program or something that can actually properly create a new xorg.conf that will work with the newest ubuntu, or if any other linux distro can configure displays better then ubuntu..i've heard suze is much more friendly for nvidia users (can anyone confirm?) and i know puppy linux has an excellent configuration wizard for this that's worked on all 3 computers.. but puppy isn't what im looking for as a main os. will ubuntu EVER start providing reliable tools for this, rather than assuming that people arnt having problems because many of those that are simply go back to windows...?

---

### Post by PRC09 on 2010-10-07
What kind of computers? Desktop or laptop,netbook.What are the specs for each machine.What video cards are you using???? I have done quite a few installs on a good variety of machines and have yet to have to mess with xorg or much of anything actually just the usual wireless set-ups....

---

### Post by PARO on 2010-10-08
one of the three is old and i really don't care to mess with it, and i'm not really sure what the video card on there is, but the other 2 get used every day. 

1. is my compaq presario desktop with an nvidia 4000mx card. out of the box (by default after installation of lucid/nouveau driver) it would not show the mouse cursor. after installing proprietary nvidia drivers all is good except for boot up screen is in low resolution and displays artifacts, flickers, and occasionally hangs (known bug). nv driver requires custom xorg.conf to properly display, but then works perfectly (minus the 3d accel). when connected to my hdtv i cant get higher than 600x800 resolution with nvidia driver, but the nv driver changing resolution works fine.
   
2. dell dimension 8100 with nvidia TNT Riva card. out of the box (with nouveau) windows, menus, panels etc. lag. i believe this is because of it's attempt to support 3d acceleration (this is how it looks with the nvidia drivers also, and always has been this way which is why i use nv instead) but custom xorg to eliminate xgl loading and option falsing hwcursor and acceleration did not help. so i decide to use the nv driver (as in the past), but i cant get resolutions above 600x800, and i tried all the old tricks to fix this (actually i tried copy and pasting my old working xorg.conf first since that's what i was using before the upgrade, but it doesn't work now...). nothing has worked...

[the headache begins...]
btw i'm not looking for a fix, but a solution.. something that will allow things to work now and in the future, or a distro that will do this work for me properly.. i've spent the last 4+ years manually fixing my xorg.conf for every new release (that didn't allow me to use my old one, or when i had to change for new screen/hardware/software/personal desires etc... a artifact free display that can change resolutions such a simple request...)

---

### Post by PRC09 on 2010-10-08
I know this may not be the only solution or a solution you wish to pursue but if these problems have continued thru the last few releases  then maybe the answer is new hardware or different hardware... and not waiting for the software to change and suddenly make it all just work.Chances are if it doesnt work now after 4 years then it probably never will....

Dell Demension 8100 - Originally designed for Win Me so that is getting pretty old.Also the Nvidia GeForce4  MX4000 card from what I have read (2006) never worked correctly in Vista either so maybe it was just not a very good card to start.......Just my thoughts....

---

### Post by NoNameWill on 2010-10-08
Have you tried this way to install nvidia drivers. I did and have not had a problem with nvidia.

[http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx](http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx)

---

### Post by corcomp84 on 2010-10-08
Let me ask what you might think is a dumb question, but I have to ask,, do they all have the same monitors?  I had a couple of dell dimension desktops that I have installed Ubuntu on many many times with no problems, but this one time I installed it on my brothers and nothing but problems almost the exact same as your having.. I tried everything until I said well maybe its the monitor. it was a perfect square gateway monitor and sure as sh@# that was the problem.. The monitor wasn't telling the computer what it could use for a resolution.. but it would tell Windows  it was a duel boot system.. I never did fully figure it out but its at-least a direction.. I even installed different video cards trying to solve the problem with no luck.. I installed three different distro's of Ubuntu and upgrades still nothing.

---

### Post by corcomp84 on 2010-10-09
one more question, are you upgrading over the internet with the update manager or doing a clean install? Because if you have been doing the upgrade through the update manager then thats a very good chance thats your problem..  get 10.04 because its a long term release and do a clean install from scratch..

---

### Post by PARO on 2010-10-09
no, 3 different monitors plus one hd tv, and i always do clean installs. but i think you're on to something. i've tested suze and debian, and they seem to have the same issues (except their base xorg.conf created arn't strange like ubuntu's is for me). but yea, i'm thinking it's a monitor issue, ubuntu sees it as crt-c(?) but it gives proper resolution in puppy when i select lcd from their xorg configuration wizard. i've heard suze also has a way to configure your monitor like that, but i didn't test it because i didnt know when i first tested it. maybe it's doing the same with my hd tv? but why would nv see my monitor properly when it's my tv and nvidia driver not, or nouveau see my monitor resolutions properly but nv not if it's xorg thats responsible for that? but if that fixes my problem i'm happy.. so is there anyway to setup a monitor like in the puppy xorg wizard in ubuntu? my search is coming up nill.

my geforce 4000mx actually works pretty well, outside of the cosmetic issues and resolution on my hdtv, day to day computing is not a big deal. it does all the fancy compiz fusion stuff and acceleration works well, i can watch hd video and play video games and all that, so no need to upgrade yet.   

the dimension 8100 is old, and the tnt riva card is worthless today, i actually did buy a new card, but had to return it because only unusually large videocards will fit. it's got this strange hammer thing to keep the card in place rather then the little snaps.. and modern cards wont reach it.. so i'm stuck with it, unless i can jerry-rig something, but then i'm afraid of breaking it...

and yes i can install and get the nvidia drivers working on my dimension 8100, but then i get the window lag.

---

### Post by PARO on 2010-10-09
Problem Solved! I don't know why it took me so long to think of this, but since i know puppy linux properly can set up my display with the nv driver, and unfortunately i see no app in ubuntu to do this, why not just boot into puppy, have it set up my xorg.conf and copy it into my ubuntu :D.. worked perfectly. if only ubuntu had a simple little app like that (or would port puppy's), it would save some people so much time and frustration..

---

