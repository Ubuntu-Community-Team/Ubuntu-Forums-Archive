---
title: "Does WINE work?....At all?"
date: 2009-11-05
forum: General Help
---

### Post by arnab_das on 2009-11-05
I havent found a single windows software which works on WINE so far. utorrent used to work with jaunty, but doesnt work with karmic anymore.
also, i found that wine changes the font settings so that my firefox fonts looked perfectly weird.

i seriously doubt the use of this program. its way too buggy for use.

(sorry for being a bit rude here, but i have been trying wine for quite sometime now and nothing in that program is working for me! :( )

---

### Post by matthewbpt on 2009-11-05
It works great for Spotify, Half Life 2, and Dvd Shrink. Don't really use it for anything else. I also tried it with Microsoft Office 2007 and it worked pretty well, but I prefer OpenOffice anyway. What programs did you try it with? You might want to look at [www.winehq.org](www.winehq.org) , it has a compatibility database for Windows programs using wine.

---

### Post by arnab_das on 2009-11-05
i tried using flickr uploadr, vinn player etc.

---

### Post by mCion on 2009-11-05
check what version of wine you're using.  Try different versions, sometimes that helps.

Like it was mentioned earlier, check the database at WineHq.  

Also, it may not be likely for your case, but I remember having to install a modified version of Wine for a specific program once.  That info was also in winehq.

---

### Post by orasis on 2009-11-05
> **arnab_das said:**
> I havent found a single windows software which works on WINE so far. utorrent used to work with jaunty, but doesnt work with karmic anymore.
also, i found that wine changes the font settings so that my firefox fonts looked perfectly weird.

i seriously doubt the use of this program. its way too buggy for use.

(sorry for being a bit rude here, but i have been trying wine for quite sometime now and nothing in that program is working for me! :( )


I've only had one program that would not work with it and it was a Direct3D heavy game but other than that I have not had much problems with wine... probably because I rarely use, or need, Windows software anymore. 

So, yes --wine does work but it's not a God layer ... it runs a few things perfectly everything else is pretty much hit and miss. 

If you really need something that cannot be done with Linux just run Windows via Virtual Box. That's what I do for Civilization III the only thing that keeps me from selling my Windows disc on Ebay... :)

---

### Post by ciaopaulo on 2009-11-05
Yep works great for Spotify. Although I had to run the installer from XP, slightly defeating to objective, but once installed the exe runs as normal* under Ubuntu 9.04 (except the occasional scroll bar issue... :) )

---

### Post by myromance123 on 2009-11-05
Your Wine version matters!

 Gotta stress that.
What comes with Karmic's installation is WINE ver 1.0.1.
I have been using ver 1.1.32 since Jaunty and it has stayed the same in Karmic, there really is no difference UNLESS your version of WINE has *_changed_* :D

Make sure.
To make sure, Applications->Wine->Configure Wine
Then click on the  'About'  tab. The first thing listed will be the version you are using :)

---

### Post by Mark Phelps on 2009-11-05
> **arnab_das said:**
> ... I havent found a single windows software which works on WINE so far. utorrent used to work with jaunty, but doesnt work with karmic anymore...

Wine only works with SOME Windows apps, mostly the older versions.

The link below is to the CodeWeavers Application Compatibility database site.  Use it to search for the windows apps you're trying to run.  If they are rated Platinum or Gold, there is a different problem and you need to post you questions in the Wine subforum, not here.  If they are not rated, or are rated Garbage or Bronze -- you're wasting your time on Wine:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

### Post by grumpyoldgit on 2009-11-05
I can confirm that Spotify works fine with Wine on 9.10.

---

### Post by JugglinPhil on 2009-11-05
It's true there's quite a lot of stuff that doesn't work in wine, however Jedi Academy works alright (no sound, but I can get used to that).

---

### Post by tacantara on 2009-11-05
I had a limited success with Wine when I added Play On Linux to the mix.  POL figures out which version of Wine you need to run certain apps, then assists in the installation and running of those apps.

The limits of my success were with web browsers.  I was able to run IE 6 and 7 (with some glitches), and IE 8 wouldn't run at all.  I was also able to run the more recent versions of FF for Windows, but again with glitches.

In my opinion, gamers benefit the most from Wine and POL, although it can handle some other apps.  Your best bet is a virtual machine running Windows (my personal #1 choice) or a dual-boot system.

---

### Post by crowfield on 2009-11-05
> **arnab_das said:**
> 
also, i found that wine changes the font settings so that my firefox fonts looked perfectly weird.
 :( )

I had that problem as well. Just remove the ttf-mscorefonts that are installed with wine.

---

### Post by Giblet5 on 2009-11-05
For those who want to run Windows apps w/o lobotomizing their PC in order to do so, Wine sometimes does what's needed.

It can be disappointing, especially for people who are strictly Computer Operators (people lacking any/all knowledge of how computers or software work).

It's worth noting that Windows can emulate a Linux system quite well. CygWin being the prime example.

So, why can Windows emulate Linux but not vice versa? Easy: Windows is closedsource while Linux is opensource. The folks who provide Cygwin have Linux source to build that clever Linux emulation from. The Wine developers must reverse-engineer *everything*.

IMO, Wine does an impressive job of emulating an ugly, ancient, featureless, operating system whose latest and greatest release (Win7) still has both legs hopelessly mired in the primordial ooze of VAX VMS and CP/M.

Wine is to Windows apps, as Chilton's is to those maintaining a rusty old DeSoto classic car: It takes dedication.

---

### Post by myromance123 on 2009-11-05
Its actually a lot harder on the WINE devs.
Legally they can't reverse-engineer windows, SO they can only study how it functions and reacts and try to mimic it.

 Its like trying to make a car but never getting to see whats inside (like the engine, or how the wheels are attached).
They are doing a pretty darn good job. Its up to us to help them and yes truly start looking for Linux alternatives or making alternatives to Windows Apps. 

Its a hard movement but its gotta be done sooner or later.

---

### Post by fox.esq on 2009-11-05
NO, WINE is a pipe dream.  Until those numb skulls figure out some intuitive, functional GUI  to make work for the common computer user, it will always be a waste of hard disk space. The only people who can get it to work have some sort of degree in Terminal script - and terminal is really the only way you can get it to work... if you're lucky.

---

### Post by arnab_das on 2009-11-05
> **fox.esq said:**
> NO, WINE is a pipe dream.  Until those numb skulls figure out some intuitive, functional GUI  to make work for the common computer user, it will always be a waste of hard disk space. The only people who can get it to work have some sort of degree in Terminal script - and terminal is really the only way you can get it to work... if you're lucky.

well said mate. i totally understand the trouble programmers are facing right now, but the thing is, at the end of the day, wine is going to be used not by software engineers or programmers but by users who want windows programs to work on linux/ users who find linux apps hard to figure out. i dont think wine is helping either in its present form.

---

### Post by shazbut on 2009-11-06
> **arnab_das said:**
> well said mate. i totally understand the trouble programmers are facing right now, but the thing is, at the end of the day, wine is going to be used not by software engineers or programmers but by users who want windows programs to work on linux/ users who find linux apps hard to figure out. i dont think wine is helping either in its present form.

Exactly.  What are we paying these guys for?  Oh, wait...

---

### Post by arnab_das on 2009-11-06
> **shazbut said:**
> Exactly.  What are we paying these guys for?  Oh, wait...


well its true we have great people behind ubuntu who dont work for money. but at the end of the day, we all want ubuntu to be as popular as windows! dont we? its no use if ubuntu is popular among a handful of people. most of the apps for ubuntu are really really good. and in many cases even better than its windows counterpart. but then, there's this software which claims to do a lot, but does nothing, except making some strange changes to ur browser font settings! ubuntu is not going to get popular with non-working softwares.

sorry for sounding harsh, but thats the reality.

---

### Post by arnab_das on 2009-11-13
> **crowfield said:**
> I had that problem as well. Just remove the ttf-mscorefonts that are installed with wine.

how do i do that?

---

### Post by lykwydchykyn on 2009-11-13
> **Giblet5 said:**
> 
It's worth noting that Windows can emulate a Linux system quite well. CygWin being the prime example.


CygWin is not analogous to WINE.  CygWin is a collection of open source applications which have been ported to Windows to provide a *nix-type environment for Windows.  You cannot run native Linux binaries in CygWin, they have to be ported to the cygwin environment and recompiled.

WINE is an attempt to make native Windows binaries run on non-windows OS.  TOTALLY different ballgame there.

---

### Post by hwttdz on 2009-11-13
To remove ttf-mscorefonts (note this is how you remove anything, to remove and remove config files as well replace remove with purge, to install new software say install)

sudo apt-get remove ttf-mscorefonts

The functionality of software seems to have little to do with adoption, rather advertising does.  As as linux does not advertise popularity seems unlikely to be forthcoming.  

Running non-native software will never work as well as running native software, if you want something that works well contact the software publisher and tell them you need something that works with your operating system.

---

### Post by hwttdz on 2009-11-13
Also, please avoid posts like this in the support forum.  The support forum is intended for support requests, this sort of thing can go in the cafe.

---

### Post by arnab_das on 2009-11-13
> **hwttdz said:**
> To remove ttf-mscorefonts (note this is how you remove anything, to remove and remove config files as well replace remove with purge, to install new software say install)

sudo apt-get remove ttf-mscorefonts




thanks. btw how do i know if this is the font which was installed by wine? (coz i want to remove that) i think this font is installed by ubuntu restricted extras as well. i want to basically keep the ubuntu version and remove the wine version of this font coz it modifies the way firefox looks.

---

### Post by hwttdz on 2009-11-13
You can view information about packages from synaptic, maybe you should see what packages require ttf-.... 

There's probably also a fix for the firefox fonts for those who want to keep the package installed if you google for it, that seems like a more reasonable solution.

---

### Post by arnab_das on 2009-11-13
> **hwttdz said:**
> Also, please avoid posts like this in the support forum.  The support forum is intended for support requests, this sort of thing can go in the cafe.
  
i wanted to know if other users were facing the same problems as i am. i've tried wine numerous times with various softwares but none of them were worked!

also plz note i have specifically mentioned the name of the programs which didnt work. so, dont mistake this as a hate thread or something.

---

### Post by hwttdz on 2009-11-13
Perhaps you should just be more clear when posting, for instance if you're having trouble with utorrent in wine you might title a thread "utorrent not working in wine, giving error 431" and then post the output of "wine utorrent.exe" in your thread and outline what the behavior is.

---

### Post by arnab_das on 2009-11-13
> **hwttdz said:**
> Perhaps you should just be more clear when posting, for instance if you're having trouble with utorrent in wine you might title a thread "utorrent not working in wine, giving error 431" and then post the output of "wine utorrent.exe" in your thread and outline what the behavior is.

point taken. okey dokey, will do that from next time. thanks again.

---

### Post by GeoPirate on 2009-11-13
I don't understand why people want to just complain, you're using linux, so try to use linux apps, there are a couple torrent programs that use the same backend as utorrent, just with a differnt front end, makes to much sense to just use the linux version, and using IE, just makes even less sense... But a little reading on the wine site reveals that the beta version of wine is pretty stable and has a lot of compatibility issues resolved.  If you don't believe me check out your karmic ubuntu software store and it's actually on there by default.

---

### Post by Giblet5 on 2009-11-13
This is an interesting thread. Some of you are using Wine to run emulated Windows applications for which there are better native Linux applications.

eg, running a Windows torrent app under Wine is like using a $30,000 custom Ducati motorcycle to tow a tractor.

```
sudo apt-get install ktorrent
```

---

### Post by ed-koala on 2009-11-13
I use Wine for World of Warcraft, nothing more, and it works magnificently so far through 9.04 (just got 9.10 working, can let ya know tomorrow on 9.10 and wine and wow).

Here's a few suggestions for programs to replace those beloved windows favorites:

Bittorrent - Deluge.  Love it, easy to config, easy to use. Does everything you'll need except superseed (they don't believe in that over at deluge central).

CD/DVD burning - K3b.  Again, does all you should ever need and a very easy to use interface.

Video watching - VLC. I like Totem, works fine for me, but most folks seem to love VLC cause it'll play anything.

MS Office - Open Office, comes with your install.

MP3s - PLaying em, I like rhythmbox, but most folks like other stuff. You'll find plenty of posts on these forums on what folks think is best. I'm a simple needs kinda guy here, I just play em, and this does that just fine.

If you need any other suggestions for what can replace such and such windows programs, just post and ask, you'll get no small number of suggestions.

---

### Post by arnab_das on 2009-11-14
okay since there's a bit of confusion, i'll tell u why i had to use wine. u see, there's no video editor which works as per my requirements.

u might say there's handbrake - but it cant change resolutions.
there's winff - but apparently the MS codec is a bit problematic.
there's devede (most useful app)- cant convert to xvid (really dont want to use divx).
avidemux - really really slow even on a 64 bit processor and to be fair its a little crash prone.

and here's what i need -  a software which can convert any video to xvid playable on a dvd player.

now, i'll tell u what, i have been using loads and loads of linux apps on ubuntu, but none of these softwares can convert videos like windows apps. (dont know why this is so) somehow, super converter or convertx etc. do a lot better job in converting videos than linux apps (i dont know why this is so, but dont both have the same dependecies, i mean both use ffmpeg right?) i'm not complaining but this is just a fact. i have reported bugs in various sections but debugging takes time, so its unfair to expect rapid development. i'm highly impressed with programs like k3b, avant, comix, gtk blog editor, kid3, songbird etc. but this one is still a grey area for me.

apart from this little pain, there's no other windows app or anything of windows which i miss.

---

### Post by RealG187 on 2009-11-14
> **arnab_das said:**
> I havent found a single windows software which works on WINE so far. utorrent used to work with jaunty, but doesnt work with karmic anymore.
also, i found that wine changes the font settings so that my firefox fonts looked perfectly weird.

i seriously doubt the use of this program. its way too buggy for use.

(sorry for being a bit rude here, but i have been trying wine for quite sometime now and nothing in that program is working for me! :( )Why would you be using Firefox in Wine for?

---

### Post by arnab_das on 2009-11-14
> **RealG187 said:**
> Why would you be using Firefox in Wine for?

am not using using firefox in wine. just installing wine changes the default firefox font settings.

i think i've posted pics as well of the problem. here's the pic.  when i posted the pics i didnt know if it was because of wine, but later when i uninstalled wine everything was worked perfectly! [http://ubuntuforums.org/showpost.php?p=8173059&postcount=3](http://ubuntuforums.org/showpost.php?p=8173059&postcount=3)

---

### Post by 23dornot23d on 2009-11-14
I have just checked and after the upgrade non of my previously installed programs
in wine appear to be working ......

Tell a lie .... Notepad works ok

Typical error message .....

[http://i36.tinypic.com/33abee1.jpg](http://i36.tinypic.com/33abee1.jpg)

[IMG]http://i36.tinypic.com/33abee1.jpg[/IMG]

The AMazing thing though is if ..........

I point the links direct to the C:\   
drive and Program Files on the Windows Vista Drive

I am having some success ...........

Not sure how safe it is doing it this way though ?

Wine Actually is working very well ........... the USB external drive and Nautilus seeing it is not .....

and it also is not seeing the directory for all my previous WINE Installations ....... 

Anybody else got this similar problem ?

---

### Post by RealG187 on 2009-11-14
> **arnab_das said:**
> am not using using firefox in wine. just installing wine changes the default firefox font settings.

i think i've posted pics as well of the problem. here's the pic.  when i posted the pics i didnt know if it was because of wine, but later when i uninstalled wine everything was worked perfectly! [http://ubuntuforums.org/showpost.php?p=8173059&postcount=3](http://ubuntuforums.org/showpost.php?p=8173059&postcount=3)It changes your Firefox in Ubuntu?

---

### Post by arnab_das on 2009-11-15
> **RealG187 said:**
> It changes your Firefox in Ubuntu?

it does for everyone not just for me. check this thread
[http://ubuntuforums.org/showthread.php?t=1301943](http://ubuntuforums.org/showthread.php?t=1301943)

---

### Post by MaxIBoy on 2009-11-15
Unreal Tournamen: Game of the Year works flawlessly.
Starsiege: Tribes works pretty well.

Those are the only legacy Windows applications I have any need for.

By the way, World of Warcraft has been clocked running faster in WINE than on Windows. (But seriously, who plays that thing anyway?)

---

### Post by RealG187 on 2009-11-15
> **arnab_das said:**
> it does for everyone not just for me. check this thread
[http://ubuntuforums.org/showthread.php?t=1301943](http://ubuntuforums.org/showthread.php?t=1301943)What would Wine have to do with anything?

---

### Post by arnab_das on 2009-11-15
> **RealG187 said:**
> What would Wine have to do with anything?

well that was what i figured out! wine modifies the tahoma font and firefox fonts were restored the moment i uninstalled wine.

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
I run GTA SA, GTA 3, GTA VC, Tomb Raider Anniversary, Star Trek Armada 2, and DivX so far. Works pretty well if you have it configured right.

---

### Post by chipfryer on 2009-11-18
Dreamweaver MX 04 / Flash MX 04 and a few other programs including MS office did work wonderfully until the event of 9.10. A few days ago my programs were running even if they did take a long time to load.

Once again however nothing happens, only a flicker on the screen.
To me this terribly annoying since all was perfectly ok before.

I know this is slightly off topic and I apologize to the first poster for hijacking this thread slightly but it is important too regarding the first question on this thread.

The version as mentioned does make a difference too.

---

### Post by RealG187 on 2009-11-20
> **Sin@Sin-Sacrifice said:**
> I run GTA SA, GTA 3, GTA VC, Tomb Raider Anniversary, Star Trek Armada 2, and DivX so far. Works pretty well if you have it configured right.Did SA work like that or did you have to configure something?

---

### Post by WatTwo on 2009-11-20
SA works "out of the box" and sa-mp works good in wine now to, just need to change 2 DLL's

---

### Post by HuaiDan on 2009-11-20
I've always found wine extremely mysterious and a little evil. There's so little clear, centralized documentation on anything useful.


For example, a search for appplication compatibility (   [http://appdb.winehq.org](http://appdb.winehq.org)   )  doesn't have any results for IE or Internet Explorer.  There's an app that will only run on IE I need to use, and I can't find any quality info on how to make a tabbed version of IE work in WINE.  Not sure where to start looking, either.

---

### Post by chipfryer on 2009-11-21
I have IE6 running in 9:10 not as good as it used to as it throws up an error box just as wine does now before loading two MS programs. 

Instructions are available at:
WARNING!!!
[www.tatanka.com.br/](www.tatanka.com.br/)

***** Apparently this has been reported to Google as an **attack site**? I've no idea why however? I've been running IE6 for months now on a solo Ubuntu Install.

Hope this helps but treat with caution yeah.
Best.

---

### Post by HuaiDan on 2009-11-22
Hey I tried out ies4linux.  Seems to work great, once "settled in".

---

### Post by chipfryer on 2009-11-22
> **HuaiDan said:**
> Hey I tried out ies4linux.  Seems to work great, once "settled in".

Glad it worked out for you. :D

---

### Post by arnab_das on 2009-11-22
what exactly is XPCOM error? get it all the time with wine.

---

### Post by Dr. Freeze on 2009-12-02
I play GuildWars in WINE everyday

---

### Post by Cheesemill on 2009-12-02
> **arnab_das said:**
> and here's what i need -  a software which can convert any video to xvid playable on a dvd player.

Can you be more specific please. DVD players can't play xvid, they only play DVD's.

---

