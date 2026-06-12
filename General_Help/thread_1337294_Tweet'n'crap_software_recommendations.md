---
title: "Tweet'n'crap software recommendations"
date: 2009-11-25
forum: General Help
---

### Post by StuartN on 2009-11-25
I am going to install Ubuntu 9.10 on my undergraduate student daughter's laptop shortly - she has had enough of Windows, but will dual-boot until she is sure Ubuntu meets her needs. I have to get it right because she lives a long way away. She will want to tweet'n'crap with software that I never use, so I would appreciate any recommendations and comments:

**O2 mobile connect broadband modem Huawei E1752** - sounds like it should work, but not out of the box (e.g. [http://blog.simple2web.ie/?p=363](http://blog.simple2web.ie/?p=363))

**MSN instant messenger** - aMSN seems to be more popular than using either Empathy or Pidgin, more like the experience that MSN users expect.

**iPod sync** - currently an iPod Classic. It sounds like nothing will actually sync, but Amarok looks good (or gtkPod, Banshee or Songbird). I want to avoid reformatting the iPod and I don't want trouble if it is connected to iTunes again - ideally it should be able to switch seamlessly between the two. The music collection is on the laptop in mostly MP3, possibly some Apple or Windows media, with no DRM on anything.

**Webby stuff** - it sounds like flashpluginnonfree is about all that Firefox needs, for Youtube. If there is any must-have addition for tweeting and the like, please comment.

**DVD playback** - enable medibuntu etc. Likewise mp3 playback with gstreamer plugins.

**Windows partition** - I was thinking of adding this to fstab mounted at /media/Windows so that the original filesystem is always mounted, and I can't think of a reason why not, except it won't mount following a Windows unsafe halt.

**Cool stuff** - is there any cool eye candy that doesn't suck up system resources? A nice theme and wallpaper should be enough. Compiz effects will work, but performance is poor.

---

### Post by icyj on 2009-11-25
I found this blog post has some good recommendations when setting up computers for linux newcomers.  Its worth a look:

[http://theindexer.wordpress.com/2009/10/25/to-do-list-after-installing-ubuntu-9-10-aka-karmic-koala/](http://theindexer.wordpress.com/2009/10/25/to-do-list-after-installing-ubuntu-9-10-aka-karmic-koala/)

---

### Post by audiomick on 2009-11-25
Hallo,
I haven't read these completely myself, but they might be useful to you.

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)
[http://ubuntuforums.org/showthread.php?t=1310795](http://ubuntuforums.org/showthread.php?t=1310795)

Medibuntu might have something, too:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


Michael

---

### Post by Johnsie on 2009-11-25
Alot of people are using skype these days

---

### Post by StuartN on 2009-11-25
> **Johnsie said:**
> Alot of people are using skype these days

I was just about to say "I forgot skype"! I am glad to see it works natively in Ubuntu.

---

### Post by Johnsie on 2009-11-25
Yeah, the Windows version is slightly more up-to-date, but the Linux one does the job. I think you might need to play around with the audio settings to get it to work properly with Karmic though. Something to do with pulseaudio or something (sound on Linux confuses me)

---

### Post by Junkieman on 2009-11-25
> **icyj said:**
> I found this blog post has some good recommendations when setting up computers for linux newcomers.  Its worth a look:

[http://theindexer.wordpress.com/2009/10/25/to-do-list-after-installing-ubuntu-9-10-aka-karmic-koala/](http://theindexer.wordpress.com/2009/10/25/to-do-list-after-installing-ubuntu-9-10-aka-karmic-koala/)
Including extra software sources is a good point, but replacing your entire list with the blogger's list (as they suggest) is not something I recommend. 

Also mentioned is antivirus, which isn't really required. What AV in Ubuntu *is* useful for, is checking USB disks from Windows PC's, and stripping worms from email (attachments) before you accidentally forward them on to friends.

[Alternativeto]("http://alternativeto.net/") is a site I only recently discovered, but is great for finding cross-over apps between platforms :)

---

### Post by StuartN on 2009-11-25
> **Junkieman said:**
> replacing your entire list with the blogger's list (as they suggest) is not something I recommend.

I couldn't actually read the blogger's list. I haven't strayed much outside the standard Ubuntu repositories myself, but I don't share the same interests in the always-on, scrobbled-up world. Even so, I think enabling Medibuntu and all the regular Ubuntu sources should be enough to get started.

> **Junkieman said:**
> Also mentioned is antivirus

This is really helpful, actually, because the university network might require an active antivirus package, and it is no effort to provide it. Besides, it can check the mounted NTFS filesystem - the Windows AV it has now is treacle-slow.

The big choices are the iPod sync and instant messaging. I use drag and drop with my player, which behaves like a regular USB drive, and have never messaged - so I have no idea what features matter. Amarok and aMSN seem functional and popular.

Many thanks, all, for the excellent links.

---

### Post by audiomick on 2009-11-25
> **StuartN said:**
>  I use drag and drop with my player, which behaves like a regular USB drive, and have never messaged - so I have no idea what features matter. 
Me too. I don't care much about the features either. I just want a computer that does exactly what I tell it to and nothing more and doesn't pretend to be intelligent.;)
Does that make me old? I'm only 45...

---

### Post by Junkieman on 2009-11-26
> **StuartN said:**
> The big choices are the iPod sync and instant messaging. I use drag and drop with my player, which behaves like a regular USB drive, and have never messaged - so I have no idea what features matter. Amarok and aMSN seem functional and popular.

For MSNing some of us love the feature that allows you to send custom emoticons, which aMSN handles well. The latest version has plenty new updates, making it an exceptional MSN replacement!

I found Rhythmbox handled my iPod pretty well, but that was a 4th Gen,

---

### Post by StuartN on 2009-11-26
> **audiomick said:**
> Me too. I don't care much about the features either.

This child lives to tweet'n'crap, so I have to find out what is important amongst the younger folk! Merely directing the machine to do something is not enough anymore, it has to be social and predict what the user wants.

(I am getting a standalone internet radio / uPnP music player myself, which shows my age).

[QUOTE=junkieman]For MSNing some of us love the feature that allows you to send custom emoticons, which aMSN handles well. ... I found Rhythmbox handled my iPod pretty well, but that was a 4th Gen,[/QUOTE]

Thanks. I'll set up aMSN. The iPod Classic is supported by Rhythmbox, so I could try that before anything else. I really don't want to cause a severe iPod musicectomy, but it seems that Linux packages are more accommodating than Windows, which don't like switching between packages or host machines. It is possible (or certain, even) that this one will get dual-booted into iTunes and so connect to two different packages with the same music collection.

**Firefox UserAgentSwitcher** - this seems like a really useful addition, especially when some websites decide to restrict their readers, e.g. [http://www.linuxjournal.com/content/tech-tip-view-apple-movie-trailers-firefox-linux](http://www.linuxjournal.com/content/tech-tip-view-apple-movie-trailers-firefox-linux)

---

### Post by StuartN on 2009-11-29
Many thanks for all the suggestions and links, the upgrade from Vista was a great success. I had a problem with the repartitioned Vista not booting, but it's fixed.

I am particularly grateful for the suggestion to stick with the default Rhythmbox to handle the iPod. Rhythmbox indexed all her music in several minutes (about 850 albums), pops up when the iPod is connected and displays the music collection, the iPod contents and the NAS uPNP music collection. Albums and tracks can be dragged between any of them, but there is no synchronisation - much like I handle my own music. The iPod owner was thrilled that Linux didn't trash her iPod, her music collection or both, as that seems to be normal behaviour in iTunes.

Everything else works, except a Creative Webcam that has no driver.

The Windows partition is installed in her home directory, so she can retrieve all her files. Thunderbird with all accounts and mail was fine. I could not test the Huawei wireless broadband, but installed and configured Usb_switcher and hope it works straight off. Skype installed flawlessly, but the default microphone volume was zero - it only needed a right-click on the volume applet to find and reset it. aMSN looks and behaves just as expected. All the MP3 and DVD stuff is working.

---

### Post by Junkieman on 2009-11-29
Good to hear that.

I know it's a shame the iPod Syncing support is lacking, but you can create smart playlists for favourite/random/unheard tracks, that dynamically update as your music library changes.

Which modem model is that, check if it works out-the-box for other folks. Got to be sure that little detail works, mine didn't and that stopped me from upgrading and I skipped Jaunty completely. Luckily 9.10 just works :)

Also get a whole bunch of videos of different formats and play them, to make sure the codecs function, same for audio files. 

Leave some info on Ubuntu for her just in case, for online I suggest these forums ;) For offline, the [Ubuntu pocket guide]("http://www.ubuntupocketguide.com/") is good. Written for 8.10, but it's still very relevant and explains many concepts, from file basics to customising with themes.

Also I just realised, a good idea to add RAR archive support (picking these up as I'm using my new install). This will allow the default archive manager (file-roller) to create and extract:

```
sudo apt-get install rar unrar
```

---

