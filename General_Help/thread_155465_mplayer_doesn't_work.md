---
title: "mplayer doesn't work"
date: 2006-04-05
forum: General Help
---

### Post by harys on 2006-04-05
hi, ive successfully installed mplayer with synaptic manager. i have this message when i want to run a streaming media on the net. mplayer open with this error message : New_ face failed. maybe the font paath is wrong. please supply the text font file (~/.mplayer/subfont.ttf). need a help. thanks. harys

---

### Post by trent dillman on 2006-04-05
Find a font you want for subtitles and copy it to that location.

Try:

cp /usr/share/fonts/truetype/freefont/FreeSans.ttf ~/.mplayer/subfont.ttf

---

### Post by OffHand on 2006-04-05
go to the synaptic and search for mplayer fonts. install them and you are good to go  :)

---

### Post by crazy_fox on 2006-04-05
Damn was it that easy??!?

I had to manually compile install mplayer. and then download the assets (gui theme, and fonts) from the website :S

---

### Post by Nordoelum on 2006-04-05
Have tryed this:
 
> 
How to install Multimedia Player (MPlayer) with Plug-in for Mozilla Firefox 
[LIST]
[*]Read [#General Notes]("http://easylinux.info/wiki/Ubuntu#General_Notes")
[*]Read [#How to add extra repositories]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")
[*]Read [#How to install Multimedia Codecs]("http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Codecs")
[*]Read [#How to install DVD playback capability]("http://easylinux.info/wiki/Ubuntu#How_to_install_DVD_playback_capability")[/LIST]```
sudo apt-get install mplayer-386
```
 
```
sudo apt-get install mplayer-fonts
```
 
```
 
sudo apt-get install mozilla-mplayer

```
```
sudo cp /etc/mplayer/mplayer.conf /etc/mplayer/mplayer.conf_backup
```
 
```
sudo gedit /etc/mplayer/mplayer.conf
```
[LIST]
[*]Find this line[/LIST]...vo=x11,         # To specify default video driver (see -vo help for...
[LIST]
[*]Replace with the following line[/LIST]vo=xv,         # To specify default video driver (see -vo help for
[LIST]
[*]Save the edited file
[*]Read [#How to refresh GNOME panel]("http://easylinux.info/wiki/Ubuntu#How_to_refresh_GNOME_panel")
[*]Applications -> Sound & Video -> MPlayer
[*]Restart Mozilla Firefox[/LIST]
 
[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox]("http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox")

---

### Post by harys on 2006-04-05
hi, i installed the mplayer-font with synaptic and now it work. i'm unable to view and listen streaming media file from the internet. for example the link at [http://www.bbcworld.com/content/template_talkingmovies.asp?pageid=665&co_pageid=2](http://www.bbcworld.com/content/template_talkingmovies.asp?pageid=665&co_pageid=2).  What could i do ? thanks. harys
ps. : when i click on the link and then chose gmplayer , mplayer open and i can't view anything nor listen.

---

### Post by Nordoelum on 2006-04-05
[quote=harys]hi, i installed the mplayer-font with synaptic and now it work. i'm unable to view and listen streaming media file from the internet. for example the link at [http://www.bbcworld.com/content/template_talkingmovies.asp?pageid=665&co_pageid=2]("http://www.bbcworld.com/content/template_talkingmovies.asp?pageid=665&co_pageid=2").  What could i do ? thanks. harys
ps. : when i click on the link and then chose gmplayer , mplayer open and i can't view anything nor listen.[/quote]
Looked at the above post?

---

### Post by David Haas on 2006-04-05
harys--I can play the movie trailer that you listed with Totem/Totem Xine (see in Synaptic for these), but only when I selected the RealPlayer format. On selecting Windows Media format, the video played, but not the sound. With Totem, I can play video and sound streaming media in Windows 9 format, but with Windows 10 format, the sound doesn't play--only the video. I assume that the current wiin32 codecs can't handle the newer Windows 10 media format. I had the same problem when I was using MPlayer. Does anyone in this thread know about this?
David

---

