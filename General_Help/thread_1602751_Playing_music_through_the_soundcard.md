---
title: "Playing music through the soundcard"
date: 2010-10-21
forum: General Help
---

### Post by xtremesupremacy3 on 2010-10-21
Hello,

I use a chat program called Paltalk. Sometimes music is played.
I want to play music into the room too but rather than play music loud and then have the mic close to it, I would like to play the music from the soundcard.

If this is possible, how?

---

### Post by linuxpyro on 2010-10-21
Do you want to play music from an external source (like a CD player) into your computer?  If your sound card has a line in, it should be straightforward, especially with PulseAudio.  You might want to check into the sound configuration panel; I'm not sure how to do it right now, but I'll check it out.

---

### Post by xtremesupremacy3 on 2010-10-21
no basically, I want to play music on my Rhythmbox but fix it directly into a mic chat, but i use headphones so not to disturb people around me, so what I want is that the people in the chatroom can hear my music, but i dont need to remove headphones. Kinda like a virtual cable

---

### Post by linuxpyro on 2010-10-22
Alright, I think I see what you mean.  Try this: first, install pavucontrol:

```

sudo aptitude install pavucontrol

```
You could also do it in the software center if you're not comfortable with the command line.

Next, open the Pulse Audio Volume Control, should just be Applications->Sound & Video->PulseAudio Volume Control.  When you get it, click on the Input Devices tab.  At the bottom in the Show drop-down menu, select All Input Devices.  In the window you'll find a level called something like Monitor of Internal Audio Analog Stereo (that's what it was called on my system).  Make sure that that option is unmuted, and that the button with the green checkmark is pressed.  After doing this I was able to play a song in Rhythmbox and record it using the Sound Recorder application.  I'm not familiar with Paltalk, but you might have to mess with the sound settings there too.

---

### Post by xtremesupremacy3 on 2010-10-30
Sorry for the late reply but thats done it.

Thanks very much!

+1

---

### Post by buckeyered80 on 2010-11-01
Hey xtreme,

If you don't mind my asking, how did you get paltalk to work on Ubuntu? Are you using a VM or did you get it to work through Wine?

---

### Post by xtremesupremacy3 on 2010-11-01
Well I have it on a VM, through Wine but also through Mozilla Prism.

With Mozilla Prism if you direct it to [http://express.paltalk.com](http://express.paltalk.com) then you can use Paltalk Express, which I use most of the time.

Through Wine, you are best using wine1.2 or wine1.3, then you want to install vb6run, ie6, all the fonts and dotnet (using winetricks)

After that is done, download MSN for windows and install it through wine. Once that is done, simply download Paltalk, install...and enjoy

---

### Post by buckeyered80 on 2010-11-02
Interesting...I didn't even know about Mozilla Prism. I'm going to give that a shot, thanks.

---

