---
title: "Youtube won't play in Firefox"
date: 2009-09-19
forum: General Help
---

### Post by thompsonstudios on 2009-09-19
I've read some pages with tons of how to play the videos on youtube. It seems to work for many but, as a newbie, I'm still struggling to understand why it's difficult to play videos. I tried gnash, mplayer, greasemonkey, vlc and I have no clue what to do with theses add ons. I'd like to start over and have some one to suggest and walk me through getting youtube to work on my newly installed Ubuntu on my Imac G5 PPC

---

### Post by lovinglinux on 2009-09-19
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by HappyFeet on 2009-09-19
Just remove gnash or anything else you have tried, and do
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by thompsonstudios on 2009-09-19
> **lovinglinux said:**
> See **Solution** [*[COLOR=Red]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").

 I ended up with :

E: Couldn't find package flashplugin-nonfree

---

### Post by thompsonstudios on 2009-09-19
> **HappyFeet said:**
> Just remove gnash or anything else you have tried, and do
```
sudo apt-get install flashplugin-nonfree
```


I removed gnash and still got:

E: Couldn't find package flashplugin-nonfree

---

### Post by lovinglinux on 2009-09-19
> **thompsonstudios said:**
> I removed gnash and still got:

E: Couldn't find package flashplugin-nonfree

I guess you are using Hardy Heron then, right? I don't remember which package installs it on Hardy, but you can get the deb file from Adobe site [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by thompsonstudios on 2009-09-19
> **lovinglinux said:**
> I guess you are using Hardy Heron then, right? I don't remember which package installs it on Hardy, but you can get the deb file from Adobe site [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Jaunty Jackalope. I tried the Adobe site. I guess I'm screwed on a Imac G5 ppc ~non! intel

---

### Post by sideaway on 2009-09-19
Well there is aone way. sudo apt-get install youtube-dl

Then just in a console;

youtube-dl [www.youtube.com/yourvideoextention1234abcde](www.youtube.com/yourvideoextention1234abcde). That'll download it to your home directory, I know it's annoying, but that's the only way I could get yt on a ppc.

---

### Post by odinb on 2009-09-20
> **thompsonstudios said:**
> I've read some pages with tons of how to play the videos on youtube. It seems to work for many but, as a newbie, I'm still struggling to understand why it's difficult to play videos. I tried gnash, mplayer, greasemonkey, vlc and I have no clue what to do with theses add ons. I'd like to start over and have some one to suggest and walk me through getting youtube to work on my newly installed Ubuntu on my Imac G5 PPC

This is what I do:

First install Medibuntu repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

And then I do the following to get basically all media to work:

(Much of this info came from: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683))

--== Browsing experience/video-Audio codecs ==--

	sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4 vlc gxine libxine1-ffmpeg gstreamer0.10-plugins-ugly-multiverse w64codecs msttcorefonts flashplugin-nonfree sun-java6-plugin

NOTE!!! Change w64codecs to w32codecs if running 32-bit OS!
NOTE!!! Change libdvdread4 to libdvdread3 if running Intrepid or older OS!

Note: When installing Sun Java you will be asked to accept an end-user license agreement (EULA) before the installation of the Sun Java packages begins. Press the tab key on your keyboard (above the caps lock key), followed by the enter key to accept the EULA and complete the installation.

Also, if something (like Java) will not install, try sudo apt-get install ubuntu-restricted-extras

Alternative GNOME front-end for Xine called Gxine (this is optional, VLC will do just fine):
	sudo apt-get install gxine libxine1-ffmpeg

Now you can test a DVD with VLC, Gxine or whatever your favourite media player is.

Note: Enable deinterlacing ("VLC > Video > Deinterlacing > Blend") if playback is choppy or if you notice artifacts.

--== Streaming Video ==--

Streaming Video (Gecko Media Player, for virtually streaming anything):
for ubuntu, remove totem etc.:
	sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
	sudo apt-get install gnome-mplayer gecko-mediaplayer

Good luck!

---

