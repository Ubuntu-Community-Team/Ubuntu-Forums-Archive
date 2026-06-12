---
title: "Problems :P"
date: 2006-03-02
forum: General Help
---

### Post by Minyaliel on 2006-03-02
I'm having two problems which I consider quite serious... bear with me...

1. My WLAN card won't work after I had to reinstall Kubuntu. It worked out of the box before. I'm using the Topcom one.

2. Online radio won't work! :cry: Kaffeine tells me I probably need to install a few plug- ins, but not which ones. Except for shouting "no fair" I have no idea what to do about this.

Also, one question: is it possible to play .avi movies in Linux?

---

### Post by andrewsawyer on 2006-03-02
Not sure why your WLAN card would have stopped working.  Which chipset is it?

Online radio and avi would require codecs.  Have a look at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) as they list the ones that most peolpe will need.  Note: w32codecs and divx4linux and maybe a couple of others won't download as they are no longer kept on the server.  You should be alright without them.

You could also try installing totem-xine from Synaptic.  This also has a firefox plugin.  Might help you.

---

### Post by Minyaliel on 2006-03-04
*isn't quite sure what  chipset is* This is what is written on the card label: 
> Skyr@cer Pro PC Card 3054
Wireless LAN PC Card
108 Mbps super g
Hope that helps somewhat... :P

I have downloaded the stuff from the Guide (well, except those that weren't working)... still doesn't work :P

---

### Post by souteneur3190 on 2006-03-04
yes totem, mplayer, xine, vlc can all play avi's... pretty standerd for linux.

---

### Post by Jeff Eklund on 2006-03-04
[QUOTE=Minyaliel]1. My WLAN card won't work after I had to reinstall Kubuntu. It worked out of the box before. I'm using the Topcom one.[/quote]Could be that you need the restricted modules for your kernel to get it working. The restricted modules provide you with closed propriatory drivers for hardware.
[QUOTE=Minyaliel]2. Online radio won't work! :cry: Kaffeine tells me I probably need to install a few plug- ins, but not which ones. Except for shouting "no fair" I have no idea what to do about this.[/quote]Probably a problem with codecs. Check out the wiki: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[QUOTE=Minyaliel]Also, one question: is it possible to play .avi movies in Linux?[/QUOTE][quote=souteneur3190]yes totem, mplayer, xine, vlc can all play avi's... pretty standerd for linux.[/quote]AVI is a containerformat. The video and audio streams within the avi could be coded with several different codecs. Get the correct codecs to be able to play the file. So, in avis case, it's not dependent on the fileformat, but what codecs the streams has been encoded with.

---

### Post by Minyaliel on 2006-03-04
[QUOTE=Jeff Eklund]Could be that you need the **restricted modules** for your kernel to get it working. The restricted modules provide you with closed propriatory drivers for hardware. ...
AVI is a containerformat. The video and audio streams within the avi could be coded with several different codecs. Get the **correct codecs** to be able to play the file. So, in avis case, it's not dependent on the fileformat, but what codecs the streams has been encoded with.[/QUOTE]

Alright, that sounds logical... any idea on  where to get those?

---

### Post by Minyaliel on 2006-03-04
Look, I installed the stuff from the wiki, and tried to listen to a stream (still with Kaffeine). 
> There were no decompilers found to handle the stream. You might need to install the correspondending plug- ins.
Same as last time, I believe. :P

---

### Post by nalmeth on 2006-03-04
[http://www.ubuntuforums.org/showthread.php?t=114251](http://www.ubuntuforums.org/showthread.php?t=114251)

easiest way to install that stuff,
won't help with wlan tho.. I wish I could help you with it, but I can't even get mine going. My wlan problem seems all but unresolvable, so I wish you luck

---

### Post by Minyaliel on 2006-03-04
Alright, I made the stream work.... but the sounds all choppy.... *sigh*

---

### Post by Minyaliel on 2006-03-05
bumpity

---

### Post by lupine_nickt on 2006-03-05
Apparently, Madwifi ([http://madwifi.org/wiki/UserDocs/GettingMadwifi](http://madwifi.org/wiki/UserDocs/GettingMadwifi)) works with that particular wlan card. Try compiling it from source, and see if it gives you any joy.

xF,

...Nick

---

### Post by ren wins on 2006-03-05
what are you using to listen to the streams? firefox? konqueror? some media player?

i suggest getting VLC to play your movie files, once you get the codecs and restricted codecs activated (from the guides people posted) it'll play just about everything. and if it doesnt, then mplayer will play the rest.
that was the simplest way i found to get everything working

---

### Post by Minyaliel on 2006-03-10
I haven't compiled software before - how do I do that?

I've been using Kaffeine to listen to streams. It's strange, because I can listen to some streams, while I can't listen to others. For instance, I have no problems hearing the soundfile played on this site: [www.xanga.com/luthienundomiel](www.xanga.com/luthienundomiel) but get error messages on this site: [www.sleepbot.com](www.sleepbot.com).

VLC? Hm. Will try it :)

---

### Post by Adrian on 2006-03-10
[QUOTE=Minyaliel]I haven't compiled software before - how do I do that?

I've been using Kaffeine to listen to streams. It's strange, because I can listen to some streams, while I can't listen to others. For instance, I have no problems hearing the soundfile played on this site: [www.xanga.com/luthienundomiel](www.xanga.com/luthienundomiel) but get error messages on this site: [www.sleepbot.com](www.sleepbot.com).

VLC? Hm. Will try it :)[/QUOTE]

I don't know if this is helpful or not, but I'm listening to a sleepbot broadcast right now, using XMMS. However, I had to save the .pls file on my disk and open it locally for it to work. However, I'm using SUSE at the moment.

So, maybe you can give XMMS a try. It's a little primitive though and I usually prefer amaroK for audio streams. Unfortunately, my amaroK is a little messed up right now, so I need to fix some things before I can use it :)

---

### Post by Minyaliel on 2006-03-10
Well.... VLC worked. Weee! But even with your method, Adrian, sound is still choppy... :(

---

