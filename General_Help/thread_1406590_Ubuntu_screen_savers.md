---
title: "Ubuntu screen savers"
date: 2010-02-14
forum: General Help
---

### Post by Dreamer-of-Days on 2010-02-14
So, I wasn't too satisfied with Koala's default selection of screen savers. For anyone else who's not entirely satisfied with the default screen savers available, an easy way to get more (200 total, I think) on your system is click on

System-> Administrator-> Synaptic Package Manager

in the search area type in 

xscreensaver-gl-extra

this one gives you 3D screen savers. For more 2D ones

xscreensaver-data-extra

There's also an option for those of you who prefer xscreensaver to gnome. For a full guide to installing xscreensaver, 23meg has a phenomenal "how to" [here]("http://ubuntuforums.org/showthread.php?t=195557&highlight=xscreensaver")
Hope that's what you wanted.

Added Feb 14 (after I woke up)
When reading the descriptions it states that both of the above work for gnome-screensaver (Karmic Koala's default) and x-screensaver, so if you want to convert to gnome/x at any point you won't have to reinstall packages to get more screen savers.

---

### Post by joeknoodle on 2010-02-14
Good eye, but still no help for those who wish to use a particular folder for images as screensavers.

One of the first issues I get when converting folks to Ubuntu is...

"Where's my pictures screensaver"

"It's there, it points to your pictures folder"

"I see that, but I want to set a particular folder"

Without resolving that one issue I will forever be hamstrung trying to gain converts to Gnome at least, and Ubuntu in general. 

I don't buy the developer's claim that it's too complicated to implement. If folks can do it on Winblows, surely they will be comfortable doing it on Gnome/Ubuntu.

I tell folks, "they do that to avoid confusion". What do I hear back?

"Do you think I'm that stupid? I can do it on Winblows, why not here?"

---

### Post by SecretCode on 2010-02-14
```
cp /usr/share/applications/screensavers/personal-slideshow.desktop \
   ~/.local/share/applications/screensavers/my-personal-slideshow.desktop
gedit ~/.local/share/applications/screensavers/my-personal-slideshow.desktop
```

Change the Exec line to read
```
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow \
   --location=/media/Pictures/favourites
```
and change the 'Name' to something you like.

Save. Go into prefs > screensavers, select.

There is a sort of explanation [here]("http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions#Why_doesn.27t_the_screensaver_preferences_tool_allow_me_to_change_the_settings_for_the_theme.3F") of why GNOME requires you to make a new screensaver entry rather than have a settings dialogue for every screensaver theme. I don't agree with it but at least they have a reason.

---

### Post by Dreamer-of-Days on 2010-02-14
xscreensaver allows one to change the picture folder through the GUI (for the newbs: Graphical User Interface: windows and buttons you can click). After I did some browsing I discovered that most versed Linux uses prefer xscreensaver to gnome-screensaver, and were livid that gnome was the default in Koala. I checked it out and it works, so if that's what people want, then you can easily guide them through that set-up.

Also

1) Newb, or newbie (new*bee) is not a derogatory term, and is unaffiliated with it's "1337" counterpart "noob". It means someone who is new. It is even considered an affectionate term, like when a parent calls their child "buba", "honey", or "sweety". Sorry if I say something you don't understand. I try to explain all of my colloquialisms.

2) We realize that the console/terminal can be intimidating, but don't fret. When I first began conversion to Linux I used the Ubuntu Software Center (formerly Add/Remove Applications) solely and wouldn't even read a page that had text commands. I eventually acquiesced and copy and pasted the commands needed to install Skype. Since then, I'll opt to install stuff through yakuake just because it's kinda fun.

3) If you are indeed what I consider a newb, and you can't find answers to your questions in Ubuntu Forums, try

google.com

I kid, I kid. Email me at

[email]progenyofcuchulainn@gmail.com[/email]

I don't have all the answers, but I'll try.

---

