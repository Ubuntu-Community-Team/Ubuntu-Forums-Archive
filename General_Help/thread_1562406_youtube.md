---
title: "youtube"
date: 2010-08-27
forum: General Help
---

### Post by limestone on 2010-08-27
Hi, this is a Debian issue but I get no answer in their forum. 

I installed gnash, gstreamer-plugins-base, gstreamer-plugins-bad, gstreamer-ffmpeg and mozilla-plugin-gnash + some other plugins. 
I'm using Iceweasel and I can't get youtube videos to work... It says "an error occurred, please try again later."
But the fun thing is that I CAN watch youtube videos on other websites :S
My friends can view vids on youtube so I guess the problem is at my end. 
Is there something else I need exept my plugins and gnash?

---

### Post by samn122 on 2010-08-27
You are supposed to have flash player 10

---

### Post by limestone on 2010-08-27
> **samn122 said:**
> You are supposed to have flash player 10

No, I'm using gnash - GNU flash player

---

### Post by kelvin spratt on 2010-08-27
Gnash is not really ready yet. 
You need to uninstall every thing to do with gnash. and install adobe flash player at this moment in time.

---

### Post by limestone on 2010-08-27
> **kelvin spratt said:**
> Gnash is not really ready yet. 
You need to uninstall every thing to do with gnash. and install adobe flash player at this moment in time.

But the website says it shall work... And I can watch youtube videos embedded on other websites..
Also, I think it worked when I installed the whole Debian system...

---

### Post by limestone on 2010-08-27
> 
[http://forums.debian.net/viewtopic.php?f=30&t=54959&p=317863#p317863](http://forums.debian.net/viewtopic.php?f=30&t=54959&p=317863#p317863)
chance2105 wrote:

Lenny, Squeeze?

This sounds like something I've experienced on squeeze.. in that case.. A way to get more youtube videos to show with gnash directly at youtube is to disallow youtube from setting cookies in Iceweasel. 

In iceweasel, click Edit -> Preferences -> Privacy, select "Use custom settings for history" if it isn't already, click "Exceptions", enter youtube.com and click Block then Close. Delete the remaining youtube cookies ("Show Cookies", search for youtube, then delete).

After doing that I get about 3/4 of videos or so to work. Other than that, you can upgrade to the newer version of Gnash that has been recently released, you can use an external commandline tool like [youtube-dl]("http://bitbucket.org/rg3/youtube-dl/wiki/Home"), or one of the various Firefox plugins that allow you to download youtube flash videos.

ChanceThat fixed the problem!

---

