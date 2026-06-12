---
title: "After the 9.10 install"
date: 2009-10-29
forum: General Help
---

### Post by DeMus on 2009-10-29
I installed 9.10 using the alternate CD because I use a RAID configuration. Most things seem to work well:
[LIST=1]
[*]I could very easily install the nVidia driver
[*]flash was installed in Firefox already, although I have a feeling it is because I was putting my home folder back where it belongs
[*]Karmic is very fast in shutting down, booting takes a bit longer though.
[/LIST]
There are however some issues I have:
[LIST=1]
[*]Whenever I start a mediaplayer, or a flash movie in Firefox, I hear a loud click coming from my loudspeakers. Is it possible to make it stop doing that by some setting, or is it simply a bug?
[*]Where can I switch off the 60 seconds delay when I want to shutdown or restart? It used to be in the preferences of the button. Why is it there anyway? Who wants to wait after having given the command to shutdown or reboot?
[*]I have a radio station added in Banshee but it won't play. On my laptop using DSL it plays fine so there is nothing wrong with the station. MP3 file son my disk play also fine, it's just the radio which doesn't work.
[/LIST]

I especially like the fact that after putting back the /home folder from the backup all programs are working again as if nothing happened. Fantastic.

---

### Post by lovinglinux on 2009-10-29
> **DeMus said:**
> [LIST=1]
[*]Whenever I start a mediaplayer, or a flash movie in Firefox, I hear a loud click coming from my loudspeakers. Is it possible to make it stop doing that by some setting, or is it simply a bug?[/LIST]

[http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12](http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12)

> You probably have a HDA audio card. If so then those clicks is caused by the power saving option introduced in karmic. You can solve this problem by commenting out the last line in the /etc/modprobe.d/alsa-base.conf

---

### Post by celtic426 on 2009-10-29
> **DeMus said:**
> 
2.Where can I switch off the 60 seconds delay when I want to shutdown or restart? It used to be in the preferences of the button. Why is it there anyway? Who wants to wait after having given the command to shutdown or reboot?

alt+f2
gconf-editor
apps, indicator-session 

source: [http://www.youtube.com/watch?v=_K79PrQdDYQ]("http://www.youtube.com/watch?v=_K79PrQdDYQ")

---

### Post by emigrant on 2009-10-29
@ [DeMus]("http://ubuntuforums.org/member.php?u=576559") soon change the ubuntu version in your profile ;)

---

### Post by DeMus on 2009-10-29
> **emigrant said:**
> @ [DeMus]("http://ubuntuforums.org/member.php?u=576559") soon change the ubuntu version in your profile ;)

Oops, sorry. Had no time to do it yet. Will do it soon.
Thanks for reminding me.

---

### Post by DeMus on 2009-10-29
> **celtic426 said:**
> alt+f2
gconf-editor
apps, indicator-session 

source: [http://www.youtube.com/watch?v=_K79PrQdDYQ]("http://www.youtube.com/watch?v=_K79PrQdDYQ")

Fantastic, thanks a lot.

---

### Post by DeMus on 2009-10-29
> **lovinglinux said:**
> [http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12](http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12)

Great, I hope the clicks are gone now. Thanks.

---

### Post by dresden on 2009-10-29
you guys are amazing :D the annoying click is goooone

---

### Post by DeMus on 2009-10-30
Point 3 of my initial post is working now after a reboot. Which I must say is strange. Why reboot after adding a radio-station in a media-player?

I do have to add a point 4 though:
Programs start very slow, or sometimes not at all, when started from the upper panel. In the lower panel I get a button with text: Starting .....
but after a few seconds (sometimes) the button disappears again.
When starting the same program from the menu it starts almost directly.

---

### Post by celtic426 on 2009-10-30
> **DeMus said:**
> Point 3 of my initial post is working now after a reboot. Which I must say is strange. Why reboot after adding a radio-station in a media-player?

I do have to add a point 4 though:
Programs start very slow, or sometimes not at all, when started from the upper panel. In the lower panel I get a button with text: Starting .....
but after a few seconds (sometimes) the button disappears again.
When starting the same program from the menu it starts almost directly.

Weird...Right click on the icons on the upper panel that you use to start the program and select properties.  See if the command is the same as the other ones in the menu.

You could try deleting the ones in the upper panel and then re-adding them by dragging the shortcuts from the main menu.

---

### Post by DeMus on 2009-10-30
> **celtic426 said:**
> Weird...Right click on the icons on the upper panel that you use to start the program and select properties.  See if the command is the same as the other ones in the menu.

You could try deleting the ones in the upper panel and then re-adding them by dragging the shortcuts from the main menu.

That's the way I got them there. In the main menu right-click on an item and choose: "Add to panel".
So they must be exactly the same. Nevertheless they work much slower than the ones in the main menu.
Thanks for your advise.

---

