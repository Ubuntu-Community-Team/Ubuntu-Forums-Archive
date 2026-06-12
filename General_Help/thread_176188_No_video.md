---
title: "No video"
date: 2006-05-14
forum: General Help
---

### Post by cssutto on 2006-05-14
I still have no decent video.

totem came with Ubuntu.

I installed VLC.

I installed Gxine

I installed MPlayer

I installed xine.

The only one that works as it should, and I don't like it, is mplayer.

I like full screen.

I can get the others to work sometimes, usually by getting mplayer running and then starting one of the others over it, then closing it.

Very impractical and not fun.

All of them start with sound, but no video.

The fact that they play correctly once I get them going tells me that I have all of the files but that there is something lacking in the way they are linked or pssibly in permissions.

Suggestions would be appreciated.

CSSJR

---

### Post by louis_nichols on 2006-05-14
Did you install the extracodecs for totem? I use totem most, with the xine engine and I like its ease of use. Gsteramer engine is ok too.

Are you using Breezy or another version of ubuntu?

---

### Post by cssutto on 2006-05-14
ver. 5.10

I have installed everything I can find, including all of the codes at Automatix.

J ust ran a serch using "libdvd" as the key and I show that libdvdcss2  is installed as well as everything else that was listed other than developer's packages.

The way it acts, I feel that everything is there except that something is not being found by the system unless it is found through the back door, so to speak.

In other words, I can start this file that is elusive with mplayer and then run most of the others, but I can't start them from scratch.  This indicates to me, although I am such a beginner at linux that it is nothing more than a wild guess, that the file is there but not available until mplayer activates it.

CSSJR

---

### Post by louis_nichols on 2006-05-14
There is no connection between all those players. mplayer and vlc come with their own set of codecs, while totem can have its own set or share the codecs that gxine also uses. You haven't told me wether you're using Breezy or Dapper or what, cause codecs are packed differently in each.

Now, mplayer works. For vlc to work, you have to go to Settings>Preferences, check "Advanced options" in the lower right, then expand "video" from the left, click on "output modules" and select something else from the dropdown. I use X11 and works. It should work for you too, but if it doesn't, just select another one until one does.

As for totem... under Breezy, totem works by installing the package totem-xine (which I recommend because it's friendlier with subtitles) and needs nothing else, or by installing totem-gstreamer and then following the instructions [here]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs"), which are also found in Breezy under System>Help. Under Dapper, you should install totem-xine plus libxine-extracodecs, or totem-gstreamer plus the iinstructions found under System>Help>System Documentation>Ubuntu Desktop Guide>Common Tasks>Multimedia Codecs.

Good luck! Hope to hear good news in your next post.

---

### Post by cssutto on 2006-05-14
Well, the joke is on me in a way.  I have been working on the wrong end of the problem.

I spent a couple of hours completely going through my setup.  I took everything I have read and been told, with the FAQ's and went through all of my files and it appears that all is installed with one possible exception, which is a file named faab.  I have files with that included in their name, but not a file with that name only.

Anyway, to the point.

For some reason, I thought to open my laptop and look at its screen.  My machine is a Thinkpad A31p, but I only look at the display on it for a few seconds during bootup.

Then I close the lid and work with my Sony LCD.  I have a Sony disply both at home and at the office.

Imagine my surprise to see the DVD playing perfectly on the laptop.

I tried all vidios and every one of them plays the way they should.

Everything else is properly displayed on the sony.  At the time I am looking at this bue hole in the screen that is supposed to be playuing a DVD, it is surrounded by the normal desktop, files on the cdrom properly displayed, etc.

So it is not a DVD files problem.  It is some sort of display problem in my equipment.

I tried the display 0,1,2 0r minus numbers and that made no difference.

I have been using an external display for quite a while and this is a first.

CSSJR

---

