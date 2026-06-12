---
title: "Best Media Players"
date: 2006-02-24
forum: General Help
---

### Post by simoncoul on 2006-02-24
I'm in the process of making the complete switch from windows to linux(other then a few programs I have for school that only run on windows).   But I'm trying to find good media players, I currently use iTunes(big surprize) and media player classic(with the k-lite codec pack).

I really enjoyed this set up as itunes kept my music very organized and media player classic with the codec pack played anything.   

I saw a few good media players like VLC and xmms(I personally never liked winamp so I dunno if I'd like xmms).   But I was woundering what are the limitations of this programs, or if better ones could be suggest.

I saw banshee which had a very similar set up to iTunes, but I could not find alot of info about it or any media player on this forum(or I'm just stupid and couldn't find it).

Anyhow I'd like to hear the linux gurus say on which is best and why.

Thanks in advance!

Coulson

---

### Post by PsychoTrauma on 2006-02-24
I would recommend using rhythmbox, There is a updated version at [http://mighmos.org/](http://mighmos.org/) that works good for me. It looks pretty close to itunes I believe and it has good developement going on for it atm.

For video, totem-xine with the win32codecs from the mplayer site should do the trick for most videos. It's a basic interface but it should play almost everything you throw at it.

---

### Post by bluevoodoo1 on 2006-02-24
There's rhythmbox and amarok (people seem to like amarok a bunch). Rhythmbox and Amarok have that organized-itunes way to them, which is why I don't use them :) but Amarok is pretty snazzy. I use xmms most of the time... since you're not fond of that I don't have to elaborate! For video I use xine.

---

### Post by jchau on 2006-02-24
VLC

Pros: VLC can play pretty much anything you throw at it (music & video) (i'm a bit annoyed that it can't play midi).  I has a easy to use yet powerful interface.  It has a network capabilities like getting streaming video / audio.  It can plugin to firefox & has optional alsa support

Cons: I noticed that it doesn't quite quit all the time when I close the window.  If I open Application->System Tools->System Monitor, I can still see it running & sometimes I can still hear it play music after I close it.  You can just send it a TERM signal to close it (for real), but it gets a bit annoying.  

I use VLC.

---

### Post by ronmarley1 on 2006-02-24
I use XMMS with the EQU for XMMS (31 band equalizer) plugin for audio (mp3 and ogg).  It's pretty similar to Winamp, so if you didn't care for Winamp, you probably won't like XMMS.  Ther's quite a few plug-ins for it, so it is expandable.  I use Xine with the Totem front end for DVDs.  Everything works A-OK.  
The cool thing with Linux is that you can choose from many different apps for audio and video and stay with what you like best.
Good luck with your decision.

---

### Post by thelazzyone on 2006-02-25
I use Banshee and haven't looked back since! :D 

[http://www.banshee-project.org/Main_Page]("http://www.banshee-project.org/Main_Page")

---

### Post by Josef K. on 2006-02-25
_on kde:_

(I switched to arts-plugin)

best audio player is for sure amarok: it requires _terabytes_ of ram and musicbrainz support works randomly (some users made it works other no :confused:) but support almost everything, has a great interface, and is very scriptable

basically there're 2 video player: kaffeine and kmplayer
kaffeine (the default kde player) is great for occasional user (ask almost nothing, and manage almost everything without messing up with conf) but crash _always_ when turned off (not a big deal if you don't mind the pic of a bomb:rolleyes: )
kmplayer is a front-end for mplayer, require a bit search among repository to find a recent version with right dependancies, but never crash
I really hope kubuntu team wipe out kaffeine an switch to kmplayer

_on gtk_

(I use default gstreamer support)

bmpx (next generation of bmp\xmms) is a wery pretty player, but doesn't have db capabilities
quodlibet should the gtk-amarok :D, but lot of people (like me) cannot managed to make it work: there's a kind of fork, called listen, that should fix this but quodlibet authors made listen-project stop due to copyright issue
I heard banshee is pretty good, and works almost like amarok, but it doesn't work for me :-k 
there's also rythmbox that seems be a good choice (not sophisticated as amarok, not minimalist as bmpx)

for video playing
forget totem: with xine support seems work, but is simply a pain
best players are mplayer and VLC: they're both great
VLC manage better the fast-forward option but seems have sometimes a lag in subtitles, which I didn't notice in mplayer support

if I forgot some good player (or maybe somebody known how to make banshee\quodlibet work) please let me know :)

---

### Post by Skeletonix on 2006-02-25
for cinemas: mplayer
for music without database: Beep-media-player
for music with database: rhythmobox(but sometimes I have a problem with stability)

---

### Post by simoncoul on 2006-02-25
Does the terminal always run while mplayer is running?  Also how does VLC have the same codec capabilities, or are they easy to download like in windows?

Do most audio players support ipods?  Also do any have the ablility to get pod casts and online radio, I read there are plugins for some but which is hte best?

Thanks everyone for all the responses

---

### Post by nik on 2006-02-25
I'm surprised nobody has mentioned Quod Libet for music. I think it's great, many different views and cover art support. For streaming radio I use streamtuner and bmp, and for videos vlc.

---

### Post by Josef K. on 2006-02-25
[QUOTE=simoncoul]Does the terminal always run while mplayer is running? [/QUOTE]

don't understand
which terminal are you talking about?!:confused: 

>   Also how does VLC have the same codec capabilities, or are they easy to download like in windows? 

as usual
sudo apt-get install w32codecs
let you play almost everything (of course on 32bit, due to lack of 64bit codecs)

>  Do most audio players support ipods? 

don't have an ipod :) but for sure banshee and amarok support it (guess others too)

>   Also do any have the ablility to get pod casts and online radio 

yes

---

### Post by simoncoul on 2006-02-25
For mplayer all the screenshots I saw what I thought was the terminal (The thing u type command lines into, I could be wrong on what it is called).

I read in another post about Songbird, looks very nice I Was woundering if anyone uses it on windows, I read the roadmap and says it will be released for mac and linux in the next release.

[http://www.songbirdnest.com/features]("http://www.songbirdnest.com/features")

---

### Post by spahn on 2006-02-25
i still consider myself to be fairly new to Linux as well- i really enjoy the combination of streamtuner and XMMS.
Streamtuner gives you a ton of stations to choose from (more than itunes) and lets you bookmark them.
boogie on \\:D/

---

### Post by captainstormy on 2006-02-25
I really like VLC.  Its great for video and Audio stuff and I love using one program for both things.

Like said above, there is a bug that the program dosnt acctually close when you close it.  Ive only seen that like 2 times thou out of all the times ive used it.

---

### Post by Josef K. on 2006-02-26
this songbird sound really promising! :D 
but I'm afraid is still too young

---

