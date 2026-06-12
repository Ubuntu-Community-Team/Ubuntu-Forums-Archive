---
title: "3 MAJOR Problems"
date: 2010-06-25
forum: General Help
---

### Post by ZenTrinity on 2010-06-25
Ok so I am a total newbie at Ubuntu Linux and I'm having problems I don't know how to solve.

1.) Up until yesterday this wasn't a problem, but after a power outage while I was connected I am now unable to connect to the internet anymore as it says "Networking is disabled", how do i enable the "networking"?

2.) Another problem I am having is that I am not able to dim the screen in order to save power among other uses, I've looked around but haven't been able to find a solution, I am running ubuntu on a Gateway M-Series Laptop.

3.) Finally, since installing linux I have been unable to listen to music or any other sounds through headphones or speakers, when i connect something into the audio output, the outer speakers do shut off but no sound is emitted through the speakers/headphones, and yes i have tried multiple ones to make sure it wasn't the headphones or speakers.

If someone could please help me as soon as possible with these problems I would really appreciate it, anything you need to know just ask.

---

### Post by jbrown96 on 2010-06-25
1) post output of ```
ifconfig
``` Right click on your network icon and "enable networking"

2) I don't have any good ideas.

3) Your headphone channel is probably muted. Try running ```
alsamixer
``` and see if there is a headphone channel and unmute it with "m". Otherwise dig around in System->preferences->sound or in the sound icon by the clock to add channels. Look for the headphone channel and try to unmute it or raise the volume.

---

### Post by Deadite81 on 2010-06-25
This guy says a program called "xcalib" is good for screen dimming.

His video is [here]("http://www.youtube.com/user/gotbletu#p/search/13/A9xsvntT6i4").  (I've never tried it.)

---

### Post by lukashjanssen on 2010-06-25
first of all, I'd like to welcome you to the Ubuntu Forums community. it's a grand place, where there are almost always people who can help you. I don't know how to fix all your problems for certain, but I'll give you some suggestions, and hopefully a more experienced user will stop by later:

1) On the upper Panel there should be a notification icon for your internet (symbol should be either two black monitors or a wireless icon). If you right-click that, there should be an option "Enable Networking."

2) The easiest way I know to change monitor brightness is to right click on an open area of a Panel and hit "Add to Panel." Seclect "Brightness Applet" and hit "Add." You should then be able to hit the Brightness Applet and adjust brightness. Also, under System->Preferences->Power Management you'll find other options for save power.

3) I'm not sure why your audio isn't functioning. I'll give you the same suggestion: Under System->Preferences->Sound make sure that all 3 of the "Sound Playback" are set to whatever you're trying to use.

I hope these suggestions could help any. A suggestion for future posts would be to include your Ubuntu version (Karmic, Lucid, Jaunty). Forum tips are at [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475).

In case you need it, information about the Terminal is at [URL="https://help.ubuntu.com/community/UsingTheTerminal"]https://help.ubuntu.com/community/UsingTheTerminal
[/URL]

---

### Post by ZenTrinity on 2010-06-25
Ok so for some reason the internet network decided to work again, so I am now able to connect to the internet, but thanks for the tips.

Secondly, I've tried all the suggestions with the exception of that youtube video but still haven't been able to find a solution, I've looked around and see that it might just be an incompatibility with Gateway laptops and Linux concerning screen dimming, but any other suggestions would be welcome.

Lastly, I've looked at all the preferences and still am without a solution. All the sounds are at 100 and not muted, sound plays through my laptop speakers but once i plug in headphones, I cannot hear anything in the headphones, are there any other suggestions for this?

In addition, I have recently realized I overwrote both drives on my laptop to be linux (i partitioned the drive to run both windows and linux on the same computer) but instead ended up rewriting linux on both partitions, this means I have lost all the files (mainly just pictures) i had saved, I have tried recovering using photo rec and saving the recovery to my external hardrive, but the process keeps getting killed and I do not know what I am doing wrong or even if I am saving to the right drive (when i use the command "df -h" it shows my external as named "/media/FreeAgent Drive" but when i use photorec there is no such place only "/media/sdb1" which i assume is it since in the beginning it shows up as "/dev/sdb1", I am extremely confused and would love for any light to be shed on this matter, if you require anything whether it be screenshots or info please let me know asap.


Also I have included my ubuntu version on the left under my username, it is 10.04 Lucid Lynx, running on a Gateway M-Series Laptop, model number: W650I.

Thank you for all the support, it means a lot.

---

### Post by slooksterpsv on 2010-06-25
1. Fixed, ok skipping, they gave fixes above =P

2. Dim function on gateway is Fn + Down Arrow key - that's how I dim mine (brighten is Fn + Up Arrow key)

3. I had to modify a file to get my sound to work on my Gateway NV53, here's what lines I added to /etc/modprobe.d/alsa-base.conf:
```


options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes


```

Let me know if that helps.

---

### Post by walt.smith1960 on 2010-06-25
This applet has a problem on my Asus 1005HA.  After adding it to the upper right panel, I have to left click the applet to make the slider appear, then **right** click it, then left click outside the panel.  Now the applet slider should dim the screen.  Weird, but it works for me.  This is on an install that was upgraded rather than clean install.  That may enter into it, I don't know.

---

### Post by ZenTrinity on 2010-07-09
Thanks for the tips I plan on working on the dimness and sound soon, and I was wondering if you could explain what you meant by adding lines
*Newbie here*

The most pressing issue I have right now concerns PhotoRec, does anyone have experience using the program? I know how to work it, but the thing is I am trying to recover all my photos from my laptop (accidentally overwrote the windows partition with linux), and i want to save them to my external harddrive, the problem is I can't exactly find my external harddrive in the program to save it too, when I look it up it says that the drive should be named FreeAgent Drive, but that name is nowhere to be found in the media folder, and when I try to run the program to recover my pictures to what I think is my harddrive, it just kills itself...i don't understand what I'm doing wrong, can anyone help me?

---

### Post by slooksterpsv on 2010-07-11
> **ZenTrinity said:**
> Thanks for the tips I plan on working on the dimness and sound soon, and I was wondering if you could explain what you meant by adding lines
*Newbie here*

The most pressing issue I have right now concerns PhotoRec, does anyone have experience using the program? I know how to work it, but the thing is I am trying to recover all my photos from my laptop (accidentally overwrote the windows partition with linux), and i want to save them to my external harddrive, the problem is I can't exactly find my external harddrive in the program to save it too, when I look it up it says that the drive should be named FreeAgent Drive, but that name is nowhere to be found in the media folder, and when I try to run the program to recover my pictures to what I think is my harddrive, it just kills itself...i don't understand what I'm doing wrong, can anyone help me?

Sometimes you have to open the drive in Nautilus first (file manager). I know my drive on my big computer asks me for a password when I open the drive in Nautilus, only asks once and then once I open it it works fine for everything else. Try that.

---

