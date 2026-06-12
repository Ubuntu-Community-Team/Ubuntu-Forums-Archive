---
title: "change default file manager?"
date: 2006-02-23
forum: General Help
---

### Post by russellc on 2006-02-23
the default file manager on this ubuntu installation has been nautilus since i've installed it. and ever since i've been trying to find a decent one to replace it. now i have found one ([Thunar](http://thunar.xfce.org/index.xhtml)) and i would highly recommend it. it is amazing. now, when i open folders from firefox (open containing folder, etc) it still opens nautilus as the default file manager.

does anybody know how i can change all folder associations to open thunar (like from firefox, other apps)? thanks!

---

### Post by Xian on 2006-02-23
[QUOTE=russellc]the default file manager on this ubuntu installation has been nautilus since i've installed it. and ever since i've been trying to find a decent one to replace it. now i have found one ([Thunar](http://thunar.xfce.org/index.xhtml)) and i would highly recommend it. [/QUOTE]

Out of curiosity, what does Thunar do that makes it worth switching?

---

### Post by russellc on 2006-02-24
i just like it better :P is it really difficult to change file managers?

feels better all around.

---

### Post by rfruth on 2006-02-24
Come on russellc be more specific than feels better all around, whats it do that  Nautilus doesnt ?

---

### Post by OBnascar on 2006-02-24
[QUOTE=rfruth]whats it do that Nautilus doesnt ?[/QUOTE]

aaaah ! no answer to this ? hmmm......what do you think that means ?

I am a very big fan of Nautilus, to me it is the greatest, it fits my needs perfect. But isn't it that way with every apt, different pleasures for different people. 

At the "LinuxQuestions.org forums", they are voting on the top apts of 2005 which includes file managers, I am waiting for the results, should be interesting.

---

### Post by Xian on 2006-02-24
[QUOTE=OBnascar]But isn't it that way with every apt, different pleasures for different people. [/QUOTE]

The member stated that they had "been trying to find a decent one to replace it" ever since Nautilus was first installed. To me it sounded like a lot more was going on than just some quirky personality thing, and I don't think outright dissatisfaction would be far from the actual category. So, it was certainly appropriate to ask what was so great about their discovery and why it is so much better. 

Their answer was not very informative.

---

### Post by Joey French on 2006-02-24
The answer doesn't matter. If he wants to change it, it shouldn't matter why. That's why he uses linux in the first place- choice.

---

### Post by Xian on 2006-02-24
Of course it wouldn't matter except that _they_ brought up the subject.
It's no big deal, but I was curious so I asked.... for all the good it did.

I'll look around for a remedy to your more pertinent issue.

---

### Post by Xian on 2006-02-24
To stop Nautilus from managing your desktop:

In Gconf-editor go apps->nautilus->preferences. 
Scoll down till you see the "show desktop" item and unselect it.

If you want something else to do the same there are replacements.
Such as rox, feh & idesk (to some degree) and others...

Configuring individual apps to use another FM is another matter.
For that it will depend upon how each application is configured.

A rifle approach would be to rename /usr/bin/nautilus.
But you'll still need to enable the replacement.

---

### Post by Zyphrexi on 2006-02-24
I dislike nautilus due to the lack of a location bar, while i know (now) you can enable it, I want a location bar always. Also I dislike the style of tabs. (would they be tabs?)
I prefer the konqueror style.

when i say location bar I mean in

Go > Location...

---

### Post by jrib on 2006-02-25
[QUOTE=Zyphrexi]I dislike nautilus due to the lack of a location bar, while i know (now) you can enable it, I want a location bar always. Also I dislike the style of tabs. (would they be tabs?)
I prefer the konqueror style.

when i say location bar I mean in

Go > Location...[/QUOTE]

applications menu -> system tools -> configuration editor: /apps/nautilus/preferences/always_use_location_entry

If you enable the option above, nautilus will always use the location bar.  

[QUOTE=russellc]the default file manager on this ubuntu installation has been nautilus since i've installed it. and ever since i've been trying to find a decent one to replace it. now i have found one ([Thunar](http://thunar.xfce.org/index.xhtml)) and i would highly recommend it. it is amazing. now, when i open folders from firefox (open containing folder, etc) it still opens nautilus as the default file manager.

does anybody know how i can change all folder associations to open thunar (like from firefox, other apps)? thanks![/QUOTE]
I would have used the hack that Xian suggested (renaming the bin).  It'll get the job done I guess...
Only other thing I can think of: in addition to stopping nautilus from handling the desktop is to look at  nautilus-folder-handler.desktop files, which (I am guessing by the name) decides what app to open for folders.

---

### Post by russellc on 2006-02-26
thanks for the replies. i already have disabled nautilus from handling the desktop (or running a new shell in my case, since i am using enlightenment. i have tried creating a symbolic link to thunar (named nautilus) when i rename nautilus to something else, but that didn't help. its alright i guess, i can survive.

since i got some free time now, i'll be more specific as to why i like thunar better haha. before, i was a bit lazy.
- speed. it loads faster and loads large folders faster than nautilus
- features. you could argue that nautilus has more, but i feel that thunar has what i need, and is simple at presenting those features to me
- aesthetics/layout. i like the way its laid out better than the way nautilus is laid out (has a finder-esque layout to it)
- gestures. middleclick (hold) and you get to back/forward/up/reload with a move of the mouse
- thumbnails. the thumbnails look cooler too. lol.

---

### Post by OBnascar on 2006-02-26
[QUOTE=russellc]
- speed. it loads faster and loads large folders faster than nautilus
- features. you could argue that nautilus has more, but i feel that thunar has what i need, and is simple at presenting those features to me
- aesthetics/layout. i like the way its laid out better than the way nautilus is laid out (has a finder-esque layout to it)
- gestures. middleclick (hold) and you get to back/forward/up/reload with a move of the mouse
- thumbnails. the thumbnails look cooler too. lol.[/QUOTE]

Thanks russellc for sharing this, I'll be checking out thunar myself sometime.

---

### Post by huckem on 2006-02-26
sounds good, thanks for the info on it.  I think I might check it out too, although I have no qualms with Nautilus... Russellc, was there anything in particular that you *didn't* like about Nautilus?

---

### Post by russellc on 2006-02-26
well, basically the opposite of what i listed is what i didn't like. heh.

i'm guessing it takes a bit longer to load because it needs to load some gnome libraries also, since nautilus does not load for me at startup (am using enlightenment desktop environment). thunar loads instantly, and that is not an understatement. i click the button and it's there. nautilus takes 1.5 seconds more at least.

folder loading times (depending on the  contents of the folder) are also very obvious in thunar than in nautilus

also, this might just be me, but sometimes i just get tired of something and search for something new/fresh. nautilus had its own small annoyances that i didn't like.

---

### Post by akinokaze on 2007-05-28
Recently switch from kubuntu to xubuntu.
This was what i did to set default file manager in firefox (open containing folder, etc) to thunar:
cp /usr/share/applications/Thunar-folder-handler.desktop ~/.local/share/applications/
vi ~/.local/share/applications/mimecache.info
change to line: x-directory/gnome-default-handler=Thunar-folder-handler.desktop;kfmclient_dir.desktop
For my case previously i set konqueror to be default file manager, hence the existence of kfmclient_dir.desktop file. Now i just add Thunar-folder-handler.desktop infront of it.

Thunar is really fast. Open instantly when open containing folder.

---

