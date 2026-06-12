---
title: "No Sound in Google Chrome"
date: 2009-12-08
forum: General Help
---

### Post by DedMoroz on 2009-12-08
YouTube shows the videos, but no sound. Ive had a pre-beta version (or was it alpha) of Chrome (not chromium) for the past few weeks... also without sound. Ive upgraded to the new Google Chrome Beta and still no sound. There is a link here if interested in testing...

[http://www.google.com/chrome](http://www.google.com/chrome)

Anyways, on my computer at home sound on youtube and other flash content works fine. Would anyone have any tips or recommendations? Thanks!

---

### Post by PPPP on 2009-12-11
I have the same problem...ideas?

---

### Post by Chops II on 2009-12-17
same here. FF works fine. Flash itself works fine, apart from sound.

---

### Post by akakingess on 2009-12-17
I have no problems, sound or otherwise in Chrome, but could you all post some more specs as far as Ubuntu version, hardware, etc?  I am running an AMD64 desktop with 9.10 64-bit with Google Chrome 4.0.249.43. Let me know if you want to know more about my setup, but I am not using any sound cards or anything special other than the onboard audio. So, we need to try to narrow down the possible issues if you could post what you are all running.

---

### Post by yarri on 2009-12-19
Bump! I have the same problem - Sound in flash in firefox but in chrome not even a blip. 
I have Karmic with 2.6.31-16-generic kernel. Are there other information that can be helpful?
Cheers 

Yarri

---

### Post by yarri on 2009-12-20
Here I found solution that [works]("http://happyubuntu.blogspot.com/2009/12/how-to-make-google-chrome-browser-play.html").

---

### Post by milia on 2009-12-22
> **yarri said:**
> Here I found solution that [works]("http://happyubuntu.blogspot.com/2009/12/how-to-make-google-chrome-browser-play.html").

Now, that's an elegant and fast solution !!!
Thanks!

ps: the above trick worked on a 8.04 LTS, 2.6.24-25-generic kernel.

---

### Post by victusmei on 2010-01-05
@yarri, thanks for the link. It worked flawlessly for me. Saved a lot of frustration.

---

### Post by DedMoroz on 2010-02-12
> **yarri said:**
> Here I found solution that [works]("http://happyubuntu.blogspot.com/2009/12/how-to-make-google-chrome-browser-play.html").

Thanks so much! Bye Bye Firefox!

---

### Post by victor9098 on 2010-02-15
> **yarri said:**
> Here I found solution that [works]("http://happyubuntu.blogspot.com/2009/12/how-to-make-google-chrome-browser-play.html").

Thank you! Worked perfect. Time to migrate from firefox (just too slow on a netbook)

---

### Post by cscott0108 on 2010-02-23
> **yarri said:**
> Here I found solution that [works]("http://happyubuntu.blogspot.com/2009/12/how-to-make-google-chrome-browser-play.html").

I have tried this fix, but I even renamed the old plugin folder and created the symbolic link to the new one, but it still did not work. When in a terminal I run 'sudo google-chrome' I do get sound, but the problem is before all of these upgrades sound did work with out going to the super user. I am running 64bit version of Kubuntu 9.10 any other ideas?

---

### Post by cscott0108 on 2010-02-26
> **cscott0108 said:**
> I have tried this fix, but I even renamed the old plugin folder and created the symbolic link to the new one, but it still did not work. When in a terminal I run 'sudo google-chrome' I do get sound, but the problem is before all of these upgrades sound did work with out going to the super user. I am running 64bit version of Kubuntu 9.10 any other ideas?

I just fixed my problem thanks to another post those multimedia & Video guys in that forum know their stuff.
Try this first at [Ubuntu Forums.]("http://ubuntuforums.org/showthread.php?t=789578")

But did not work for me, what I did was,
Remove the required packages

sudo apt-get remove pulseaudio

sudo apt-get install esound

Now remove the 70pulseaudio file

Before removing make a backup of this file

sudo cp /etc/X11/Xsession.d/70pulseaudio /etc/X11/Xsession.d/70pulseaudio.back

sudo rm /etc/X11/Xsession.d/70pulseaudio

[COLOR="DeepSkyBlue"]In 9.10 Kubuntu I did not have to do this.

Now go to System -> Preferences -> Sound

Make sure they are all set to ‘Autodetect’.

The only one you will have to set manually to ALSA is ‘Sound Capture’ under ‘Audio Conferencing’.

Note:-At this point Pulseaudio is now nolonger an option under these drop menus.

Gnome Sessions

Go to System -> Preferences -> Sessions

Deselected or Remove the Pulseaudio Manager[/COLOR]

I did this.
cd ~

cp .asound* /home/chris/asound\ backup/

rm .asound*

then rebooted, this solved my issue, now all of my browsers get sound with out Super User permissions.

*Note - When you remove pulseaudio or install esound, the package manager also removes the metapackage ubuntu-desktop. Don’t worry, this file is used only for upgrades between Ubuntu releases. Just make sure you install it before upgrading. If you do clean installs between releases, then you don’t need to worry about it. Nevertheless it is recommended to fix pulseaudio configuration instead of removing it.

These were found at [ubuntugeek.]("http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html")

---

### Post by puv on 2010-08-29
Check your extensions!!!! Video's and sound were working fine then after install this extension "Chrome Sounds - Version: 1.1" I got no sound so I just disable it, now all is good. I hope that works for you.

---

