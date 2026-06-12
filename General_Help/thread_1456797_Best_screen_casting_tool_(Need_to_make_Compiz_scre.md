---
title: "Best screen casting tool (Need to make Compiz screencast)"
date: 2010-04-17
forum: General Help
---

### Post by Andy06 on 2010-04-17
I am looking to make a Compiz effects video to demonstrate to friends.

Need something with adequate frame rate, audio recording and preferably, annotation.

Tried Istanbul and that just refuses to work and freezes comp with both cores maxed out to 100%.

gtk-Recordmydesktop does the video part well but falters with the audio. The background sound even at 20% quality comes out jumbled and fast forwarded in places

Thanks a lot

---

### Post by chris.jericho on 2010-04-17
Use camtasia studios using Wine

---

### Post by Andy06 on 2010-04-17
Really :D?

I'd have preferred a non Wine app but I'll give it a shot. But Camtasia is a paid app right? I can't use it for more than the trial period.

---

### Post by chris.jericho on 2010-04-17
then there are many other great free desktop capture tools... available on windows... you can check anyone of them and then download and run it using wine

---

### Post by Andy06 on 2010-04-21
I would prefer a native linux app.

I've done the research. Have tried Camstudio, Gtk, Istanbul and 4-5 more obscure ones. Also tried the Fx Add On Capturefox and two online screen recorders but none of them give satisfactory results.

If anyone has any recommendations, that would be very helpful :)

---

### Post by robbiefarai on 2010-08-15
This screen cast explains your audio problems I hope...
[http://www.youtube.com/watch?v=pz8ejjS-bwo&feature=related](http://www.youtube.com/watch?v=pz8ejjS-bwo&feature=related)

---

### Post by ApocalypeX on 2010-08-15
I use XVidcap Screen capture its available in the software centre.

---

### Post by Gyanos422 on 2010-08-31
> **ApocalypeX said:**
> I use XVidcap Screen capture its available in the software centre.

How is that working?  Does it give good features?  Audio isn't a huge requirement for me, but the in depth editing is. I like the zooms, the callouts, and the simplicity of learning that Camtasia offers.  

To those who have used Camtasia with WINE how has that been working for you? is it smooth? i'm not working with the fastest computer but its no slouch either.  It runs Camtasia just fine when i boot into WinXP but i'd like to use Linux to show stuff instead of using a vm.

---

### Post by ebharv on 2010-11-19
> **Andy06 said:**
> I am looking to make a Compiz effects video to demonstrate to friends.

Need something with adequate frame rate, audio recording and preferably, annotation.

Tried Istanbul and that just refuses to work and freezes comp with both cores maxed out to 100%.

gtk-Recordmydesktop does the video part well but falters with the audio. The background sound even at 20% quality comes out jumbled and fast forwarded in places

Thanks a lot

Most Ubuntu screen-casters use gtk-recordMyDesktop or XvidCap.  As with anything your set-up will be the most determining factor as far as performance goes. 

For instance my first screen-casts ([**[COLOR="Blue"]_learnitwithlion_[/COLOR]**]("http://www.youtube.com/learnitwithlion")) were recorded at 10fps with gtk-recordMyDesktop. Then I was running 512MB 9800GTs in SLI on 5GBs of DDR2 with Compiz enabled. The recordings were done at 1680x1050. Later on I reduced the size of the recording window to about 1280x720 and I could get 15fps.

Now (thanks to ATI fixing their drivers) I can record at 30fps 1080p using a 1GB 5850HD on 8GB DDR3 with Compiz enabled.

Things to note if using gtk-recordMyDesktop.
- Make sure "Full Shots Every Frame" is checked if running Compiz. This reduces the artifacts. Watch some of [**[COLOR="blue"]_these_[/COLOR]**]("http://www.youtube.com/learnitwithlion") and you'll see what I'm talking about.
- Do not compress while recording. This will slows down the system.
- Using quick subsampling will get better fps but worse video quality.
- Reducing video quality with slider will get better fps.
- Reducing (or eliminating) audio recording quality will get better fps.
- Reducing recording window size will get better fps.

I'm sure the last one isn't an option since you want to make a Compiz video though.

Hope this helps.

---

