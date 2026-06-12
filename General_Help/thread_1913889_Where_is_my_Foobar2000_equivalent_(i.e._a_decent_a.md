---
title: "Where is my Foobar2000 equivalent (i.e. a decent audio player)"
date: 2012-01-23
forum: General Help
---

### Post by demonboy on 2012-01-23
I know this is a tired subject now but I've been using Ubuntu for a year to two now and I still cannot find a  decent audio player, nothing that comes close to Foobar2000 (which I've  tried in Wine but doesn't perform). I wondered if anyone could give me  some pointers. 

This is my list, in order, of the most important  features:

1. Ability to handle a very large media library without stalling
2. Ability to play many different audio formats (inc wma, ogg, flac and aac)
3. Ability to view my media library by file structure
4. Ability to view my media library by genre (ID3 tag)
5. Ability to view my file structure whilst also viewing playlist
6. Ability to add entire folders to playlist
7. Large font and easy GUI

What I **don't** care about:
1. Lyrics
2. Cover art
3. Online radio channels
4. Last FM etc
5. Visuals, skins
[B]
In a nutshell I am looking for a stripped down but powerful audio player  and manager for me to access my large offline audio library.
[/B]
Here are some initial thoughts on my experiences with the media players I've tried so far:

**Jaruk**
I thought I'd found the answer with Jaruk but after opening once and  asking me for my library location, it has forgotten the location and I  can no longer add my library. It displays nothing and I can't work out  how to add a folder. Online support limited so I've not solved this problem.  Suspect this is incompatible with 11.10 or  something.
[B]
Clemetine[/B]
This appeared to be quite good and I've been using it for a while. It almost ticks all the boxes but  there were three things that bugged the hell out of me. 1) You have to  drill down to the lowest level before you can add anything to the  playlist. You can't add an entire folder to the playlist, for example.  2) When you open an album as a playlist, the label of the tab at the top  inherited the entire folder directory,  making the label twice the  width of the screen! Why can't it just call it 'new playlist' before I  change the name of it? This feature renders Clementine almost unusable.  3) It's slow, though my computer is not the fastest machine.

**Banshee**
So terrible I can't believe this was shipped as the player that comes bundled with Ubuntu. Buggy as hell, crashes, etc. Rubbish.
[B]
Rhythmbox[/B]
Not bad and I haven't used it for a while but not that feature-rich in terms of viewing and interrogating file structures.

**Audacious**
Can't view my folder structure. Playlist-based view and also opens features in different windows. I hate that. Thought the rendering of a Winamp interface was weak.

**Quod Libet**
I did try this because someone told me it was the closest to Foobar. Sadly at the time of writing this I can't remember why I stopped using it! It might have been when I upgraded to 11.10 or something so whilst I await replies to this thread I will give it another go.
*[edit] Tried viewing by folder structure but it will not allow me to drag and drop a folder into a playlist! That's a bit unintuitive, isn't it?*

**Exaile**
It does allow me to interrogate my library by file structure but not sure I can view by IP3 tag/genre.

**Amarok**
As per Quod LIbet. Am installing now and will remind myself why I didn't like this. I was disappointed to see in USC that much development has been given towards online, web-based services, which are of no use to me.

Any suggestions gratefully received.

---

### Post by Cheesemill on 2012-01-23
Maybe try Guayadeque
[http://guayadeque.org/forums/index.php?p=/wiki/page/Home](http://guayadeque.org/forums/index.php?p=/wiki/page/Home)

---

### Post by satanselbow on 2012-01-23
**Decibel** does the job for me ;) I can't stand the "hey i'll mangle your carefully formatted/tagged/renamed music collection for you... but it'll take a day or 2... you don't mind if I undo all you good work while i'm at it? I'll swap in some wrong covers and everything!" mentality of media players either (both Win and 'nux)

It's in the repos or head over to [http://decibel.silent-blade.org/index.php?n=Main.Download](http://decibel.silent-blade.org/index.php?n=Main.Download) for the latest version ;)

---

### Post by demonboy on 2012-01-23
> Maybe try Guayadeque

Wow, that's a bit of a mouthful! I notice on the download page it says don't download with USC, not sure why. Also there is no version for Oneric but I'm going to download via USC and give it a go anyway. Thanks for the heads up.

---

### Post by prshah on 2012-01-23
> **demonboy said:**
> 
**Exaile**
It does allow me to interrogate my library by file structure but not sure I can view by IP3 tag/genre.


I too switched from Quod Libet to Exaile (but I too cannot remember why!)

Exaile does everything that I ask of it.

Yes, you can sort by Genre ID3 tag in exaile. In the "collection" tab, above the search box, you can select the type of view you want. If you are not able to see a drop down box, just blindly click about 0.5 cm above the search box, and it should appear. If you cannot see the search box, then blindly click about 1 cm from the left border, and just below the file menu.

I don't know if anyone else faces this problem, but in Exaile, some controls just disappear. They are there, but invisible until I blind-click on them.

You can sort by Genre-Album or Genre-Artist.

Please post back if you need more information, or a screen shot.

---

### Post by Cheesemill on 2012-01-23
> **demonboy said:**
> Wow, that's a bit of a mouthful! I notice on the download page it says don't download with USC, not sure why. Also there is no version for Oneric but I'm going to download via USC and give it a go anyway. Thanks for the heads up.
 
I think they say this because the version in the repos isn't current. As it's under heavy development at the moment the latest version has a lot more features/bug fixes.

There is a PPA for it:[FONT=monospace]
[/FONT]```
sudo add-apt-repository ppa:anonbeat/guayadeque[FONT=monospace]
[/FONT]sudo apt-get update[FONT=monospace]
[/FONT]sudo apt-get install guayadeque-svn
```

---

### Post by demonboy on 2012-01-23
Thank you, prshah, for the tips. I love your description of 'blind-clicking'! And satanselbow, I have downloaded Decibel to play with too, so thanks for that.

Over the last hour I have been playing with Guayadeque and I have to say it comes pretty close to what I am looking for. I did install the one from USC but I will uninstall and download the PPA for it instead. Thank you very much for that suggestion.

There are just a couple of things that I find frustrating, which perhaps the latest version has ironed out.

1. The 'playlist' is in the left column, the file library in the middle, and the corresponding tracks on the right. Therefore you are searching in the middle column, finding the tracks in the right column and then dragging them across the whole screen to the left column. This is counter-intuitive. Surely the file structure should be on the left, its content in the middle, and the playlist on the right.

2. That column on the right that contains the tracks, the only available columns are Name | Size | Modified. Why? Why can I not choose my own columns and why these three columns? I don't care about the file size or when I last viewed it, but I would like to rerank the list by album, genre, artist etc.

3. I can save my layout, which is great, but why do I have to load it up every time I open the app? Why can't it just remember from when I last had it open?

4. I would like to be able to move the windows or elements around. For example I would like the control buttons at the top, the name of the track at the bottom etc. This was easy in foobar. It's not essential but I'm finding that left column annoying. Normally I want to expand the column with the tracks in them so I can see all the details. However in order for that top left window to operate properly (the one with the controls, volume, track details etc) it needs to occupy at least a third of the screen. Since the middle column is my expanded folder tree view, that has to be a third wide too, meaning the last column which has all the track details is only a third wide, so all the columns are bunched together. This could be solved by having the controls and volume etc in a horizontal strip across the top. I would send a screen shot but I am typing this on a different computer.

I will continue to play with it, however, as it looks like it's a hot contender. Aside from the niggles above, which are quite important to its usability, I could live with it. Thanks once again, Cheesemill.

---

### Post by gmargo on 2012-01-23
I rather like the latest Clementine.  
I don't know if it addresses all of your issues, but I know I found it "easier" for me. The official repo version is outdated (v0.7.1 in Oneiric).

Version 1.0.0 is available in a ppa: 
[https://launchpad.net/~me-davidsansome/+archive/clementine]("https://launchpad.net/%7Eme-davidsansome/+archive/clementine")

There's also a cutting edge ppa, currently at Version 1.0.1:
[https://launchpad.net/~me-davidsansome/+archive/clementine-dev]("https://launchpad.net/%7Eme-davidsansome/+archive/clementine-dev")

---

### Post by nothingspecial on 2012-01-23
Guayadeque's developer is very active here

[http://guayadeque.org/forums/index.php](http://guayadeque.org/forums/index.php)

He appreciates all bug reports, feedback and suggestions.

---

### Post by demonboy on 2012-01-23
> **gmargo said:**
> I rather like the latest Clementine.  
I don't know if it addresses all of your issues, but I know I found it "easier" for me. 

See my OP, gmargo.

@nothingspecial - thanks for the link to the developer's website. I'll need it because I uninstalled the version from USC and installed the latest version from the PPA and it is playing up by not displaying any of my content. Anyways, it's bedtime here in India so I'll pick up on all this tomorrow.

Thanks all for the links and suggestions.

---

### Post by paradajz on 2012-04-18
I'm feeling your pain, demonboy. I've also tested out nearly every single player available for nix systems, including some terminal-based ones, and I still haven't found player which has all of these features:

Jump to now playing tracks
Playback follows cursor & cursor follows playback
Double-clicking a file in file manager adds track to specified playlist
Playback count synced with last.fm
Grouping of playlist items (with artwork)
Grouping of playlists the way I want to, not alphabetical or random or something else

It just frustrates me so much and believe it or not, I boot to Windows just to enjoy foobar2000. Using it via Wine feels slugish and with latest ubuntu and wine, the sound stutters alot. But, I feel like there's some hope, I'm back to testing Quod Libet and I find it rather usable (looking on my want-list that is) but the thing I miss the most is this:

double click track in file manager should send it to queue (I can't even select it as default player - what the foolishness?)

Edit:
Forgot to mention gmusicbrowser. I still can't figure the darn playback order, if I for instance type in search "prodigy", it gives me couple of albums, I play some track and when it's finished it plays something completly random from my librabry and it's driving me nuts.

---

### Post by rcosby on 2012-04-18
Have you looked at Beatbox?  You left it off your list.  I like the fact that it is lighter than most although it still 
has most of the features that I use.

---

### Post by arclance on 2012-04-18
@paradajz
Take a look at [Deadbeef]("http://deadbeef.sourceforge.net/") its interface is very similar to Foobar2000 and can do everything you want if you configure it that way.
You will have to check the lastfm plugin to see if it does what you want, I don't know anything about it.
I like it so much I went ahead and made this for it.
[[IMG]http://fc04.deviantart.net/fs71/i/2012/103/d/5/deadbeef_controls_conky_by_arclance-d4w147r.png[/IMG]]("http://arclance.deviantart.com/art/Deadbeef-Controls-Conky-295664535?q=gallery%3Aarclance&qo=0")

---

### Post by HiImTye on 2012-04-19
MPD is the best choice for media player, hands down but it requires a (very) little set up.
currently I'm listening to music and it is consuming less than 1% of my processor. you can plug into it with an array of clients (mpc/ncmpc/ncmpcpp/gmpc/etc) and it can be set up to serve your network with music, or even over the interweb. it handles just about anything you throw at it, provided they have a file extension (but its easy to [add one to missing files]("http://ubuntuforums.org/showpost.php?p=11848227&postcount=5")). it has a wide array of plugins that add functionality to it but it seems that those plugins are not big priorities on your list

---

### Post by paradajz on 2012-04-19
> **arclance said:**
> @paradajz
Take a look at [Deadbeef]("http://deadbeef.sourceforge.net/") its interface is very similar to Foobar2000 and can do everything you want if you configure it that way.
You will have to check the lastfm plugin to see if it does what you want, I don't know anything about it.
I like it so much I went ahead and made this for it.
[[IMG]http://fc04.deviantart.net/fs71/i/2012/103/d/5/deadbeef_controls_conky_by_arclance-d4w147r.png[/IMG]]("http://arclance.deviantart.com/art/Deadbeef-Controls-Conky-295664535?q=gallery%3Aarclance&qo=0")

I've tried to install latest version in 12.04 and it didn't work, I've started it and then nothing happens. Got solution for that?

Edit: Nevermind that, found .deb for oneiric and it works.

The only thing simmiliar to foobar is that it looks like it and that's just about it.

It doesn't have media library - definite turn off

---

### Post by arclance on 2012-04-19
> **paradajz said:**
> I've tried to install latest version in 12.04 and it didn't work, I've started it and then nothing happens. Got solution for that?

Edit: Nevermind that, found .deb for oneiric and it works.

The only thing simmiliar to foobar is that it looks like it and that's just about it.

It doesn't have media library - definite turn off
It is similar to the way I used foobar2000 maybe it is not to the way you used it.
You didn't mention that you wanted a media library in your post 
> **paradajz said:**
> 
Jump to now playing tracks
Playback follows cursor & cursor follows playback
Double-clicking a file in file manager adds track to specified playlist
Playback count synced with last.fm
Grouping of playlist items (with artwork)
Grouping of playlists the way I want to, not alphabetical or random or something else

otherwise I would not have mentioned Deadbeef.
I know where all my music is so I have never seen a need for a media library myself.
All the players I tried that had one felt slow and bloated, and did not work very well.

---

### Post by al111 on 2012-04-19
[Ultimate Player]("http://ultimateplayer.info/")

---

### Post by paradajz on 2012-04-20
I'm actually finding mpd+ncmpcpp combination AWESOME.

---

### Post by riks24 on 2012-04-22
I'm in the same boat as you, tried all the ones you have and a few more, I'm going to give [[COLOR=Blue]Foobnix[/COLOR] ]("http://www.foobnix.com/?lang=en")and Deadbeef a go.

There's a review from a while ago for it[COLOR=Blue] [here]("http://www.webupd8.org/2010/12/foobnix-023-comes-with-ui-changes-many.html")[/COLOR].

---

### Post by rickbeton on 2012-05-09
I'm totally fed up with Rhtyhmbox, which seems to defy my limited intelligence especially regarding lyrics & cover art. I've tried Banshee with some success - although everyone disparages it so.

Only today, I've discovered Clementine. It has a quirky UI not in step with the normal Gnome, but who cares?  It just seems to work right and I'm very impressed.

For the benefit of the original poster, you *can* add whole folders to the playlist.

* You get both the library view and the filesystem view to choose from.
* The library is nicely grouped into alphabetic sections, initially. There are several other 'group by' modes too.
* The song info and artist info work well.
* Cover art *just works*TM (unlike Rhythmbox!)

Rick :)

---

### Post by ohnonot on 2012-05-31
hello everyone, i'm on a similar quest.
have been comparing many mid-range audio only players. except the daemon-based players (mpd and xmms2) - couldn't set them up.
and some others probably.
i had been using **gmusicbrowser** which was just perfect but sadly it didn't work well with my old external ntfs (windows) hard drive which hosts most of my music.

@demonboy (if you're still around), **clementine** covers ALL your points - i think you really want to check if you got the newest version (1.0.1). there's a ppa.
also it plays everything. had to install some gstreamer plugins, but it politely told me what's missing.

**guayadeque** is version 0.3.5 now, my second favorite. you can drag ui elements around. it plays everything. seems a bit heavier and slower than clementine.

also **exaile**, which has a slightly cramped and less customizable layout, but it's all there. 

**foobnix** feels slightly buggy; it crashed once when i tried to open a russian radio station, but not a second time. also i don't like that it claims to be "like foobar2000". it's an exaggeration.

those players are simpler in my opinion because they lack some managing capabilities:

**deadbeef** is good, simple, quick. feels well made & robust. doubleplus: the equalizer can be integrated in the gui. probably my new ad-hoc player.
**decibel** is a bit bare and not very fast for being one of the simple players.
**listen** has some really nice features (now playing window with different colors, dynamic playlist filling), but is also missing some (no file browser, static columns). but i like it somehow.

all players take ~20% cpu (2GHz) whilst playing, but they are very different at startup, browsing, updating.


[_ultimateplayer and clementine are identical?_]("http://i.imgur.com/fx7ho.png") why?

if you're interested in new command line ways of approaching your music collection, you might want [_to take a look at this._]("http://ubuntuforums.org/showthread.php?p=11985754#post11985754")

ps: some players use qt4 for creating gui's (instead of gtk) which can look rather ugly. there's qtconfig-qt4 for customizing that (which is called qt4-qtconfig in the repos ;-)

---

