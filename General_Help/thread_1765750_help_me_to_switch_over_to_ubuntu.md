---
title: "help me to switch over to ubuntu"
date: 2011-05-23
forum: General Help
---

### Post by pandurang_m on 2011-05-23
hello,
please help me to switch over to ubuntu from windows 7...

my desktop specs

motherboard: gigabyte GA-MA790XT-UD4P
cpu: amd phenom II x2 545 3.0ghz 
ram: 4gb
graphics card: nvidia gt240 
hdd: wd 1tb

presently using windows 7 64bit...
i use my desktop for browsing web, video calling, gaming, editing lots of pictures and videos, music...of course checking security for windows, updating antivirus, scanning virus for every pen drive...etc

i tried live ubuntu and installed it...
its amazing os when compared to paid os, and coming to multitasking in ubuntu i think it has some problems or i may be wrong...

below are my concerns regarding ubuntu...

1. when i play music and try to open some video or pictures to edit, music playback will be little chunky, like it stops for few seconds and again it plays...multitasking issue? 
2. no sound from hdmi connectivity...
3. can i watch hd movies with 5.1 audio?
4. can i resize display? i get option in win 7 (under nvidia control panel)
5. gaming in ubuntu?
6. heard hdd life will be more in ubuntu (because of ext4), is it true?

---

### Post by mikewhatever on 2011-05-23
1. What version of Ubuntu are you using? There were some kernel related changes in the latest version to address multitasking issues?
2. Try selecting the HDMI output under Sound Preferences.
...

5. There are games in the repositories, on [http://www.playdeb.net/](http://www.playdeb.net/), then there is wine for Windows games. That said, it's probably not going to be enough for a die hard gamer.
6. No.

---

### Post by Mr. Shannon on 2011-05-23
> **pandurang_m said:**
> hello,
1. when i play music and try to open some video or pictures to edit, music playback will be little chunky, like it stops for few seconds and again it plays...multitasking issue? 
2. no sound from hdmi connectivity...
3. can i watch hd movies with 5.1 audio?
4. can i resize display? i get option in win 7 (under nvidia control panel)
5. gaming in ubuntu?
6. heard hdd life will be more in ubuntu (because of ext4), is it true?

1. Installing the proprietary driver for your NVIDIA card may fix a lot of these issues (use ** Additional Drivers** in Ubuntu, don't download from NVIDIA).  Also make sure that the vdpau driver for NVIDIA gets installed (check synaptic or the software center).  If you want to make full use of the your graphics card when playing videos (important for HD), then you need to install **gnome-mplayer** and enable **vdpau** as the video output under preferences.  Note: installing gnome-mplayer will not make it the default video player, so you will need to do that separately.

2. Don't Know

3. HD movies, yes (given the steps in 1).  5.1, I have no idea.  And if you are talking about playing a Blu-Ray disk then I don't know, I only know that you can play HD video.

4. Yes, if you install the NVIDIA driver.  You can change screen resolution in **NVIDIA X Server Settings** once the driver is installed.  Never tried it though.

5. Look in the software center under **Games** or at [http://www.playdeb.net/]("http://www.playdeb.net/").  If you are talking about Windows games then Wine (a Windows emulator) or Play On Linux (a front end to Wine) will let you play some Windows games.

6. Don't Know, but you won't have to defragment the ext4 partition.

If you need any help with the suggestions above just ask.

---

### Post by pandurang_m on 2011-05-24
after installing Ubuntu, had some issues like

pros

1. all my desktop hardware works out of box...
2. new file system (ext4) and no worries on security...
3. all basic applications are available...
4. no issues on connectivity, even my android phone, and 3g modem works great...
5. easy to understand concept...


cons

1. no polished applications...
2. no polished games to play...(default games are no use) when compared to default games in Windows 7... 
3. music playback freezing while opening different files...(no multitasking)
4. no flash playback on Google chrome browser...

---

### Post by pandurang_m on 2011-05-24
i am using Ubuntu 11.04

---

### Post by FormatSeize on 2011-05-24
> **pandurang_m said:**
> 
 
1. no polished applications...
2. no polished games to play...(default games are no use) when compared to default games in Windows 7... 
3. music playback freezing while opening different files...(no multitasking)
4. no flash playback on Google chrome browser...
 
1. What exactly do you mean by "no polished applications?" What one person may call "polish" another may call "extraneous", so a little clarity on that would be helpful. As in, are you talking about MS Word 2010 vs OpenOffice Writer 3.2?
 
2. I can't be of much help here. As I am a hardcore gamer, but I don't use my desktop to play them. 
 
3. I haven't experienced this problem. I'm using 10.04, and it multitasks pretty well. That, too, though, is largely dependant on what you are trying to do. What are the typical tasks you are trying to perform while your music is playing? Personally, I spend most of my time in a terminal, Kate, and Bluefish, which aren't terribly demanding applications.
 
4. Do you have flash playback in any other browser(s)? If so, then that's weird. But if not, then you need to go to Adobe's website and install flashplayer from there.

---

### Post by linuxinstalledfromhdd on 2011-05-24
I don't know about these games you are talking about, because I use my computer for more important stuff than playing games on it. 

As for the rest of your issues, you would need to reinstall Ubuntu and following a guide:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Try using 10.10 since it is more stable.  Goodluck

PS you should have flash in Google. You installed it wrong.

---

### Post by mikewhatever on 2011-05-24
> **pandurang_m said:**
> ...

1. no polished applications...
2. no polished games to play...(default games are no use) when compared to default games in Windows 7... 
3. music playback freezing while opening different files...(no multitasking)
4. no flash playback on Google chrome browser...

1.Some applications are less polished then others, that's the way life is. We might be able to suggest alternatives, if you chose to reveal the details. Obviously, nothing can be done if you find that all applications are unpolished.

2. Yes, that's the area where Linux lags very far behind Windows. By the way, I didn't know there were default games in W7.

3. Multitasking doesn't mean you can do any number of things at the same time. Perhaps, whatever freezes the music is just too heavy for your computer to handle while playing music.

4. That should be easily solvable. Search the forums, or open a separate thread with a moderately descriptive title.

---

### Post by Tribis on 2011-05-24
This thread is a perfect example of why I just downloaded Ubuntu 11.04 and deleted it two days later. 

Douche bags defending and fighting that Linux is better, saying that games aren't "important", and debates as to what "polish" is. I'm a programmer and strictly a programmer, not an operating system lover - I would like to learn a new OS, but with Linux I always have to visit this forum and see an *** load of fanatic responses and awkward workarounds using terminal or by adding repositories. I've noticed that in OSX and Windows I simply find what I want and install it when I want - simple.

Do I have anything against Linux? No. I'd love to use it and learn it simply because it is free and legal to use for free, but I refuse to listen to the dbags on these boards.

---

### Post by ChrisWells on 2011-05-24
I hear a lot about apps not looking as good as Windows. I think the complete opposite. Ubuntu has a great font, and most apps look almost universally the same because of the theme. Nice big UI which is plain and simple and very very neat looking.  It looks great compared to Windows with millions of little buttons everywhere, an ugly small skinny font, and checkboxes/options everywhere. Linux is pretty minimalist compared to windows it's a matter of taste

---

### Post by ChrisWells on 2011-05-24
> **Tribis said:**
> This thread is a perfect example of why I just downloaded Ubuntu 11.04 and deleted it two days later. 

Douche bags defending and fighting that Linux is better, saying that games aren't &quot;important&quot;, and debates as to what &quot;polish&quot; is. I'm a programmer and strictly a programmer, not an operating system lover - I would like to learn a new OS, but with Linux I always have to visit this forum and see an *** load of fanatic responses and awkward workarounds using terminal or by adding repositories. I've noticed that in OSX and Windows I simply find what I want and install it when I want - simple.

Do I have anything against Linux? No. I'd love to use it and learn it simply because it is free and legal to use for free, but I refuse to listen to the dbags on these boards.

 You'll probbaly find that you will use it, delete it, go back to Windows, then go back to Linux etc etc until you finally use Linux permenently. When I very first started I was completely put off by having to enter commands etc to fix very simple problems. What you need to realise is that a) Linux is generally much more stable than Windows. I have never had a single crash, ever. and b) Terminal seems impossible to use/understand when fresh coming from Windows- stick with it for a couple of weeks / 1 month and you'll understand why it's important and it becomes easier and easier.  When I first tried Linux (Ubuntu) I had to sort a couple of problems- my keyboard would randomly freeze completely until reboot. Found out from google it was Asus atk0110 driver, so I blacklisted it and never had the freeze since. There was a couple more but when I was set up, honestly I never had a problem again. You'll learn that Linux is completely different from Windows, and usually if you've had a problem, someone else has too so it's easy to find a fix, and fixes are always coming out for things.  The pro's of using Linux far outweigh the cons, and Linux will only get better as Windows stays the same. I'd give try to stick with if it I was you- I'm glad I did. As for the software, it's easier in Ubuntu than Windows- you only ave to go to software centre for most popular programs. Repositories are only for updates so you can update everything centrally- something Windows doesn't do

---

### Post by linuxinstalledfromhdd on 2011-05-24
There are two kinds of users.  

The ones that want to learn how their computer works, runs, etc. 

And the ones that want everything done for them. 

That's why commercial software exist. 

Everything is a trade-off in life.  It's -not- about arrogant support. Or even which OS is best. 

That is all subjective and doesn't really matter in the end.  Everyone needs/wants their OS to work. 

To each his/her their own, and their way of accomplishing this feat.

---

