---
title: "Dock recommendations?"
date: 2009-07-14
forum: General Help
---

### Post by Vrekk on 2009-07-14
This has probably been asked before but i was unable to find it.  I'm looking for recommendations for a good dock for gnome, but i need one that can go on the right side of the screen not the bottom.  I tried the docky from gnome do, and i like it a lot, but it seems i can't to move it to the right side of the screen.  

I don't need something with a lot of fancy features just something to launch my normal apps off of.

---

### Post by PGScooter on 2009-07-14
If you're just looking for something simple, right click the default ubuntu panel and click "new panel". I think you can add program icons to it pretty easily. ANd use the drawer applet to stack up icons. Haven't tried it, but might be what you're looking for.

---

### Post by Vrekk on 2009-07-14
I tried that once but it just didnt look very good.  And when I said I don't need something with a lot of fancy features, I was just tring to say that i dont NEED them, but its not gonna kill me if it has a cool feature or anything :D

---

### Post by snakeman21 on 2009-07-15
Try Cairo-Dock.  Unbelievably customisable, so you can turn it into pure eye candy or make it a very simple, plain dock.  You can put it on any side and control the size.  I suggest you give it a try.

---

### Post by PGScooter on 2009-07-15
Vrekk, I definitely understand what you mean. I agree that if fancy and pretty things work just as well as the simple ones and are just as stable, why not indulge a little :).

Good luck!

---

### Post by Vrekk on 2009-07-15
> **snakeman21 said:**
> Try Cairo-Dock.  Unbelievably customisable, so you can turn it into pure eye candy or make it a very simple, plain dock.  You can put it on any side and control the size.  I suggest you give it a try.

I cant get that one working correctly for some reason, I cant add any launchers :|

---

### Post by Short__Error on 2009-07-15
You can get gnome-do and use it as a dock its nice an simple and i have had no problems with it unlike the cairo-dock i could not get the theams to work right,,, but thats because i am a noob rofl...

---

### Post by Twitch6000 on 2009-07-15
Cairo Dock is what I would suggest.

Or you can use Kiba-Dock. If you don't want to compile kiba-dock there are deb files at getdeb.net

---

### Post by Vrekk on 2009-07-15
Cario dock isnt working and Kiba docks not worth the trouble (i heard that the physics stuff dosnt work anymore anyway) :mad:

---

### Post by TheNosh on 2009-07-15
> **Twitch6000 said:**
>  If you don't want to compile kiba-dock there are deb files at getdeb.net

could you give me a link, cause i searched getdeb.net ([http://www.getdeb.net/search.php?keywords=kiba-dock](http://www.getdeb.net/search.php?keywords=kiba-dock)) and i found nothing

---

### Post by binbash on 2009-07-15
> **Vrekk said:**
> Cario dock isnt working and Kiba docks not worth the trouble (i heard that the physics stuff dosnt work anymore anyway) :mad:

Physics stuff is working

---

### Post by fabounet on 2009-07-15
> I cant add any launchers
a permission problem ? 
try ```
chmod -R 777 ~/.config/cairo-dock
```

---

### Post by hibliss on 2009-07-15
I have used Cairo and Gnome-Do. 

I have recently been running Eeebuntu on my Eee PC, and they have an interesting and lightweight solution on how to create a "dock" from the existing panel.

All you do is add things to the panel and make it autohide, then make the panel transparent.

There is a tutorial here -- [http://www.eeebuntu.org/wiki/index.php/Gdock]("http://www.eeebuntu.org/wiki/index.php/Gdock")

The best thing about this is it always starts with the machine and there is no process for the dock as it is built in to the Window manager. It also looks great with a few custom Icons.

---

### Post by mammalsauceman on 2009-07-15
try avant-window-navigator, it is in the add/remove thingy in ubuntu (Applications->Add/Remove...)

I dont know if it can go on the side of the screen, but it is easy to use, and has cool little applets

btw i dont think it will come up if u put the hyphens in the search bar

---

### Post by scaine on 2009-07-16
Docky (the Gnome-Do dock option) can only go top or bottom, it doesn't support left/right (and won't until they think up a slick way to stay within the parameters of the Gnome-Do search list).

Cairo-Dock is the slickest dock out there in terms of eye-candy and is incredibly customisable.  So much so that they include a "simple" options screen by default, which *still* lets you customise to extreme levels.  If you can't get it working, try the latest version ([https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14108](https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14108))

AWN is more basic, but, I believe, more functional and possibly more stable.  It doesn't support the Mac OSX style "zoom" effect (or didn't a year ago when I last tried it).

Personally, I use Docky, because it's more than just a dock, it's also a search, a twitter client, a music front end, an e-mail initiator and many more - there's about 40 or so plug-ins that integrate to a vast number of services - twitter, youtube, etc.  But if you need a dock on the left/right, you'll need to look elsewhere.

Happy hunting.  If you find a good one, post back.

---

### Post by MasterPoulos89 on 2009-07-16
I love the kiba-dock. 

The next best I think is AWN which is in the repositories. But AWN doesn't separate the launchers from the running applications the way I would like.

To easily install kiba-dock check my thread:

[http://ubuntuforums.org/showthread.php?t=1203969&highlight=kiba+dock](http://ubuntuforums.org/showthread.php?t=1203969&highlight=kiba+dock)

---

### Post by Vrekk on 2009-07-16
> **binbash said:**
> Physics stuff is working

How do you set it up then? Was looking for how to set that up and i wasnt able to figure it out.

Edit: Never mind i didnt read the full thread.

---

### Post by Vrekk on 2009-07-16
OK so right now im using Kiba-dock and so far i like it!, but 2 things are acting really werid with it, for one its shows the same window twice, and then the lanucher.  For example if i open Chromium , which is a launcher on the desktop, two more show up acting as the window selectors, giving me a grand total of 3 icons on the dock :|.  Also some times when I open a new app it appers in the dock as a gray square.  If anyone knows any fixes to this, I REALLY like this dock

---

### Post by MasterPoulos89 on 2009-07-17
> **Vrekk said:**
> OK so right now im using Kiba-dock and so far i like it!, but 2 things are acting really werid with it, for one its shows the same window twice, and then the lanucher.  For example if i open Chromium , which is a launcher on the desktop, two more show up acting as the window selectors, giving me a grand total of 3 icons on the dock :|.  Also some times when I open a new app it appers in the dock as a gray square.  If anyone knows any fixes to this, I REALLY like this dock


I use the newest kiba-dock version so I'll explain how I set it up for me. Obviously once its running drag and drop the icons to launcher. I don't know why u have a double launcher problem. For me when I launch an app a new icon shows up as a running application then I add a separator between the running app and the launchers. Its hard to grab the separator sometimes but it does work. Then I just edit the settings to use the features I like.

If you continue getting the double launcher problem try to remove the icons and re-drag and drop them.

Other then that I don't know why you would have such a problem. It works good for me.

Edit: The problems I do know are:

1) Specific programs don't show up on kiba-dock at all. ex: Open System/Preferences/Appearance and you will see kiba-dock does not show it running.

Work Around: I get around this problem by adding the "Windows List" applet to the top panel.(I also delete the bottom panel just because it interferers with the dock. Any necessary applets could be easily added to the top panel)

2)Few programs show up with no icon and I see a generic icon(that might be your grey square problem)

Work Around: You can always right click on the launched app from the dock and set a custom icon.

Those are the only problems I have had and they don't bother me.

Hope you manage to solve your other problems.

---

