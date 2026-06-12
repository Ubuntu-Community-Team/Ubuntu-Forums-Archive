---
title: "multimedia nightmare with mplayer and realplayer in Firefox"
date: 2006-06-13
forum: General Help
---

### Post by Loungefly on 2006-06-13
Hellooo,

After coming back to Linux after a break to try Dapper, I gotta say I'm impressed, but the major stumbling block I'm having is setting up embedded streaming media in Firefox using mplayer and real player.

I've searched around in different forums and when reading threads about people having problems using real player I've seen quite a few people saying things like "Why bother with  Real Player? Why not just use mplayer instead?" etc etc.  After having no luck getting them to work together I decided to start fresh. I reinstalled mplayer and the mozilla plugin, and uninstalled Real Player altogether.

The only problem I'm having now is that I can't get BBC streaming real audio using Mplayer since it opens two feeds in the same window and plays them over one another. Here's another example and I've never been able to get this to work no matter what I've tried -

[http://www.cbs.com/latenight/lateshow/](http://www.cbs.com/latenight/lateshow/)  -From there if you look under "DaveTV" and click on "Big Show Highlight" for example,  a popup appears and it should start playing the streaming real media file. I get nothing but a blank window with a broken icon. I've looked around in Ubuntu forums as well as others and have yet to find a definitive answer on how to fix this.

I had this working in MEPIS a year or so ago (out of the box if I'm not mistaken) and possibly PCLinuxOS. It irks me because in all other respects I find Ubuntu far superior to any of the other distros I've tried.

I was hoping any of you who don't have any of these issues could give me some tips, maybe share your configuration for  playing embedded streaming media with Firefox etc. It's really the only thing that's keeping me from making a clean break from Windows.

I'd appreciate any help with this.

:)

Thanks in advance.

---

### Post by sfynx on 2006-06-13
Loungefly - did you ever get a response to this? 

I've had the experience EVERY time I install Realplayer - it is never used to a real-audio related stream. If I go to real.com and click on a link to a movie, Mplayer starts. I've changed the defaults.list to reflect realpayer as the prefered app, but with no luck. The biggest problem I have (other than there should be no problem, it should just work) is that mplayer does a lousey job playing realplayer files.

Any advice?

Hint to anyone (other than loungefly) who suggests it: The answer is not 'that's crap, you need to use xyz media player'. That is not an answer.

---

### Post by Omnios on 2006-06-13
Hi ed to have similar problems with mplayer nad real player where the mplayer plug in was very agressive and over powered the realplayer for real player media. I solved this by putting the mplayer plug ins into a archive file and installing media connect firefox plug in, anyways I found t6hings to work pretty well this way as the plug in will start either the mplayer or real player counting on the media format.

---

### Post by caldevil on 2006-06-13
Well the best thing is to remove the mplayer plugin for real media files and let real handle it.

---

### Post by sfynx on 2006-06-13
How will that affect the other media types (quicktime for example)?

---

### Post by caldevil on 2006-06-13
Quicktime will work. What I am saying is remove mplayerplug-in-rm.so and mplayerplug-in-rm.xpt from your plugin directory and make sure nphelix.so and nphelix.xpt are there.

---

### Post by hanzomon4 on 2006-06-13
Setting up streaming media under linux has been hell
I got it working more often then not by compiling the latest mplayer-plugin from
[mplayer-plugin]("http://mplayerplug-in.sourceforge.net/")

Also you could look hear [scroll down to patrick295767's post]("http://www.ubuntuforums.org/showthread.php?t=157589")

---

### Post by sfynx on 2006-06-13
Caldevil - thanks! It works - RealPlayer finally appears when I select one of the rm movie links. This was such a simple solution - why hasn't this been posted before? Most of the posts I've seen reference installing a different media player.

For the record, I'm not a huge fan of RealPlayer, but for cryin out loud if it's installed with extensions, it should work.

---

