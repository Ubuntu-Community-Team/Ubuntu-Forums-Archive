---
title: "MPlayer - poor internet video"
date: 2006-04-29
forum: General Help
---

### Post by heislord5 on 2006-04-29
MPlayer is reallly really poor playing video from internet, while Realplayer does fine.  Found a previous thread that indicated that MPlayer may be using a lower bandwidth stream....How do I make it use high bandwidth?

If not, what else can I use to play windows media files from the internet.  Also, I don't know what kind of files are being played at foxsports.com, but I can't get them to come up at all even though I can get both real and windows media to play at c-span.

---

### Post by Gannin on 2006-04-29
Have you explored the MPlayer configuration window at all?

---

### Post by heislord5 on 2006-04-29
is that something I install....how do i get (to) it?

---

### Post by heislord5 on 2006-04-29
If you mean the window that you can open from the MPlayer from the applications->Sound & Video->MPlayer menu.  Select the config icon.  I don't see an option under there for this?  Are these options only for the desktop MPLayer and not the plugin.

---

### Post by reubadoob on 2006-04-29
I've "explored" the mplayer config and I still get the worst video streams I've ever seen using mPlayer. It most cases I have the shuddering low quality streams. And on top of that I keep getting the black screen within the web page but I get the video in some pop-up-like window playing at the horrible quality I just described.

---

### Post by Gannin on 2006-04-29
The MPlayer plugin uses the same settings as your regular MPlayer, which are stored in ~/.mplayer.

Have you tried adjusting the video output driver and device?

---

### Post by reubadoob on 2006-04-29
[QUOTE=Gannin]The MPlayer plugin uses the same settings as your regular MPlayer, which are stored in ~/.mplayer.

Have you tried adjusting the video output driver and device?[/QUOTE]

Not to my knowledge I haven't. Can you explain the steps needed to do so. By that I mean the steps to keep Mplayer from opening up videos in another window & the awful streams.  I'm on my brother's Windoze box right now. Won't be able to get to Ubuntu untill Monday.

---

### Post by Gannin on 2006-05-01
I've never used the built-in MPlayer or MPlayer plugins.  I've always compiled it myself from source and installed the MPlayer plugin available from the MPlayer plugin project, so I haven't had the issue with video opening in a separate window.

It sounds to me like instead of using a &#8220;regular&#8221; plugin that incorporates the information directly into the web page, you're using a plugin that takes the stream and then launches an external plugin to view it.  So, are you comfortable with compiling things from source?

As for the configuration window, you said earlier that you explored the config.  Did you mean just the config file, or the config window itself?  And just to make sure we're on the same page, if it was the config window, were there any tabs?

---

### Post by reubadoob on 2006-05-01
Well I had to re-install and now it is NOT launching another window. I checked using quicktime movie trailers. Although Mplayer is still studdering throughout the movie play. I did fiddle with the cache and % to cache. I noticed in the configuration window there is nothing selected next to Video & Audio output. Any ideas?

---

### Post by Gannin on 2006-05-01
When you open the video output drop-down, what options are you given?  If gl is one of the options, give that a try.

---

### Post by reubadoob on 2006-05-01
The optioins include:
gl
xll
xv

I tested them all on a Apple Quicktime moive trailer Alpha Dog. All were pretty jerky

---

### Post by Gannin on 2006-05-01
Can you post the location of the trailer?  I'll see if it's jerky for me too.

---

### Post by Bloch on 2006-05-01
Re: gl x11 xv options on mplayer
You can delete the option showing to get the initial blank option.
gl didn't work properly for me, though I have a Nvidia card which works properly.
The mplayer plugin is plain buggy, and makes firefox crash about once in ten. However it would be nice to know if there were any options that might make video clips more smooth. It is choppy even on a 900MHz PIII
As usual there is a lot of information on the web but it is hard to know what applies to ubuntu breezy.

Does the mplayer plugin work better on Dapper Drake?

---

### Post by reubadoob on 2006-05-02
[QUOTE=Gannin]Can you post the location of the trailer?  I'll see if it's jerky for me too.[/QUOTE]
[http://www.apple.com/trailers/lions_gate/hardcandy/large.html](http://www.apple.com/trailers/lions_gate/hardcandy/large.html)

---

### Post by Gannin on 2006-05-02
The clip plays fine for me, but then again, I always get the MPlayer plugin directly from the project's website.  I haven't had any problems with stability.  You might want to try getting it from the project's website and compiling it yourself.  It might work better for you that way.

---

### Post by reubadoob on 2006-05-02
I guess I'm going to have to. How do you compile your own though? I'm pretty new at this.

---

### Post by Gannin on 2006-05-03
Sometimes the forum doesn't e-mail me when there are new replies in a thread I'm subscribed to.  Bah.  Anyhow, the instructions.

[http://mplayerplug-in.sourceforge.net/install.php](http://mplayerplug-in.sourceforge.net/install.php)

---

### Post by reubadoob on 2006-05-03
Looks like some work. Thanks. I'll tell you how it works out or if I have any questions during the compiling.

---

### Post by Gannin on 2006-05-03
It is some work, but there is the advantage that the software will be tailor-made for your system, so you'll get the best performance from it that's possible.  That goes for anytime you compile your software yourself.

---

