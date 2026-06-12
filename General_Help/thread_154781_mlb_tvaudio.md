---
title: "mlb tv/audio"
date: 2006-04-03
forum: General Help
---

### Post by theOrange on 2006-04-03
Anyone able to get mlb tv and/or audio working?

Since they dropped real format and changed the layout - it is now WMV9 ONLY embedded/played via flash - i have not been able to get it to work.

I have Firefox 1.0.X and mplayer plugin.

I have even tried CrossOverOffice IE6 with WMP9 but still can't get it to work!!!

Any help would be GREATLY appreciated as this is the first time i feel i am being penalized for using Linux!!!

---

### Post by theOrange on 2006-04-04
Anybody?

---

### Post by rbenchley on 2006-04-04
There is some discussion over at this forum: [http://www.linuxforums.org/forum/mandriva-linux-help/57883-mlb-tv-realplayer-mplayerplugin.html]("http://www.linuxforums.org/forum/mandriva-linux-help/57883-mlb-tv-realplayer-mplayerplugin.html")

I've watched MLB.TV on my OS X machine, but like you, I haven't got it working on my Ubuntu machine yet and I'm feeling a little frustrated.  Good luck.  (Go Sox!)

---

### Post by prof_booty on 2006-04-06
[QUOTE=rbenchley]There is some discussion over at this forum: [http://www.linuxforums.org/forum/mandriva-linux-help/57883-mlb-tv-realplayer-mplayerplugin.html]("http://www.linuxforums.org/forum/mandriva-linux-help/57883-mlb-tv-realplayer-mplayerplugin.html")

I've watched MLB.TV on my OS X machine, but like you, I haven't got it working on my Ubuntu machine yet and I'm feeling a little frustrated.  Good luck.  (Go Sox!)[/QUOTE]


I've resorted to trying to get WINE to work so I can watch.  I can usually hear a mufffled audio stream while trying to watch the videos, and I'm fairly sure my mplayer plugins are configured correctly as I installed them from apt-get.  The mlb.tv FAQ says you can use RealPlayer, but I've never been presented with an option.  Thank goodness I only subscribed for a month...

---

### Post by purdy on 2006-04-12
Hey. I got mlb.com video working! Oh yeah!

I'd like to see if it works for a few people before posting a guide. 

Get in touch :)

-john

---

### Post by prof_booty on 2006-04-13
Love to be a guinea pig and help write a guide, please feel free to post details and I'll get to work on it tonight!

---

### Post by rbenchley on 2006-04-13
If you need additional guinea pigs before you post a guide, let me know.

---

### Post by prof_booty on 2006-04-17
Looks like others have had success editing mplayerplug-in.conf:

[http://www.thomascochran.com/article/47/mlbtv-running-on-linux-with-firefox-and-mplayer](http://www.thomascochran.com/article/47/mlbtv-running-on-linux-with-firefox-and-mplayer)

---

### Post by prof_booty on 2006-04-17
Hah!  Got it.  Little different than in the link above because Ubuntu doesn't seem to have this conf file in $HOME.  I'd like to see if this works for others.

First, make a back up of your mplayerplug-in.conf that you can use if this breaks anything.

$ sudo cp /etc/mplayerplug-in.conf /etc/mplayerplug-in.conf.bak

then, edit the file to force mplayer to open the video in a new window

$ sudo gedit /etc/mplayerplug-in.conf

find this line: 

#noembed=0

change it to 

noembed=1

Then go to mlb.tv and log in before clicking on the streams, this seems to be a key step.  

Anyway, I am watching the Angels/Orioles right now on dapper!

---

### Post by egghead3 on 2006-04-22
This worked great. Thanks.

---

### Post by egghead3 on 2006-05-03
Well, it was working great, until a reinstall of breezy. Now, when I launch mlb.tv, the mplayer window comes up and immediately closes/vanishes. I cannot for the life of me figure out what is different between my previous install and the current one.

Any ideas?

---

### Post by prof_booty on 2006-05-03
I've seen that behavior if I'm not logged in before clicking on the streams.  I also have seen it when I bookmarked the authentication page and logged in there.  There seems to be some sort of cookie or token passing that requires vising the site and then clicking on "Register/Login"

Did you install the W32 codecs? and the non-free flash plugin? Also, it might help if you post your /etc/mplayerplug-in.conf.

---

### Post by egghead3 on 2006-05-03
Investigating further, it seems like this is happening on any stream. I did not have mlb.com bookmarked and was logging in explicitely before attempting to run a video. And, as I said, it worked before. I should have all win32 codecs and flash installed, other media including flash seems to be working fine. Embedded videos are not streamed are also working.

```

#debug=0
#vo=xv,x11
#ao=arts,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
noembed=1
#cachesize=512
#use-mimetypes=0
#enable-ogg=1
#enable-smil=1
#enable-helix=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer

```

edit: Streaming quicktime, such as apple movie trailers, does seem to work. Windows media is what is having problems...

---

### Post by egghead3 on 2006-05-05
For some reason, it seems the win32 codecs were not installed, despite the command being included in a bash script i ran to setup my machine (everything else worked fine). (Re) Installing them did the trick.

---

### Post by 0MG on 2006-06-28
This really sucks.

I had MLB.tv working on my machine, worked like a champ.

Then, being who I am, I decided to not leave well enough alone. I went ahead and added some repositories to my apt sources list. After updating/upgrading, I no longer can watch MLB.tv. 

Everything looks right in my mplayerplugin.conf file; like I said it worked before. Anyone have any advice before I go ahead with a format and start fresh?

---

### Post by prof_booty on 2006-06-28
Does mplayer work in other websites?

---

### Post by 0MG on 2006-06-28
I'm the man. I'm the man. I'm the man. *Does a little dance*

All of a sudden after clicking the MLB.tv button like a madman for a while (as if it would make a difference) I got a message saying that totem didn't like the link and couldn't start. Then I realized that totem-xine was probably trying to start it.

apt-get remove totem-xine, restart firefox, GO BREWERS.

Works fine again.

---

### Post by russbuss on 2006-06-29
Anybody have any problems with audio on mlb.tv?  I have it working just fine, but no audio.

Audio works for other content from other sites which is why I find this odd.

Any takers?

---

### Post by egghead3 on 2006-07-29
Well as of yesterday something strange has happened that has apparently destroyed mlb.tv for me. I had it working great thanks to the guide in this thread.

I was watching in ubuntu yesterday when suddenly the window just closed. I haven't been able to get it back. I also have archlinux on the box so I switched over to that, where it had also been working. No luck. I then tried to watch from OSX on my powerbook (which worked, just had some syncing issues). Again no luck; I was beginning to think (perhaps hope) that there was some billing or account issue. 

Finally, I booted my pc into xp to check there. Strange things were afoot. Mlb.tv works, sort of. When I launch the game window thing, that flash cover for the embedded window player that exists in windows is gone, and instead I get the standard media player insert. Video works, but audio does not. 

It looks like they might be tinkering with their setup. The last time they did something like that they ditched the real format and we all got screwed big time. I highly doubt any of us will enjoy any "improvements" they might make. I'm going to try calling them tomorrow, but I hardly anticipate any helpful information being obatined.

Anyways, I was wanted to see if anyone else has mlb.tv and if it is still working for them, on any platform.

---

### Post by Dr. Nick on 2006-07-30
I have mlb.tv working with the mplayer plugin. They are very picky about IP addresses aswell, if you try and watch a local game they give no warning, you just dont get anyhting

Sometimes I am certain they are at fault, when the audio isnt working I just check another game, if it has audio i blame mlb.tv

Hopefully they change it for the better, took me awhile to get it working this time with the stupid flash intro.

---

### Post by egghead3 on 2006-07-30
Well its good to hear its still working for you. I have no idea what went wrong here. Strange that something is up in 2 different linux distros on my pc and OSX on my powerbook. ::sigh::

I can't even seem to get it to stream the free highlights. I guess I will try installing ubuntu on a fresh partition and see what happens.

Like I said, the plugin is working fine for other sites...

edit: In browsing on some mac forums, apparently they have made recent changes to the wmv server and how the playlists are handled or something that are causing mac problems. Have you actually gotten a game to work in the immediate past (say yesterday or today)?

---

### Post by Dr. Nick on 2006-07-30
yeah, ive heard from a friend with a mac that winmp is really outdated on osx

I watched a game just last night, but near the 8th inning it just died, I tried to get if back and never got mplayer to reappear, after several attempts it finally came back.

I did not change any settings during this time. It went from working, not working, back to working,


Their have been several other times where I just have to keep trying at it before it starts to work.

If you have the abality to reinstall a fresh copy of linux without much trouble then I might suggest you try Kubuntu out. I have one system with ubuntu and mplayer plugin that I ususally use to watch, but the other with Kubuntu and Konquereor browser with the Kaffeine player plugin seems to handle it slightly better,

---

### Post by egghead3 on 2006-07-31
Media player is really outdated on osx; I had been using a solution called flip4mac which allowed for playing wmv and avi files in quicktime. I mentioned it mostly just because it seemed a strange coincidence that it would stop working at the same time as my linux. 

Have you updated to the latest firefox? I'm wondering if this has something to do with things. It seems likely that they have made some change not to the video streaming, but to the flash on their site. Linux and osx aren't ever getting access to the stream url.

I have gotten mlb.tv working again by installing windows firefox in wine, getting the media launcher plugin, and creating a simple mplayer.exe script that redirects it to linux native mplayer. Obviously not the preferred solution, but at least I get the video going in the native player, so i only need to open mlb.com in the wine firefox.

I will have to try the kubuntu konqueror approach. I'm not a big kde fan, but its a hell of a lot better than windows.

---

### Post by Dr. Nick on 2006-07-31
Nope, after I got it all working I havent updated a thing in fear that it would cause errors.

I actually use the epiphany browser with mlb most times. Forgot to mention this before. When i use firefox sometimes the sound in the mplayer plugin doesnt work, I have always had better luck with mplayer+epiphany then with FF and mplayer.

---

### Post by 0MG on 2006-08-01
Still working for me. Only problem is I must have done something that doesn't  allow it to go fullscreen anymore. When I try to go fullscreen, it will just center the video in the same size with a huge black border.

Any ideas?

---

### Post by Dr. Nick on 2006-08-01
yes, answered this question just yesterday on another thread.

Open mplayer and get to the prefrences, click video tab and look at the output codec, if it reads X11 change it to xv and then restart mplayer or firefox and see if it works

---

### Post by 0MG on 2006-08-02
Thank you for the reply, I was already on XV though.

---

### Post by thousandrobots on 2007-06-25
I finally got this working. 

The key seems to have been opening MPlayer preferences, clicking the codecs tab, and selecting "Win32/vfw video codecs" in the video dropdown.

As others mentioned, I also edited the mplayerplug-in.conf file so that no-embed was set to true.

The stream works but seems to get choppy and flangy if I do to many other network operations while it's streaming.

---

