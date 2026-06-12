---
title: "Ubuntu n00b"
date: 2006-03-04
forum: General Help
---

### Post by Dale Hay on 2006-03-04
Ok, i've installed Ubuntu correctly... well it loads up correctly and normal, however I've never used Ubuntu before so I have no idea how it works or what it does, ect... now there are just 3 things that are bothering me...

1) How do I get my resolution higher than 640*480 ?? (As there isn't anything higher in the selection box)

2) How can I get on the internet (Using a SpeedTouch USB ADSL Modem) ??

3) How can I play music, as it won't let me... :(


(Oh and i'm sorry if this is in the wrong place...)

---

### Post by WelterPelter on 2006-03-04
RE: music - what do you mean it "won't let" you play? Are you trying to play from a CD or an mp3 file? What player(s) are you trying to use? More info please.

---

### Post by Dale Hay on 2006-03-04
I have just got an MP3 off my generic mp3 player. And it gives me an error saying "There is no plugin installed to handle a MP3 file". Right... so I take it I need a plugin? Where would I find that??

(Oh and i'm playing it in **Music PLayer**)

---

### Post by stuporglue on 2006-03-04
> 1) How do I get my resolution higher than 640*480 ?? (As there isn't anything higher in the selection box)

3) How can I play music, as it won't let me... 

I can help with 1 and 3. :-D 

1) Open a terminal and run "sudo dpkg-reconfigure xserver-xorg". It sounds like your video card wasn't detected completely correctly. You can find out more about your card by running "lspci | grep VGA" -- it might help you choose the right options in the dialog that dpkg-reconfigure brings up. 

After the dpkg command is done, log out, press CTRL+ALT+BACKSPACE and let the login manager restart, then log back in. 

3) gstreamer0.8-mad - MAD MPEG audio decoder plugin for GStreamer
 
That's what you want to get installed. Do a search for it in Synaptic. You may have to enable new repositores first -- search the forums as how to do that has been discused more than a couple times alread.

---

### Post by Dale Hay on 2006-03-04
[QUOTE=stuporglue]I can help with 1 and 3. :-D 

1) Open a terminal and run "sudo dpkg-reconfigure xserver-xorg". It sounds like your video card wasn't detected completely correctly. You can find out more about your card by running "lspci | grep VGA" -- it might help you choose the right options in the dialog that dpkg-reconfigure brings up. 

After the dpkg command is done, log out, press CTRL+ALT+BACKSPACE and let the login manager restart, then log back in.[/QUOTE]Erm... I don't understand any of the gibberish it was telling me when I ran that code... so I just kept everything to the default stuff except when it asked me about the screen resolution and now I'm back in... nothing has changed... the maximum I can choose is 640*480 >=[

This is too hard >_<

---

### Post by WelterPelter on 2006-03-04
[QUOTE=Dale Hay]I have just got an MP3 off my generic mp3 player. And it gives me an error saying "There is no plugin installed to handle a MP3 file". Right... so I take it I need a plugin? Where would I find that??

(Oh and i'm playing it in **Music PLayer**)[/QUOTE]

I'm not sure about the Music Player app. Perhaps it has a differnt name? I don't have it on my Ubuntu machine, and I don't see it in apt-get. 

If I were you, I would install XMMS. It's basically a Linux version of WinAmp, and should run right away on ubuntu with no problems. You can use apt-get to install it. Try typing this: sudo apt-get install xmms

---

### Post by xmastree on 2006-03-04
[QUOTE=Dale Hay]Erm... I don't understand any of the gibberish it was telling me when I ran that code... so I just kept everything to the default stuff except when it asked me about the screen resolution and now I'm back in... nothing has changed... the maximum I can choose is 640*480 >=[

This is too hard >_<[/QUOTE]
Firstly, and I mean no offence by this, there's an absolute beginners' forum which would be more suited to you I think.

As for the resolution, my bet is that it will be a refresh rate problem in your configuration file fot the x server. That sounds frightening, but it's quite easy to fix, and well documented here.

Firstly, try to find the data for your monitor from the manufacturers' website.
Then, armed with that information, open a terminal and type these commands in order:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.back
sudo gedit /etc/xorg.conf
```They're case sensitive, so make sure that's a capital X in there.
You will be asked your password the first time, use the same one as your login. The first command copies the file to a backup, the second opens the file in an editor.

Scroll down the file until you see a section something like this (taken from mine):

```
Section "Monitor"
	Identifier	"NEC CI CT700"
	Option		"DPMS"
	[COLOR="Red"]HorizSync	nn.n - nn
	VertRefresh	nn - nn[/COLOR]
EndSection
```See those lines in red? My guess is yours won't have them. Put in the data for your monitor there, but change **nothing else**. (I deliberately removed the figures from that example, because trying the wrong ones can damage the monitor...)
Save and exit, then press Ctrl-Alt-backspace to restart your desktop.

---

### Post by towsonu2003 on 2006-03-04
[QUOTE=Dale Hay]Erm... I don't understand any of the gibberish it was telling me when I ran that code... so I just kept everything to the default stuff except when it asked me about the screen resolution and now I'm back in... nothing has changed... the maximum I can choose is 640*480 >=[

This is too hard >_<[/QUOTE]
here's a suggestion on that: try to find the horizontal and vertical sync values of your monitor. via google or contacting the manufacturer, or the seller? 
do that dpkg-reconfigure thing again, and when it asks, tell it that you want to set you monitor stuff in advanced mode. once you enter the correct values (be careful, wrong values may physically break the monitor), you should get what you want... this is how in my system at least.

---

### Post by towsonu2003 on 2006-03-04
for the mp3 thing, search the ubuntu forums on how to get and install w32codecs (which is your keyword for searching)

---

### Post by Dale Hay on 2006-03-04
I'm totally lost... I feel really thick. erm.. where abouts would this "Absolute Beginners" forum be??

---

### Post by xmastree on 2006-03-04
Right [**here**]("http://ubuntuforums.org/forumdisplay.php?f=73")
Did you try setting your monitor rates? What's the exact make and model of it?

---

