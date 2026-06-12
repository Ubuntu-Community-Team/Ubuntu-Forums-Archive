---
title: "How do you change the default program for multiple files at once?"
date: 2010-05-06
forum: General Help
---

### Post by kimangroo on 2010-05-06
I know you can change them one at a time by finding a relevant file and right clicking - open with, but I'd like to change all the media files that are currently set to open with the default media player to vlc.

Anyone know how this can be done?

---

### Post by WorMzy on 2010-05-06
There's a couple of places I know of where you can set defaults, these are:

Places -> Home Folder -> Edit -> Preferences -> Media

And

System -> Preferences -> Preferred Applications

---

### Post by philinux on 2010-05-06
> **kimangroo said:**
> I know you can change them one at a time by finding a relevant file and right clicking - open with, but I'd like to change all the media files that are currently set to open with the default media player to vlc.

Anyone know how this can be done?

You dont need to find all the files. Post #2 will do the job or right click on a file and select Properties>Open With. Select the program. That changes it globally.

---

### Post by vevel on 2010-05-06
> **WorMzy said:**
> There's a couple of places I know of where you can set defaults, these are:

Places -> Home Folder -> Edit -> Preferences -> Media

And

System -> Preferences -> Preferred Applications

"System -> Preferences -> Preferred Applications" might work here, though I don't know exactly what type of files trigger the 'multimedia' execution.   I think if this is set to 'custom' with 'vlc' or 'usr/bin/vlc' in the field, that could do the trick. 

I had run into this once before and ended up renaming /usr/bin/totem to totem.orig and linking vlc to /usr/bin/totem.  That might cause unintended effects down the road, though.

---

### Post by vevel on 2010-05-06
Oddly, I've had that fail before.  I probably had some tweak in place that broke the default behavior -- which is why I added the additional tweak of sym-linking vlc to 'totem' .  Yuck.

---

### Post by Roasted on 2010-05-06
I always just right click the file in question - Properties - Open With - and change there. Then it changed globally as mentioned above.

---

### Post by kimangroo on 2010-05-06
Thanks for the replies.

Unfortunately I can't seem to change the default programs for specific extensions which is what I want to do, with your two suggestions above.

Also, my first post was confusing, I want to be able to change the default program for every possible extension ie .mp4 .asf or whatever including for files I don't have on my computer. I'd also just like to see what files are associated with what players.

This is partly because I'm trying to work out another problem re the Totem plugin in Firefox which sometimes gives me the option to open streams it doesn't have the codec for in VLC (good) and sometimes in "Movie Player" (bad).

---

### Post by vevel on 2010-05-06
Could you provide us with a description (or URL) of the files that work versus cause problems?

---

### Post by WorMzy on 2010-05-06
Have you got totem-mozilla installed? Try uninstalling that and reinstalling mozilla-plugin-vlc. Alternatively, you can edit the plugins that Firefox uses from inside Firefox: Edit -> Preferences -> Applications, and change the action for the extensions you want to change. Unfortunately you need to modify each extension individually this way.

---

### Post by kimangroo on 2010-05-06
I feel I should start at the beginning:

Basically there are a number of streaming sites that I watch regularly, I think they are all mms (note I don't really know what that means).

By downloading gecko-mediaplayer plugin from synaptic I could get all but one stream to play. However I couldn't seek in streams that I had been able to in windows. That's a deal breaker because some of the streams have many hours of content.

I noticed that the same mms streams played well in vlc so I installed vlc-plugin. At first I couldn't get firefox to use this plugin even though I changed all the settings that I could in the preferences. I noticed that the plugin content manager (tools - manage content plugins) was completely buggy as well and I couldn't change or even select any of the options.

So I uninstalled gecko-mediaplayer, finally got the streams to use the vlc plugin only to discover the that plugin doesn't give you any controls whatsoever. 

On someone else's advice I then uninstalled that and installed gstreamer0.10-plugins-ugly and gstreamer0.10-ffmpeg. That solved the original broken stream but others that had worked no longer did.

In the meantime I noticed that the totem plugin when it tried and failed to find a plugin online sometimes gave me the option to open the file in vlc and sometimes in movie player when right-clicked.

I figured this was something to do with file associations in Gnome itself. Hence the question above about wanting to change all the media associations with movie player to vlc.

What I just did now, was to get a random file and rename it .asf, .wma, .wmv which I were all the extensions I could think of that work with mms and change it's open with properties each time.

So far so good. Totem tries to play the streams, fails miserably at which point I right click and open in vlc which does the job nicely with seeking enabled.

Hacky as hell but lets me watch what I want to watch.

If anyone has bothered to read this far and is willing to see if their setup can play and seek the following streams, I'd be interested to know what the proper plugin setup is which can deal with this inside Firefox.

[http://www.thalassa.france3.fr/?page=accueil&id=1&play=yes](http://www.thalassa.france3.fr/?page=accueil&id=1&play=yes)
[http://www.nhk.or.jp/rj/asx/jp/japanese.asx](http://www.nhk.or.jp/rj/asx/jp/japanese.asx)
[http://news.tbs.co.jp/news_mainprogram/asx/1_nb.asx](http://news.tbs.co.jp/news_mainprogram/asx/1_nb.asx)

Thanks!

---

### Post by kimangroo on 2010-05-06
AAARRRRRGGGGHHHH!


The gods definitely have it in for me today.

My little workaround was working nicely. Until I finished the last post, and thought right, enough messing about, wasting time trying to get stuff to work, time to watch some of these bloody streams, and of course something goes wrong again.

When I view the very same streams that were working ten minutes previously, now although I am streaming them (the cursor moves forward and the length of the stream is displayed correctly) I get no sound! With video, I get the picture but no sound. wtf.

Stranger still if I use the same vlc console that was streaming the video to now open a movie file locally, I still don't have any sound. If I double click the video and play it in a different vlc console the sound works fine.

I have no idea what is going on.

---

### Post by vevel on 2010-05-06
Haven't had a chance to try out streaming in firefox here, but thought I'd pass along this link, in case you hadn't tried it:

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

> 
VLC media player for Ubuntu Lucid Lynx 10.04 LTS, Ubunty Karmic Koala 9.10 Ubuntu Jaunty Jackalope 9.04
*Graphical way*
Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "multiverse" repository activated.
Search for vlc and install it. You should also install vlc-plugin-pulse, mozilla-plugin-vlc (and libdvdcss2).
If you are interrested in streaming or transcoding, you should also install libavcodec-extra-52.
*Command line way*
You need to check that a "multiverse" mirror is listed in your /etc/apt/sources.list.
% sudo apt-get update
% sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc


---

### Post by mb_webguy on 2010-05-06
There are a few things that could be at play here...

First, open Firefox and type "about:plugins" in the address bar.  This will show you the plugins currently in use, as well as the file types they handle.  If you type "about:config" in the address bar and change the value of "plugin.expose_full_path" to "true", you'll be able to see the full path to the plugins on the "about:plugins" page.  Make sure you don't have any conflicting plugins.

Second, you might want to check Firefox's applications list in Edit->Preferences->Applications.  You should be able to specify the plugin used to handle various types of file types and streams here.

Third, there's the Gnome defaults.  As has been stated, you could set System->Preferences->Preferred Applications->Multimedia (though I honestly can't tell you what that does), and you can right-click on a file and go to Properties->Open With (which obviously doesn't work with streams, since you don't have a file to right-click).  OR, if you don't mind getting your hands dirty, you could go straight to the source and follow [this guide]("http://ubuntuforums.org/showthread.php?t=51012") to edit your file associations manually.

---

### Post by mc4man on 2010-05-06
> If anyone has bothered to read this far and is willing to see if their setup can play and seek the following streams, I'd be interested to know what the proper plugin setup is which can deal with this inside Firefox.

In lucid the mozilla plugin works fine here for in browser.

You'll also get the little arrow box where you can choose to open in a player directly.
The player shown would be the first listed on the appropriate line in - 

~/.local/share/applications/mimeapps.list.

So for instance on the 1st link (mms stream), if I wished vlc to be in the dropdown (best choice for mms), this line with vlc.desktop first
> video/x-msvideo=vlc.desktop;totem.desktop;totem-xine.desktop;userapp-mplay-WN8J9U.desktop;
ect. ect.


=====================================

If running karmic I'd upgrade the gstreamer plugins from this ppa - not a plus for these streams but generally overall (obviously also has nothing to do with vlc, just a good upgrade in general

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by kimangroo on 2010-05-06
Thanks for the tips guys.

mc4man can I just confirm you can view all 3 streams with seeking enabled, you can start half way through the stream for example. If so which plugin did you mean by the mozilla plugin?

I'm using lucid btw.

---

### Post by mc4man on 2010-05-07
> mc4man can I just confirm you can view all 3 streams with seeking enabled

With the totem-mozilla plugin can seek in all 3. ( on first link any video on that site, tried some of the longer ones - a slight pause to re- buffer

(only have 1 browser plugin installed at once. - search totem-mozilla in synaptic


As far as the mimeapps line and opening in a player - bit of a mystery here that is going to drive me crazy...

On my desktop - simply by moving any of the .desktops in the line i posted to front of that line then that becomes what's shown in that drop down. - very handy ( or any new .desktops I add to line.

On my lucid laptop cannot get anything but 'Movie Player' to show up. No matter what I do...

So it was showing 'Movie Player' - edited line and see screen.

I guess I  may need to figure out what caused that added association in the first place.

Edit: figured it out - adding the line did no good for some reason. Still wouldn't affect the browser plugin.
The laptop had no .avi files, so created an empty text .file, named 1.avi, then  a r. click -> properties -> open with and choose an app other than totem. ( did a couple of times - used vlc and gnome-mplayer.

Now the first listed is what's shown in the dropdown.

If I wish to change then just moving another .desktop to front of line will do so

---

### Post by kimangroo on 2010-05-07
Thanks for getting back to me. It's good to know that I should be able to get it to work at least.

What I don't understand is isn't the totem-mozilla plugin installed as default? I have it on my system, but I'm pretty sure I didn't install it. I tried to watch the streams on a fresh install, and it definitely doesn't work out of the box.

I'm guessing you must have downloaded some codec packages as well. You don't know which ones do you?

I'll try and get rid of all the old plugins, but unfortunately firefox doesn't seem to get rid of the associations when I do that.

---

### Post by mc4man on 2010-05-07
> You don't know which ones do you?

You aren't going to need too much for these, since I've changed some things up on my lucid installs used a live cd to ck. instead.

Just doing this (only things installed) and they were playable and seek-able in the firefox in-browser player

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly

```

===========================================
Then installed vlc and set it as the default for .avi thru r. click - properties - open with and it also worked fine from drop down (again didn't have an avi so just made a dummy one with text file (applies to mms, mmsh streams

You may wish to also test your player(s) by using the url directly in them ( totem - movie - open location, vlc - media - open network stream or by pasting url into firefox's address bar

For the 1st link 
```
mms://a988.v101995.c10199.e.vm.akamaistream.net/7/988/10199/3f97c7e6/ftvigrp.download.akamai.com/10199/cappuccino/production/publication/France_3/Autre/2010/S17/120668_thalassa_integrale_300410.wmv
```

---

### Post by kimangroo on 2010-05-07
Thanks for the reply.

I'm pretty sure I already had installed all that gstreamer stuff, on someone's advice, but it only solved one of the three streams... Maybe I didn't have the gstreamer-bad one at first, but I do now though.

Anyway someone suggested ubuntu-restricted-extras and that seems to have done the trick with the three streams above.

I've now got just one or two streams that are being difficult on this page:

[http://www.rusnovosti.ru/online/](http://www.rusnovosti.ru/online/)

The Green loudspeaker icon opens a flash? proprietary player and doesn't play. This might not be ubuntu specific though because I sometimes had problems with it on XP.

The webcam icon opens a standard mms stream but doesn't play for me. (directly loading the mms in vlc works fine)

Do you think you could check these two out for me too?! I'm so close now, I just wish I hadn't messed about installing a bunch of plugins right at the beginning.

---

### Post by mc4man on 2010-05-07
> The Green loudspeaker icon opens a flash? proprietary player and doesn't play.

Not that I can understand anything (written or audio) but plays fine in in a pop up player - see screen

(not flash, if i find any more info will post back


Well - in vlc (note - it may take about 10 secs for stream to connect 
```
vlc http://cluster.quantumart.ru/broadcast/default.aspx?media=rsn
```

or 
```
mms://broadcast02.station.ru/rsn?MSWMExt=.asf
```


or make yourself a .m3u Ex. - named  RSN_Radio.m3u
```
#EXTM3U
#EXTINF:0,RSN Radio
mms://broadcast02.station.ru/rsn?MSWMExt=.asf

```

The url and or .m3u work also in totem, pana, ect. - again it does take a bit to load - *be patient* if trying in player vs browser

---

### Post by kimangroo on 2010-05-10
Well I still can't get the stream to play in Firefox no matter how long I wait, but that direct mms link you gave me works great, so I can just use that, until I can be bothered to fiddle about with plugins again.

Thanks very much mc4man.

---

### Post by Johannes Eva on 2011-01-12
> **kimangroo said:**
> I know you can change them one at a time by finding a relevant file and right clicking - open with, but I'd like to change all the media files that are currently set to open with the default media player to vlc.

Anyone know how this can be done?


Yes, there is a way to do this. It is a somewhat clumsy way but it works. As it needs a longer explanation, I have written an article about this:

_**[How to change file associations on Ubuntu]("http://www.johannes-eva.net/change-the-default-application-ubuntu-linux")**_

(Tested with Ubuntu 10.10 Maverick Meerkat)

---

