---
title: "Low Mic volume in Skype"
date: 2010-06-23
forum: General Help
---

### Post by CoolJohnB on 2010-06-23
So pleased to finally get mic working thanks to this forum problem I have now is the volume is very low in Skype, I have set it to 100% but it is barely discernible on playback from the Skype test.  Any suggestions?

---

### Post by Denz Choe on 2010-06-23
Look at this link [http://www.uluga.ubuntuforums.org/showthread.php?t=312237](http://www.uluga.ubuntuforums.org/showthread.php?t=312237)
It helped alot of people, but I'm still facing the same problem. Still looking for answers :(

Open the terminal window and type "alsamixer"

---

### Post by CoolJohnB on 2010-06-23
Thanks for the link explains things in detail, but please excuse my ignorance, how do you increase the volume in alsamixer?

---

### Post by dhysk on 2010-06-23
Hiya JohnB,

alsamixer per the link provided .

1) type in **alsamixer in a terminal**, 
2) toggle via "tab key" to "capture" view, 
3) there you will see a row, with "capture" written on the bottom, 
4) increase the volume to that to maximum. (increase the vol to maximum, for   any row you can,in this window)

3)open sound recorder, and in the option, where it says, "record from", chose "capture".

also if you still have the little speaker controle on you're system tray you can go in thier and play with that as well.  You just have to go to view and check the correct boxes to enable the controles.  It's worth looking at but the alsamixer is faster and easier i think.

---

### Post by CoolJohnB on 2010-06-23
Ok have done the bit with alsamixer was only able to adjust volume in "Capture" couldn't get to the other two, how do I do that?

Also in sound recorder I can't find option "record from" where is that?

In sounds I now have an option in hardware to choose Digital Duplex should I do that?

---

### Post by CoolJohnB on 2010-06-23
Tried Digital doesn't work with Skype, am getting slightly better volume but it's still low, where is Mic boost in sound recorder?

---

### Post by Denz Choe on 2010-07-09
> **CoolJohnB said:**
> Tried Digital doesn't work with Skype, am getting slightly better volume but it's still low, where is Mic boost in sound recorder?
Hi JohnB,
yeap, I'm getting very minimal boost too like you. I'm still **searching** for a solution. 

I'm running on dual boot mode (windows & ubuntu). Strangely it records fine with appropriate amplification in Windows. I've read somewhere that the sound driver in Ubuntu doesn't work well with certain integrated mic. It has been highlighted, but I haven't check on its fix status though.

If you have found a solution (even with another program), I'd appreciate if you post it here :) 

> **dhysk said:**
> Hiya JohnB,
3)open sound recorder, and in the option, where it says, "record from",  chose "capture".


Hi dhysk,
I'm with JohnB on this, I can't find the option "record from" as well..

---

### Post by CoolJohnB on 2010-07-09
I have done a lot of research on this trying to find a solution, but everywhere I look I find that this is a known Ubuntu/Linux problem!  And has been around for sometime, hopefully with the October release maybe they will solve it!?

If you or I or anyone else find a solution please post it here, that would be truly wonderful!

Does anyone know if it is any better with an external mic?

---

### Post by CoolJohnB on 2010-07-09
Well problem is now SOLVED!!!  Yes Really!!
Update manager wanted to download a new version of Skype 19MB in size, after it did so and installed.  I now have decent mic volume!  I Just made a test call and could hear myself loud and clear on the playback!  After many trials and tribulations, I am now very happy!! I  Like Ubuntu very much can't see any reason now for returning to windows!

Also really appreciate this forum it has helped in so many ways and I am sure it will continue to do so, hope the same thing works for everyone else.

---

### Post by Denz Choe on 2010-07-10
Hey CoolJohnB,
Jz to be certain, what version of Skype that is working for you right now that is giving you a decent mic volume?

---

### Post by CoolJohnB on 2010-07-10
It says Skype Beta version 2.1.0.81  Hope you can get yours working too.

---

### Post by neoargon on 2010-07-10
I had the same problem . I found the solution only yesterday.
In terminal, type alsamixer .
press F5
Increase the volume of capture to maximum
If there are two captures, increase volume of both
Change input source to Front mice or mic(for rear mic)

In alsamixer, press right of left arrow keys to navigate to capture and up or down to increase or decrease volume

---

### Post by CoolJohnB on 2010-07-10
Strange thing is the version of Skype is the same one I downloaded, so did the Update Manager find something new and install it?

Did the above with Alsamixer a while ago but made no difference for me, also can't see anywhere to change mic, probably as I only have array mic's in lid of laptop.

The only other thins I have done is to install Alsa Moduler synth and Audacity not sure if either of those has made a difference but have noticed Audacity seems to be running in the background so maybe that's doing something?

Anyway whatever it's now working which is the prime thing.  Hope any who have the same problem get it sorted also.

---

### Post by Denz Choe on 2010-07-11
Ubuntu may have included an update package for the sound issue when we ran update manager recently (dozens of updates. Don't know how to identify which one). You were right, I've checked my history, there weren't any update packages for Skype since the day I made a post on this topic. Somehow it magically got fixed! I've just only tested it. hehe. 

It would be great if an expert actually explains what was fixed :)

---

### Post by neoargon on 2010-07-11
To know whether the problem is that of skype , try recording sound using app named "sound recorder",
Can you please post a screen shot of alsamixer (after pressing F5)?

---

### Post by CoolJohnB on 2010-07-11
Tried recording in Sound Recorder and it didn't work so update seems to be only for Skype, which is all I use mic. for anyway!

Screenshot of Alsa Mixer:
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot-2.png[/IMG]

---

### Post by CoolJohnB on 2010-07-11
try Again:
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                                                                                                       F1:  Help               &#9474;
&#9474; Chip: SigmaTel STAC9205                                                                                                                               F2:  System information &#9474;
&#9474; View: F3: Playback  F4: Capture  F5:[All]                                                                                                             F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -9.00]                                                                                                                         Esc: Exit               &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9474;        &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;                                                                  &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;         &#9474;
&#9474;        &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;  &#9474;         &#9474;
&#9474;        &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;  &#9474;         &#9474;
&#9474;        &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;  &#9474;         &#9474;
&#9474;        &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;  &#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;  &#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;                                                                  &#9474;  &#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;          &#9474;&#9618;&#9618;&#9474;         &#9474;
&#9474;        &#9500;&#9472;&#9472;&#9508;          &#9500;&#9472;&#9472;&#9508;          &#9500;&#9472;&#9472;&#9508;          &#9492;&#9472;&#9472;&#9496;         Mic In         &#9484;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9488;      Digital Playb     &#9500;&#9472;&#9472;&#9508;          &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;         &#9474;
&#9474;        &#9474;OO&#9474;          &#9474;OO&#9474;          &#9474;OO&#9474;                                      &#9474;MM&#9474;          &#9474;OO&#9474;                        &#9474;MM&#9474;                                                   &#9474;
&#9474;        &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;                                      &#9492;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;         L    R                                    &#9474;
&#9474;                                                                                                                                    CAPTURE                                    &#9474;
&#9474;         81         100<>100      100<>100      100<>100                                                                 0          100<>100       50<>50        75<>75        &#9474;
&#9474;   <   Master    >  Headphone      Speaker         PCM      Mic Jack Mode    S/PDIF     S/PDIF Defaul S/PDIF Playba     Beep         Capture       Digital         Mux         &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9474;                                                                                                                                                                               &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by lidex on 2010-07-11
Can't really tell anything from that screenshot(?). It could be a number of things. First you need to make sure your mic works properly. There is a setting in skype preferences that you should disable. Something along the lines of 'allow skype to control mixer levels'. 

Some have had good results installing these drivers:
Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**.

Check alsamixer capture settings <F4> or <TAB> for input source and try toggling setting using up/dn keys. In sound preferences, the input tab, make sure the correct device is chosen and adjust level there. Gnome-alsamixer is good to have. There you can check to make sure mic boost is enabled.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

More here:
[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/]("http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/")
[https://help.ubuntu.com/community/SkypeTroubleshooting]("https://help.ubuntu.com/community/SkypeTroubleshooting")

---

### Post by CoolJohnB on 2010-07-12
Wow, thanks for that, very informative, I have Gnome-Alsamixer installed but cannot find mic boost anywhere, it doesn't seem to be in 10.4

As I now have mic working in Skype not sure whether to do those extra things or not?  Is there a way to go back to old configuration if they don't work?

---

### Post by CoolJohnB on 2010-07-12
Gave the adjustments suggested by lidex a try and would say it has improved Skype volume. 

I am now unable to check out 'sound recorder' as it says necessary plugins are missing?!  I tried ALL the methods of recording and they all say the same thing.  Not that I am too worried about that as previously mentioned I really only use the mic for Skype.

---

### Post by lidex on 2010-07-12
> **CoolJohnB said:**
> Wow, thanks for that, very informative, I have Gnome-Alsamixer installed but cannot find mic boost anywhere, it doesn't seem to be in 10.4

As I now have mic working in Skype not sure whether to do those extra things or not?  Is there a way to go back to old configuration if they don't work?

Yeah, not all soundcards will support it. You can try the other tweaks if you like but sometimes best to not push your luck if something works. Those changes can be rolled back.

---

### Post by CoolJohnB on 2010-07-13
I tried sound recorder again and it has very low volume, just as Skype used to, but I wouldn't want to fix that at the expense of Skype.

---

