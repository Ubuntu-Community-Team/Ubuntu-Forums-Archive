---
title: "Need help with viewing WMP + QT in Opera...help!!!"
date: 2009-07-14
forum: General Help
---

### Post by falen_pl on 2009-07-14
I've tried probably every possible plugin there is and I still can't view WMP/QT. 

I was partially successful with kaffeine - I could view WMP but the plugin would download the video file and open it in seperate window (as oppose to playing it within the browser - just like flash will do in with youtube videos), which was annoying as hell.

I'm using Jaunty and Opera 10 (4478). Everything works just great (flash, java etc.) except WMP and QT. 

I have a feeling that mplayer pluging is the best choice since people say good things about it and I just probably installed it wrong. 

I tried following Opera's installation guide but I couldn't make it past the initial stages:

1.Make sure you have the Gecko SDK installed.
2. Download the mplayerplug-in source code.
3. Type ./configure --enable-x [--with-gecko-sdk={path}] where {path} is 
the path to the Gecko SDK 

How do I install Gecko? I downloaded both versions from the official site but I've no idea what to do with them next. They're just a bunch of libraries. 

So, what I'm asking for is somebody to give me a hand and walk me thru the installation of mplayer plugin so I can view WMP/QT in Opera. Please!

---

### Post by falen_pl on 2009-07-14
OK, so gecko players handles wmp...well, kind of. 

This I can view no problem:

[http://teledyski.onet.pl/10173,5234979,teledyski.html](http://teledyski.onet.pl/10173,5234979,teledyski.html)

However, this won't play. 

[http://wiadomosci.onet.pl/5276141,1,1,1,relacjetv.html](http://wiadomosci.onet.pl/5276141,1,1,1,relacjetv.html)

Instead it gives me some bull about not having enabled Java Script, which is not true.

Still no luck with apple's trailers, though.

Generally, I have a problem with distinguishing what plugin is required for a given site. 

For instance, I know that in order to view flash I need have a proper plugin installed and then in Opera's TOOLS/PREFERENCES/ADVANCED/ DOWNLOADS/ assign "file extension - swf" to that plugin. What about wmp and QT? There's at least few choices.

So basically, what I need help with is:

1) installing mplayer plugin properly 
2) assigning mplayer plugin to play WMP+QT

I wanna stick to mplayer because I'm using it as a default video player and I don't really wanna have 5 different players installed, each for different tasks.


Please, Obi Wan Kenobi, you're my only hope ;)

---

### Post by falen_pl on 2009-07-14
All right, I fixed this mess. This is how I managed, somebody might find it helpful. 

So this is what allowed me to view Quick Time and WMP files in Opera:

First of all, I kept trying with mplayer-plugin. I followed this guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I got rid of every plugin that was either already installed or added by me. I installed mplayer plugin and launched mozilla to check if I can view QT/WMP. I couldn't. Mozilla either didn't view anything (WMP) or crushed on me (QT). So for all this time I was thinking it was Opera's fault but since the plugin didn't work under mozilla too, I blame the plugin. Screw it, I uninstalled the *******. 

Following the same guide I installed gecko mediaplayer. I also deleted everything from Opera's plugin folder (I manually copied there some plugins from mozilla's plugin folder since I read it might help -- it didn't). I restarted the system and, after making sure mozilla can view everything and Opera can see the plugin, went straight to apple.com/trailers. And what did I find out? There's new movie about vampires starring Ethan Hawke coming out soon, you should see the trailer...KOWABANGA it works. So is WMP. Such a relief, I spent hours trying to figure it out yesterday :D:D:D

---

