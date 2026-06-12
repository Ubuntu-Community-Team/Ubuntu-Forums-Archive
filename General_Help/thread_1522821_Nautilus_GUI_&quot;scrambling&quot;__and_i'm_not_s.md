---
title: "Nautilus GUI &quot;scrambling&quot;  and i'm not sure why?"
date: 2010-07-02
forum: General Help
---

### Post by Macfunky on 2010-07-02
One day, for reasons i do not know, Nautilus started acting weird. I did not touch any setting or install anything related to Nautilus but i have, since a few days ago, been having problems with Nautilus. 

First thing i noticed was that there were 3 changes in the GUI. There was a slider at the bottom left that wasn't there before. This zooms in and out of the folders. Secondly there are 3 little icons on the top right which weren't there before, to change your view of the folders, compact, etc. Finally, as far as i can remember, there was a box above the side panel which allowed you to choose which kind of layout you wanted to see your file hierarchy in? This has since disappeared. 

There changes in the GUI didn't bother me too much but since noticing them, and not knowing why the changes happened, i find whilst scrolling up and down through folders the images of them scramble and i can't make out anything. I usually have to highlight the folders for this to go away but it will happen every consecutive time i try it. It is really bugging me now as i don't know why the changes to the GUI happened and now i am having problems with the images of my folders scrambling since. I am using Lucid and am loving it bar this. Anyone have any idea what could have happened and how i can get it back to the way it was?

---

### Post by WorMzy on 2010-07-02
That doesn't sound like a nautilus problem, but rather a problem with your video card or X server.

You can try shutting your PC down for a while to let it cool down (in case the graphics card is over heating), or moving /etc/X11/xorg.conf to /etc/X11/xorg.conf.old, then restarting X (or your PC).

---

### Post by Macfunky on 2010-07-02
It has been happening for a few days where it hadn't been before. The computer has been rebooted many times since and i have been having no other graphical problems

---

### Post by Macfunky on 2010-07-02
Here are examples of what is happening

---

### Post by yo2boy on 2010-08-04
Well, I'm having the same exact problem

[IMG]http://i.imgur.com/EbslV.png[/IMG]

---

### Post by WorMzy on 2010-08-04
What version of nautilus is that?


It could be a problem with that version of nautilus, but I still think it's a graphics related problem.

---

### Post by mc4man on 2010-08-04
> What version of nautilus is that?

looks like nautilus elementary (guessing a bit, never used

if so, then the Op and yo2boy should've mentioned...

---

### Post by WorMzy on 2010-08-04
After rereading the first post, the OP did mention that his nautilus window changed, and the description sounds like it's the same version of nautilus shown in the screenshot posted by yo2boy, so it's highly likely that it's a problem with the version of nautilus after all.

I think the best thing to do would be to file a bug report on [launchpad]("https://launchpad.net/"), then look in Synaptic for a different version of Nautilus, and install that.

---

### Post by mc4man on 2010-08-04
A quick search shows that what yo2boy posted is nautilus-elementary, any issues should probably be posted to whatever ppa it was installed from.
It would also seem likely the Op added a ppa for the same, maybe inadvertently thru the likes of ubuntu-tweak.

---

### Post by meburke on 2010-08-04
You don't mention what version of Ubuntu you are using, but I had some similar problems with Lucid after an update a couple of weeks ago. After two days messing with it I reverted to Karmic.

I am using an Acer X209w, usually running at 1680 x 1050. I could get a lower resolution by booting from the LiveCD in safe configuration, but I couldn't make it stick.

Mike

---

