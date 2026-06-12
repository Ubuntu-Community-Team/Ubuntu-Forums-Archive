---
title: "Help playing Flash Video"
date: 2009-10-09
forum: General Help
---

### Post by GabrielsHorn314 on 2009-10-09
Hey guys,

    I have had this problem for a while now, but it is just getting too annoying to have to deal with it. Any time i try to watch a flash video it wont load. I can imagine why it would do this, and it doesn't matter what kind of web browser I use (I use firefox and opera). I have all the add-ons necessary to play them so that isn't it. I can watch anything I download through VLC so it's not that I cant play any video at all. Any advice would be really helpful. Thanks a lot.

---

### Post by spiderbatdad on 2009-10-09
have you installed the package ubuntu-restricted-extras or adobe-flashplugin via synaptic package manager?

---

### Post by GabrielsHorn314 on 2009-10-09
Yes. I included the screenshot.

---

### Post by gdonwallace on 2009-10-09
You may also want to install swf.  In synaptic do a quick search for firefox.  You will need to scroll down a bit, but you will find an installer for swf.  This is a linux plugin to play windows media files and other online file formats.  I have found that having both the non-free flash plugin and this one fixes my problems.

---

### Post by GabrielsHorn314 on 2009-10-09
Already installed.

---

### Post by GabrielsHorn314 on 2009-10-09
I also put my current mozilla add-ons to the left so anyone can see if something may be wrong there.

---

### Post by GabrielsHorn314 on 2009-10-09
Does anyone have any ideas? 
I can see vids on sights like youtube, but can't see anything on nearly any other site. Flash games are also out...

---

### Post by GabrielsHorn314 on 2009-10-10
Unsolvable?

---

### Post by delcypher on 2009-10-10
I think your issue is that you're using an old version of flash. You're using flash 9.0 rc999 (according to your screen shot). I'm using 10.0 rc32 . I don't have the swfdec-mozilla package installed and I can play any flash content fine. My guess is you don't need swfdec-mozilla so I think you should remove it and reinstall flashplugin-nonfree

To do that close firefox and then run the following in the terminal (Applications > Accessories > Terminal):

```

sudo aptitude remove swfdec-mozilla
sudo aptitude install flashplugin-nonfree

```

Let us know how you get on!

---

### Post by GabrielsHorn314 on 2009-10-10
Ok, I uninstalled the swf, but I already had the nonfree. here's my terminal screen afterwards.

---

### Post by GabrielsHorn314 on 2009-10-10
delcypher, you sir are a genius. After the uninstall I could play flash off the site I usually have problems with. I will check others to make sure it works for everything, but in the time being, it seems like a fix. Thanks

---

### Post by delcypher on 2009-10-10
No problem, nice terminal background by the way. Where did you get it from?

---

### Post by jawkyn on 2009-10-10
I just want to say that I have the same problems as GabrielsHorn314.  I am using Ubuntu 9.04 and get a lot of emails with WMV, MPG and PPS files attached.  The PPS files will open with OpenOffice.Org and I can view them with no trouble.  The WMV and MPG files will not open using either Totem or VLC player.  The players will appear on the desktop but when I click on the WMV/MPG file, the player just vanishes.  I have read this thread with interest and have followed all recommendations, i.e., Ubuntu-restricted extras and flashplugin-installer, flashplugin-nonfree, and flashplugin-nonfree-extrasound are all installed according to Synaptic. 

To further add to the mystery, I am using PCLinuxOS Gnome 2009 on another desktop computer.  I have had it for seven or eight months, keep it updated, and it runs without problems. AND...I don't have any problems playing WMV files.  
    
    What could be the problem?  I'm not trying to bash Ubuntu, just trying to understand what is going on.  Could it be hardware problems on this computer?  Several months ago I got rid of Windows XP on this computer (Dell Dimension 4600) and installed Linux.  It worked OK with Windows, I just decided to make the switch.

This is frustrating.  Makes you want to buy an iMac and try them.

---

### Post by delcypher on 2009-10-10
@jawkyn - You're not having the same problem as GabrielsHorn31 as flash player has nothing to do with being able play .wmv or .mpg files.

The problem is most likely that you do not have the right video codecs installed. I advise you install the w32codecs (w64codecs if you use a 64-bit version of ubuntu).

I don't think that package is available in the normal repositories so you will need to add the medibuntu repository ([http://www.medibuntu.org/]("http://www.medibuntu.org/")). Instructions are available here : [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Once you've added the repository run the following in the terminal:
```
sudo aptitude update ; sudo aptitude install w32codecs || sudo aptitude install w64codecs
sudo aptitude install gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-good

```

This should install most proprietary codecs you need to view most videos.

Now try viewing your videos.

The other possiblity is that your video drivers or settings are not setup properly.

1. run in your terminal
```
gstreamer-properties
```

and click on the video tab and try different video plugins and see if your videos will play.

2.
I've had problems with VLC playing videos if the wrong video output mode is set.

Run vlc in the terminal as well (just type vlc) as error messages will be shown there.

Once in vlc experiment with different video modes (Tools > Preferences , then click on video button). Try openGL, xV maybe?

There are other possibilities but these are the easiest to do. You could have incorrectly setup video drivers but that's a little complicated.

---

### Post by GabrielsHorn314 on 2009-10-10
delcypher, i can email u the pic if u want it. How do i change this thread to solved? thanks again for the help.

---

### Post by jawkyn on 2009-10-10
delcypher, I followed your directions as well as I could and here are the results.  The Synaptic Package Manager has two entries for the codecs:  w32codecs and non-free-codecs.  I installed them both from Synaptic, then, with the terminal, added the Medibuntu repository as per instructions from the help.ubuntu.com website.  I see from Synaptic that libdvdcss2 and libdvdread4 also appear as installed, if that means anything.  But all this didn't make it work. After running vlc in the terminal though, I changed the setting from Default to OpenGL video output and the VLC media player will now play WMV and MPG files.  The Totem Movie Player still refuses to handle them.  So, thanks to you, one of the two players is working.  Do you have any other suggestions?  And even if you don't, I really appreciate your help with this.

---

### Post by delcypher on 2009-10-10
@GabrielsHorn314 - To change the thread to solved near the top of the page click "Thread tools" > "Mark this thread as solved"

@jawkyn - Make sure all the totem stuff is installed
```
sudo aptitude install totem-plugins totem-plugins-extra totem-common totem-gstreamer
```

Did you try running gstreamer-properties and playing around with the video settings?

As an extra note I hate totem, have you tried using SMplayer? Best video player for linux I have ever used

to install run
```
sudo aptitude install smplayer
```

You will probably need to configure video again to get good performance, but it's an awesome media player (it's actually a front-end for mplayer, so mplayer is the awesome media player, but SMplayer makes it more awesome).

You won't need to run vlc through the terminal again, that was just to see if any error messages popped up.

---

### Post by jawkyn on 2009-10-10
delcypher, I believe I've got it working, although I've got my fingers crossed for luck.  I followed your suggestion in your second reply and used the terminal to install totem plug-ins.  I also installed smplayer.  And I tried again running the gstreamer-properties from the terminal.  I had tried that several times before.  I tried it yet again, changing the default output plugin from Autodetect to Custom.  This time it worked.  I now have Totem and VLC players working but the sm player isn't working yet.  I also installed RealPlayer from Synaptic but it is doing the same thing that Totem was doing before.  So, while I'm not sure exactly what did the trick, I can now view the WMV and MPG videos.  I'm glad for another reason that Totem is working -- it is the default movie player and I haven't found a way to change the default from Totem to VLC.  Now I don't suppose I need to.  Again, I really appreciate your help.

---

### Post by tars_ac on 2009-10-10
Have you tried preferences, preferred applications?

---

### Post by jawkyn on 2009-10-11
Hello tars_ac.  I had, on another occasion, used 'preferred applications' to switch email clients from Evolution to Mozilla Thunderbird.  Also, since I have Firefox and Opera installed, they both appear in the drop-down menu.  
    
    Frankly, I had never paid attention the multimedia tab.  I had 'Yahoo searched' changing the default media player but I didn't get an answer that I could use.  Now that I am studying it, I see that the drop-down menu under the multimedia tab only contains three choices -- Rhythmbox music player, Totem movie player and Custom.  Applications--->Sound and Video from the panel shows that I have much more installed, including VLC media player, RealPlayer 11, MPlayer movie player, SMPlayer, Gnome MPlayer, etc. 
    
    I'll have to find a way to get these to show up in Preferred Applications so that I can switch between them.  Thanks for the suggestion.

---

### Post by tars_ac on 2009-10-11
I think with the custom option, you can enter

```
vlc %f
```

and that should do it.  I haven't tried this myself, so apologies if it doesn't work.

---

### Post by delcypher on 2009-10-11
To change the list of programs (including the default) that can be used when opening it, right click the file and click properties. Select the open with tab and choose you program.

---

### Post by jawkyn on 2009-10-11
> **delcypher said:**
> To change the list of programs (including the default) that can be used when opening it, right click the file and click properties. Select the open with tab and choose you program.


delcypher, I don't understand your instructions.  Are you referring to Preferred Applications-->Multimedia tap?  If so, I can't right click on anything and make it do anything.  Can you throw that at me again please?

---

### Post by wojox on 2009-10-11
What he was saying is find a file you want to play in VLC and right click it and choose Properties > Open With and select your VLC

---

### Post by jawkyn on 2009-10-12
OK, I see what you are saying now.  Yes, that can be helpful.  Thanks to all of you for your help in this exchange.  I learned a lot although I'll have to admit that much of it was "monkey see, monkey do" on my part.  
    
    Back in mid-September I had a problem with Windows XP and made a deliberate decision to leave MicroSoft, hopefully permanently.  I had already made the decision to never purchase Windows Vista and I stuck with that.  I realize that Windows 7 will be for sale in a couple of weeks but Ubuntu is doing everything I want it to do for now and if I can keep it that way, I see no reason to ever buy any expensive Microsoft products ever again.  I like the idea of open source, although I'm not going to be a fanatic about it. 
    
    I'm starting to really like Ubuntu, but I'm also wondering why the developers don't put more 'out-of-the-box' conveniences into it.  What I mean is, all these codec problems that we've been working on here worked in PCLinuxOS Gnome right out of the box.  Also, PCLinuxOS has Firefox 3.5 whereas Ubuntu still gives us 3.0.something as the default.  I guess every distro has its good and bad points.  I, for one, don't like the idea that PCLinuxOS is a rolling distro. 
    
    This forum at Ubuntu is a very helpful tool in keeping Windows at bay.  Thanks again for your help.

---

### Post by matey3 on 2009-10-12
delcypher;
Thanks a lot, I got mine fixed too by removing that add on.(the 1st line to remove, the 2nd like to add messed it up again so I removed it lol)anyway...
is this what you wanted?

---

