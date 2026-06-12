---
title: "matching the features of other OSes"
date: 2009-11-02
forum: General Help
---

### Post by gamelord12 on 2009-11-02
I'm very happy with this release of Ubuntu.  I had tried KDE and it did not meet my expectations, and now that 9.10 is out, GNOME's upgrades were some pleasant surprises.  However, there are still a few features that I'd like to get figured out.

Instant search: I know Beagle can produce results, but I want to effortlessly pull up a search box from my desktop and just find things instantly.  In Vista, you just hit the Super key and it's ready to search.  In Mac, you just select Spotlight and you're ready to search.  With Beagle, you have to open up its own window, and it's kind of obtrusive.  There's the Deskbar applet, and I enabled the Beagle and Beagle Live Search plugins, but the applet always freezes after a few searches.  If it weren't for that, it would be great.  GNOME-Do is great for locating files by name, but I also want to be able to search their contents, which Beagle does, but there's no front-end to give me live results as I type that searches with Beagle except for Deskbar, which has issues.

Folder previews: In Vista, when browsing your file system with Explorer, your folders show previews of the pictures or videos or documents inside in a fan type of view.  Is there anything like that that I can install in Ubuntu?

Exposè: In Mac OS-X, there's that exposè feature where you can show all of your windows on-screen at once.  Is there a plugin for this available for Compiz?  Something like this is available in KDE4, but I want the functionality in GNOME.

Also, Empathy confuses me.  Is there any reason to use it over Pidgin in this release?  I tried giving it a shot, but it didn't appear in my notification area and I couldn't group multiple screen names together (for people with more than one screen name), and that annoyed me, so I went back to Pidgin.

---

### Post by spoon_ on 2009-11-02
The compiz plugin you're looking for is called "scale".

---

### Post by wildweathel on 2009-11-02
> **gamelord12 said:**
> I'm very happy with this release of Ubuntu.  I had tried KDE and it did not meet my expectations, and now that 9.10 is out, GNOME's upgrades were some pleasant surprises.  However, there are still a few features that I'd like to get figured out.

Instant search: I know Beagle can produce results, but I want to effortlessly pull up a search box from my desktop and just find things instantly.  In Vista, you just hit the Super key and it's ready to search.  In Mac, you just select Spotlight and you're ready to search.  With Beagle, you have to open up its own window, and it's kind of obtrusive.  There's the Deskbar applet, and I enabled the Beagle and Beagle Live Search plugins, but the applet always freezes after a few searches.  If it weren't for that, it would be great.  GNOME-Do is great for locating files by name, but I also want to be able to search their contents, which Beagle does, but there's no front-end to give me live results as I type that searches with Beagle except for Deskbar, which has issues. 

I've never run Beagle, but I think I'll give it a shot; see if I can find an instant-search feature.

> 
Folder previews: In Vista, when browsing your file system with Explorer, your folders show previews of the pictures or videos or documents inside in a fan type of view.  Is there anything like that that I can install in Ubuntu?

Well, Nautilus has thumbnails, but...one sec, I've got a Vista machine here let's see if I can see...

Ooh, that is kinda snazzy.  You mean how Explorer adds a couple of thumbnails to a folder's icon if it has pictures inside?  No, I haven't seen anything quite like that in Ubuntu.  It's cool, but to be honest, it doesn't really strike me as all that useful.

> 
Exposè: In Mac OS-X, there's that exposè feature where you can show all of your windows on-screen at once.  Is there a plugin for this available for Compiz?  Something like this is available in KDE4, but I want the functionality in GNOME.

Try Alt+Shift+Up.  I'm not sure if it's enabled by default.

System -> Preferences -> CompizConfig.  (Software center CCSM, if it's not installed)  Scale has something called "window picker" that as far as I know is pretty much identical to  Exposè.  Expo (Super+E) zooms out and shows all your desktops at once.  

> 
Also, Empathy confuses me.  Is there any reason to use it over Pidgin in this release?  I tried giving it a shot, but it didn't appear in my notification area and I couldn't group multiple screen names together (for people with more than one screen name), and that annoyed me, so I went back to Pidgin.

Karmic is a pre-LTS, thus a lot of changes planned for Lucid LTS were included, if developers felt they would benefit from 9-12 months of polishing rather than the usual 3-6.  Some things feel half-finished because they are, in terms of stabilization time, half finished.  

So, there's nothing wrong with using Pidgin/Ekiga if you prefer them.  The only reasons to use Empathy are if a) you prefer it, b) it doesn't bother you, or c) you're involved in testing or development.

---

### Post by gamelord12 on 2009-11-04
Okay, so scale works great.  Any help with the other stuff?

---

### Post by wildweathel on 2009-11-04
Yes, I covered Pidgin (use it if you like it), and the folder preview (there isn't and no plans to chase down such a little feature, as far as I know).

That leaves Beagle.  I'm not a desktop-search fan, so maybe someone else will have more to say.  I *do* like being able to do things from the keyboard, but I've used Gnome Do (a little, not much) or a terminal for that.   

"Not searching" is a design tenet of Do.  It's a communication metaphor: you know what you want and you tell the computer.  If you don't know, you'd tell your computer to search--and there even are some search plugins.  To put it in OS X terms, Do is Quicksilver, not Spotlight.  I haven't used Vista much at all, but it looks like start menu search tries to do both.

In any case, F12 toggles Beagle's search menu, and that seems even faster than clicking Spotlight.  What's missing?

---

