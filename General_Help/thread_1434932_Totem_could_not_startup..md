---
title: "Totem could not startup."
date: 2010-03-20
forum: General Help
---

### Post by Mecasickle on 2010-03-20
Hey Guys, I've been using linux ubuntu 9.10 for 3 months now, and I'm pretty used to it. I'm experiencing a problem though.

I usually just double click on any songs I have while I do some research, and all of a sudden I get this weird error message saying:

"TOTEM COULD NOT STARTUP.

Failed to create a GStreamer play object. Please check your GStreamer installation.
"

I'm like WTF!? Because I've been searching the answer for this on the web and done most of things possible out there and nothing seems to work. The wierdist thing of all is that it happened all of a sudden. Please help me out on this one guys! 

PS: Yes I do have Gstraemer installed, but how do i know if it actually "properly" installed?

Thanks!

---

### Post by garvinrick4 on 2010-03-20
> **Mecasickle said:**
> Hey Guys, I've been using linux ubuntu 9.10 for 3 months now, and I'm pretty used to it. I'm experiencing a problem though.

I usually just double click on any songs I have while I do some research, and all of a sudden I get this weird error message saying:

"TOTEM COULD NOT STARTUP.

Failed to create a GStreamer play object. Please check your GStreamer installation.
"

I'm like WTF!? Because I've been searching the answer for this on the web and done most of things possible out there and nothing seems to work. The wierdist thing of all is that it happened all of a sudden. Please help me out on this one guys! 

PS: Yes I do have Gstraemer installed, but how do i know if it actually "properly" installed?

Thanks!
It will most likely just as easy to uninstall the gstreamer package clean and reinstall.
Code: sudo apt-get purge ubuntu-restricted-extras

Then clean out cache so can fetch new software from repositorys
Code: sudo apt-get clean

Reinstall the whole package
Code: sudo apt-get install ubuntu-restricted-extras

If this does not work. Remove your Movie player (totem)  and reinstall just as easy through
Ubuntu software center since you have cleaned your cache. 

ubuntu-restricted-extras is a package of software just will be easier for you than looking
for correct codec's to reinstall.

Make sure you have know broken packages. Just for hell of it. 
Code: sudo apt-get -f install

---

### Post by Mecasickle on 2010-03-21
Hey man, 

Jsut did everything in the right order, put all the sudo commands, then uninstalled, installed again, put the final code Code: sudo apt-get -f install, but the same error still appears.

Maybe there's somethign I'm missing?? Cuz I can't really use any other media player (I downloaded some, but another ype of error appears). Another thing that might be useful, is that I think some type of error apperared due to some updates that happened in my machine as well as the new kernel. Maybe that?

Thanks for the help!

---

### Post by garvinrick4 on 2010-03-21
Can you play flash say a youtube video? Just checking on something.

Will mplayer run. install it in ubuntu software center real quick and check it out.

It will install in Applications sound and video.

---

### Post by Mecasickle on 2010-03-21
Yup, I can play youtube videos normally. However I did install the mplayer media player.

Interstingly, mplayer DOES RUN, HOWEVER, once I try to open up a music file, and click play, it does play BUT when I open an .AVI file I get the following error: 

" FATAL ERROR!

Error opening/initializing the selected video_out (-vo) device.

"

surprisingly, when I open the vidoe file, I can't acutally see the video BUT I can hear the audio FROm the video.

Andy suggestions? I'll keep you posted If I notice anythign strange.

---

### Post by Mecasickle on 2010-03-21
Just fixed the mplayer, but Movie player still looks fcked up .... =( . Other players are seeming to work perfectly so thanks for the help!

I solved the past problem with this:

Edit your .mplayer/gui.conf file and make sure that you have vo_driver line like this:
vo_driver = "x11"

The above line is the 2nd one in my file

source: [http://ubuntuforums.org/showthread.php?t=20039](http://ubuntuforums.org/showthread.php?t=20039)

Any other suggestions are welcome to fix my Movie Player, cuz probably some1 in the future will encounter a similar problem.

---

### Post by garvinrick4 on 2010-03-21
> **Mecasickle said:**
> Just fixed the mplayer, but Movie player still looks fcked up .... =( . Other players are seeming to work perfectly so thanks for the help!

I solved the past problem with this:

Edit your .mplayer/gui.conf file and make sure that you have vo_driver line like this:
vo_driver = "x11"

The above line is the 2nd one in my file

source: [http://ubuntuforums.org/showthread.php?t=20039](http://ubuntuforums.org/showthread.php?t=20039)

Any other suggestions are welcome to fix my Movie Player, cuz probably some1 in the future will encounter a similar problem.
Your welcome, have a nice day.

---

### Post by Mecasickle on 2010-03-21
Looks like the nightmare still isn't over :S

I've alwasy been using OpenCV and ARtoolkit for some research with my webcam, but now when I run Cheese, a GStreamer error just pops up!? SO apparanetly this probelm has to do with Gstreamer. 

Fortunatly the error is giving me more information on what the possible problem is.

It says this
"CHECK YOUR GSTREAMER INSTALLATION.


One or more needed gstreamer elements are missing: oggmux, videoscale, videorate, theoraenc, vorbisenc, audioconvert, gconfaudiosrc, videobalance, ffmpegcolorspace.

"

I found another thread with useful information, but still doesnt solve my problem. (Guess cuz I dont know how to add a repos to ubuntu...)

Thread: [http://ubuntuforums.org/showthread.php?t=803469](http://ubuntuforums.org/showthread.php?t=803469)

---

### Post by Mecasickle on 2010-03-22
OK, so something really funny happened. I went to my main source folder where I had all the gstreamer files and tried to reinstall everything with these commands but no luck:

make clean
./configure
make
make install

So I opened my snyaptic pack manger, and started to uninstall all the plugins that I had addded, that didn't have the ubuntu sign next to them, so I "removed them from the system. No luck either...

Hoever once I did, and after trying someother stuff, I said, 

"Hmm what If I type:

make uninstall"

And so I did type this commando in the main source folder in the terminal and it apparently"uninstalled"

oddly, when I open cheese or my bugged up media player, they work perfectly now. THis is pretty coutner-intuitive, I mean how can it work ifI appently "uninstalled it"?

So the problem is now solved, but I really don't get the solution, It's like knowing you heard a good joke but you jsut didn't laugh after the punchline.

Any explanations? Feedback?

SEe ya guys!

---

### Post by rajashekhar on 2011-06-26
Update: For anybody else who experiences this issue after updating to 11.04, the fix is to delete the folder ~/.gstreamer-0.10. After doing that, the issue should be fixed immediately without a need to logout or reboot your system. It would appear that the problem was a corrupt gstreamer configuration. Perhaps the error messages could be modified to make this more apparent?

---

