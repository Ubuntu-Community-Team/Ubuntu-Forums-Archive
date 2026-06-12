---
title: "Vlc/Mplayer not working properly due to latest updates"
date: 2009-09-03
forum: General Help
---

### Post by Struki on 2009-09-03
OK to cut it short my vlc/mplayer don't display vido for any avi files.
Anyway i got this regular updates with the update manager last night, i installed them and today i cant run any kind of video(i got audio fine).

I got all restricted extras, and medibunti upgrades, latest ati drivers, only thing that changed since last night was my regular update, so where could be the problem.

So i poked around a little bit, and found what packages I got last night, and i think these are the bad guys:

[I]libgl1-mesa-dri (7.4-0ubuntu3.1) to 7.4-0ubuntu3.2
libgl1-mesa-glx (7.4-0ubuntu3.1) to 7.4-0ubuntu3.2
libglu1-mesa (7.4-0ubuntu3.1) to 7.4-0ubuntu3.2
libmjpegtools-1.9 (1:1.9.0-0.0) to 1:1.9.0-0.0ubuntu3
mesa-utils (7.4-0ubuntu3.1) to 7.4-0ubuntu3.2[/I]

Now I read that they are used as replacment for the openGL thing, and now im wondering if they are of any use to me, and how can i keep them and still make my video players function normaly.

I've tried forcing them to an older version ( the one i had before the updates) but still no luck.

The rest of my packages in the update were:

[I]app-install-data-partner (11.9.04.2) to 11.9.04.4
dnsmasq-base (2.47-3) to 2.47-3ubuntu0.1
libnss3-1d (3.12.3.1-0ubuntu0.9.04.1) to 3.12.3.1-0ubuntu0.9.04.2
python-gobject (2.16.1-1ubuntu2) to 2.16.1-1ubuntu3[/I]

But they dont look to interfere with  general video settings, but i could be wrong


Soooooo any ideas....? :grin:

---

### Post by Struki on 2009-09-03
is there a reason why nobody is wiling to reply?

---

### Post by P4man on 2009-09-03
> **Struki said:**
> is there a reason why nobody is **wiling** to reply?

There wasn't, but there is now :s

Seriously, just 48 mins after you posted a non trivial question in a forum flooded with thousands of new questions per day and only so many knowledgeable volunteers  to help out, and then you imply *unwillingness * to help?

FWIW, in the last month I've contributed in over 600 threads trying to help where I can. During that time, I asked 3 questions and didn't get an answer either. But at least Im not accusing anyone of being *unwilling.*

---

### Post by Struki on 2009-09-03
Yea ok! I was simply wondering if im not folowing some rules cause most of my questions are not answerd so you could just tip an advice instead of counterattacking. I can't se the reason why something like that would even bother you if have 600 posts, and whay wouldn't you then simply answer my question. But nvm then...

---

### Post by andrew.46 on 2009-09-03
Hi Struki,

> **Struki said:**
> OK to cut it short my vlc/mplayer don't display video for any avi files

Can you run one of these files with MPlayer from the commandline as follows:

```
mplayer -v *[COLOR="Red"]myfile.avi[/COLOR]*
```

and post the terminal output here?

Andrew

---

### Post by Struki on 2009-09-04
Ok so here is the latest!

What I did before I saw the latest post on my thread was forcing all of my latest update packages down to the version prior to the updating. I had some minor problems but I managed, nevertheless my vlc and Movie player  still could not show any kind of video while audio was working properly, the only diference was that now I could see the video output in full screen, but whenever I tried to move the cursor or click anything the screen would turn white for the duration of that action (cursor moving or right clicking)

Next step was reinstalling the ati dirvers (Hardware specs are in the sig.) directly from the ati official site, and I had succes the players were working!

Now I ran the code after all of that as Andrew said an this is what I got:

[I]root@Laptop:/home/simun# mplayer -v myfile.avi
The program 'mplayer' can be found in the following packages:
 * mplayer
 * mplayer-nogui
Try: apt-get install <selected package>
bash: mplayer: command not found

[/I]The main question still remains if I update again I will probably have the same issue again, so since I know how to roll back to the latest working setting I'll try and update and then run the code and post again what happen...

---

### Post by Struki on 2009-09-04
[COLOR=Black]Hmmm now I'm confused, I updated again and there is no change, everything works!

But now I don't know what caused the problems at the first place. Anyway these are the packages I updated the first time and now for the second time.

[I]app-install-data-partner (11.9.04) to 11.9.04.4
libgl1-mesa-glx (7.4-0ubuntu3) to 7.4-0ubuntu3.2
libglu1-mesa (7.4-0ubuntu3) to 7.4-0ubuntu3.2
mesa-utils (7.4-0ubuntu3) to 7.4-0ubuntu3.2
python-gobject (2.16.1-1ubuntu2) to 2.16.1-1ubuntu3[/I][/COLOR]   


and in terminal with the command *mplayer -v [COLOR=Red]myfile.avi [/COLOR]*I still get

[I]root@Laptop:/home/simun# mplayer -v myfile.avi
The program 'mplayer' can be found in the following packages:
 * mplayer
 * mplayer-nogui
Try: apt-get install <selected package>
bash: mplayer: command not found[/I]

Since everything is working you could say I fixed my problem, so now I'm just wondering what is this thing with mplayer all about...

Thnx for help nevertheless!

[I][COLOR=Red]



[/COLOR][/I]

---

### Post by andrew.46 on 2009-09-04
Hi Struki,

> **Struki said:**
> 
```
root@Laptop:/home/simun# mplayer -v myfile.avi
The program 'mplayer' can be found in the following packages:
 * mplayer
 * mplayer-nogui
Try: apt-get install <selected package>
bash: mplayer: command not found
```


This is not a problem it simply means that MPlayer is not installed on your system. I have misunderstood you original question to mean that both MPlayer *and* vlc were not working, for which my apologies :P.

Andrew

---

