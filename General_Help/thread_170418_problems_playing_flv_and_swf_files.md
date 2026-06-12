---
title: "problems playing flv and swf files"
date: 2006-05-04
forum: General Help
---

### Post by mentus on 2006-05-04
hi all

can please somebody help me with the problems i am having to play the flv and swf files?
i have already installed various audio and video codecs, so i can play the flv videos in the totem player, but there is no audio trace, so i can't hear the voice. which codecs am i still missing?
concerning the swf files, i can't open them at all. no video, no sound...

thanks for any kind of help

mentus

---

### Post by chicken101 on 2006-05-07
[QUOTE=mentus]hi all

can please somebody help me with the problems i am having to play the flv and swf files?
i have already installed various audio and video codecs, so i can play the flv videos in the totem player, but there is no audio trace, so i can't hear the voice. which codecs am i still missing?
concerning the swf files, i can't open them at all. no video, no sound...

thanks for any kind of help

mentus[/QUOTE]

May I suggest kaffeine player? It's easier to change the codecs you're using.
> sudo apt-get install kaffeine

Go to the mplayer website and download the "essential codecs package", these include win32 codecs (for avi, wmv, divx), or you could get one that has all of them, whatever you wish.  

Go into kaffeine and go to (settings->choose xine paramenters->decoder), change the win32 driver to whereever you dloaded them to.  It should now play anything.  

Cheers.

---

### Post by mentus on 2006-05-07
hi
i have  installed kaffeine and downloaded / unpacked the "essential codecs package".
the problem is that i can't find (settings->choose xine parameters->decoder) in the menu. do i possibly have installed different version of kaffeine? starting kaffeine for first time gave a message regarding installation: some problems with the "kaffeine part"... does it maybe have something to do with that?

thanks for help

---

### Post by chicken101 on 2006-05-07
Mhhhh.  In the kaffeine menu it's settings->xine engine parameters (this opens another page) then click on decoder on the side of the page that just opened.

Perhaps xine isn't installed?  (although it should have installed xine with it, because kaffeine is simply a gui frontend for xine).  

> sudo apt-get install xine

Try that, see if it's installed right.  Also, try looking for usr/lib/win32  (since I believe you should already have the win32 codecs installed).  If you find them, go to kaffeine and add "/usr/lib/win32" (or wherever they are) to the external win32 codecs path option.  

Restart kaffeine, and then it should work.

Cheers!

---

### Post by mentus on 2006-05-07
hi

xine-ui is already installed on my ubuntu. in kaffeine, in the settings menu there is <Gstreamer engine parameters> instead of <xine engine parameters> and Player engine is set up to <GstreamerPart>. i think herein could be the problem...
what should i do next?

thanks

---

### Post by chicken101 on 2006-05-07
[QUOTE=mentus]hi

xine-ui is already installed on my ubuntu. in kaffeine, in the settings menu there is <Gstreamer engine parameters> instead of <xine engine parameters> and Player engine is set up to <GstreamerPart>. i think herein could be the problem...
what should i do next?

thanks[/QUOTE]


Ok, don't quote me on this, but I think most multimedia players in ubuntu use whatever totem is using.  By defualt totem uses gstreamer (which is a piece of garbage in my opinion).

> sudo apt-get remove totem-gstreamer
> sudo apt-get install totem-xine

That will change the defualt gstreamer to xine, then you can follow the directions I gave above.

Cheers!

---

### Post by mentus on 2006-05-08
hi

something very interesting.... i tried to follow your instructions and i post you here my terminal output, which indicates that i am supposed to have already done what you are asking me to do...


mentus@ubuntu:~$ sudo apt-get remove totem-gstreamer
Reading package lists... Done
Building dependency tree... Done
Package totem-gstreamer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mentus@ubuntu:~$ sudo apt-get install totem-xine
Reading package lists... Done
Building dependency tree... Done
totem-xine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


greetings

---

### Post by mentus on 2006-05-10
any idea what to do next?

greetings

---

### Post by Steve S. on 2006-05-28
[QUOTE=mentus]any idea what to do next?

greetings[/QUOTE]

Hey, mentus, I noticed this and just happened to see your post while I was messing with playing flv files with kaffeine.

I went into Synaptic package manager and looked up kaffeine.  It just so happened that I had kaffeine gstreamer and kaffeine xine versions installed.  I removed the gstreamer one and reinstalled kaffeine and kaffeine xine versions.  Then after a reboot and some coercion, I got kaffeine to run as chicken101 was describing.  I already had the win32 codecs installed so xine picked that up and kaffeine in turn picked that up.

So, now I can play flv/flash files with kaffeine.  HOWEVER, I still can't get the sound to work (same problem in totem with flv files).  Anyone have any ideas how to fix THAT?

---

### Post by mentus on 2006-05-29
[QUOTE=Steve S.]Hey, mentus, I noticed this and just happened to see your post while I was messing with playing flv files with kaffeine.

I went into Synaptic package manager and looked up kaffeine.  It just so happened that I had kaffeine gstreamer and kaffeine xine versions installed.  I removed the gstreamer one and reinstalled kaffeine and kaffeine xine versions.  Then after a reboot and some coercion, I got kaffeine to run as chicken101 was describing.  I already had the win32 codecs installed so xine picked that up and kaffeine in turn picked that up.

So, now I can play flv/flash files with kaffeine.  HOWEVER, I still can't get the sound to work (same problem in totem with flv files).  Anyone have any ideas how to fix THAT?[/QUOTE]

hi steve

thanks. it worked out. i got the movies play except the ones encoded in Flash 8+. unfortunately majority of my videos are like that. haven't found a solution till now... any idea?

i have problems with sound too. for flv files, no sound at all and for wmv files sound is breaking permanently...

mentus

---

### Post by Steve S. on 2006-05-30
[QUOTE=mentus]hi steve

thanks. it worked out. i got the movies play except the ones encoded in Flash 8+. unfortunately majority of my videos are like that. haven't found a solution till now... any idea?

i have problems with sound too. for flv files, no sound at all and for wmv files sound is breaking permanently...

mentus[/QUOTE]

The best I can offer is what I posted on this thread:
[http://ubuntuforums.org/showthread.php?t=139166](http://ubuntuforums.org/showthread.php?t=139166)
I had to convert to mpeg files then I could hear everything and it ran great.  Pretty easy to convert once you get the hang of it.

As far as the wmv, change which media player you are using (I love mplayer, but occasionally kaffeine gets some that mplayer won't) and make sure you have all the win32 codecs (check out synaptic; those codecs make it all run smooth for the wmv's).  Wish you well!

---

### Post by cvmostert on 2006-10-10
Here is another option that will help.
[http://www.linux.com/article.pl?sid=06/08/22/2121258](http://www.linux.com/article.pl?sid=06/08/22/2121258)

ciao

---

