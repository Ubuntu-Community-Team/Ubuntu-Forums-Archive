---
title: "Does any thing other than Firefox work in Ubuntu"
date: 2010-03-30
forum: General Help
---

### Post by DaveMcC on 2010-03-30
Having been given a P4 computer "not running fast" had xp on it.
I decided that the time had come to improve on Microsoft so I added an extra 1gb ram downloaded ubuntu, burn off a cd and set to work loading this computer with Ubuntu
Try 1 failed, boot of disk but stalled
Try 2 failed boot off disk but full of errors.
Try 3 from within windows, yes we have Ubuntu dual boot with a fresh install of XP, looking good took it off the work bench and plugged into my KVM system. Reboot.
Err where is {Ubuntu} bit like a rabbit and hopped off the drive
Try 4 Boot up from inside windows only this time a full reformat and full install of "Bunny" {well it has hopped off once} so from now on, I shall call ubuntu Bugs after bugs bunny that well known cartoon fool. (What's up Doc)
Low and behold I now have a fully ? no! a working version of Bugs now running.
Test it on U-tube, download install plug-in all working, let the kids now on it to try it out.
Yip, bebo , facebook run A OK, and the built-in sound card works, great I can play a bit of music
At this point things start to fall apart.
Rhythm-box, it will not play any of my mp3 files that I put on the hhd, it tells me
[IMG]http://i7.photobucket.com/albums/y282/dtmcc/Screenshot-1-1.png[/IMG] but I downloaded the whole CD from Ubuntu web site
And when I try other things to download to play music I get the following message or same as.
[IMG]http://i7.photobucket.com/albums/y282/dtmcc/Screenshot-1.png[/IMG] 

Now the last thing I want to learn is a complete new language 
If bugs can not play standard mp3 files like every man and his dog has, what is the point in having a poor rated file player
And yes I have read the help files, which like MicroSoft are totally correct but bloody useless

---

### Post by mkvnmtr on 2010-03-30
If you will approach the things you do not understand one at a time and post a polite request in the forum for each one I am sure someone can help you solve them. If that is to much trouble maybe you can get xp to work on your computer.

---

### Post by DaveMcC on 2010-03-30
One would like my mp3 file to play, in (bugs),
Gstring or what ever it is called does has the same error opening no, trying to install as the above screen shot

Maybe mkvnmtr is unable to get XP to work on his computer only a polite request

---

### Post by wojox on 2010-03-30
Try installing [Medibuntu]("http://wojox.homelinux.net/?p=77")

---

### Post by Iowan on 2010-03-30
You ran MD5 check of download before you burned CD?
You burned CD at <max speed (slower=better)?
You checked disk integrity before install?

BTW, Bugs tends to make a fool out of Elmer, the martian, or Daffy. He generally comes out on top...

---

### Post by ricyaun on 2010-03-30
Try this.  Put the CMOS jumper to clear.  Pull the battery. Give the capacitors a chance to discharge.  About 10 minutes.  Put the battery back in, and leave the CMOS jumper in clear.  Wipe the hdd (not hhd), and then try to reinstall Jaunty.  Once installed if still unsatisfactory then look to Synaptic Package manager for a solution, but first be sure to update the OS.  Perhaps the latest version Karmic Koala will work better.  Always be sure to update first.

---

### Post by 2hot6ft2 on 2010-03-30
> **Iowan said:**
> You ran MD5 check of download before you burned CD?
You burned CD at <max speed (slower=better)?
You checked disk integrity before install?

BTW, Bugs tends to make a fool out of Elmer, the martian, or Daffy. He generally comes out on top...
+1
The rhythmbox error looks strange but amarok is better, and ryhthmbox will say you need a codec when it finds a corrupt file while amark doesn't.
The second error pic is about an .exe or an .exe.zip so it's for windows so unless your trying to run it in wine it's irrelevant since you just aren't installing the linux way and trying to install as if it were windows.

To play mp3s you need the codecs no big deal and to keep from asking how to play other things later let's just do it all at one time.

I could spend a half hour saying go here click this open that  yada yada yada, instead do this with just 4 lines in the terminal.

Open a terminal
Applications > Accessories > Terminal
Copy and paste these commands one at a time into the terminal and hit Enter after each.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
You will have to enter your password which wont be displayed just type it in and hit Enter

To remove any browser media player plugins you currently have installed to prevent conflicts (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) we'll get rid of rythmbox to and replace it with amarok while we're at it.
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc rhythmbox
```
then for all the multimedia, mp3's java, divx web player, flash and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer vlc amarok
```
Use the Tab and arrow keys to agree to the Java terms of use.

And to get rid of one package in the restricted extras that causes problems
```
sudo apt-get purge ttf-mscorefonts-installer
```
ttf-mscorefonts-installer bug report
[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

And you're done.
We've made quite a few changes so you may want to reboot, or Logout and back in.

Amarok for the music player is in
Applications > Sound & Video > Amarok
For playing videos VLC Player will be in
Applications > Sound & Video > VLC

Now if you really want Rhythmbox back run
```
sudo apt-get install rhythmbox
```
:popcorn:

---

### Post by wirelessmonkey on 2010-03-31
> **ricyaun said:**
> Try this.  Put the CMOS jumper to clear.  Pull the battery. Give the capacitors a chance to discharge.  About 10 minutes.  Put the battery back in, and leave the CMOS jumper in clear.  Wipe the hdd (not hhd), and then try to reinstall Jaunty.  Once installed if still unsatisfactory then look to Synaptic Package manager for a solution, but first be sure to update the OS.  Perhaps the latest version Karmic Koala will work better.  Always be sure to update first.

Dude.... While your concerns are legitimate, there are very very very few MBR / BIOS exploits in the wild, and bringing it up in all these threads is adding fear and doubt where it is most definitely not needed.

MBR viruses have to fit into 466 disk blocks, which is not much, considering they have to do normal MBR functions as well.

BIOS vulnerabilities are specific to hardware, and require ring (1) access, i.e. root, and often custom software to flash them.  If these requirements have been met, pulling the CMOS reset jumper will do nothing, as it will have already been FLASHED.

Please don't add scare tactics to legitimate concerns.


WirelessMonkey

---

### Post by uRock on 2010-03-31
> **ricyaun said:**
> Try this.  Put the CMOS jumper to clear.  Pull the battery. Give the capacitors a chance to discharge.  About 10 minutes.  Put the battery back in, and leave the CMOS jumper in clear.  Wipe the hdd (not hhd), and then try to reinstall Jaunty.  Once installed if still unsatisfactory then look to Synaptic Package manager for a solution, but first be sure to update the OS.  Perhaps the latest version Karmic Koala will work better.  Always be sure to update first.

Please stop posting like this. It does not help.

---

### Post by dcstar on 2010-03-31
> **DaveMcC said:**
> Having been given a P4 computer "not running fast" had xp on it.
I decided that the time had come to improve on Miro-Shaft so I added an extra 1gb ram downloaded Ubuntu, burn off a cd and set to work loading this computer with Ubuntu
Try 1 failed, boot of disk but stalled
Try 2 failed boot off disk but full of errors.
.......

Boot off the Ubuntu CD and run the memtest option.

Linux pushes hardware much harder than Windows and it is quite possible your hardware may not be up to the job.

---

### Post by Rasa1111 on 2010-03-31
> does anything other than firefox work in Ubuntu"?

 yes, everything works.

---

### Post by cariboo on 2010-03-31
> **ricyaun said:**
> Try this.  Put the CMOS jumper to clear.  Pull the battery. Give the capacitors a chance to discharge.  About 10 minutes.  Put the battery back in, and leave the CMOS jumper in clear.  Wipe the hdd (not hhd), and then try to reinstall Jaunty.  Once installed if still unsatisfactory then look to Synaptic Package manager for a solution, but first be sure to update the OS.  Perhaps the latest version Karmic Koala will work better.  Always be sure to update first.

Please quit advising people to do a clean install when they run into problems, there is always a way to solve a problem without a reinstall.

---

