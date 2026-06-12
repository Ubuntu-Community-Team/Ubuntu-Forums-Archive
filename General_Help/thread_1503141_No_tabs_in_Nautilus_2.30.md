---
title: "No tabs in Nautilus 2.30?"
date: 2010-06-06
forum: General Help
---

### Post by photodan on 2010-06-06
I just came over from Mint 8 to Lucid yesterday and I installed Mint 9 on a Virtualbox. My problem seems ridiculously simple but it's driving me nuts! As the title of the thread says: In Nautilus 2.30 I have a search bar instead of tabs. I can turn it off and on by checking the view menu Location Bar button. I can find no way to change it to tabs though. The kicker is, in Mint Nautilus has tabs, enabled when I check Location Bar in the view menu. And, it's the same version of Nautilus - 2.30.1.  Anyone with experience give me some guidance? Heck, anyone with no experience too. I'd just like those tabs back.  Thanks in advance, arkiedan

---

### Post by WorMzy on 2010-06-06
The tab bar only appears if you have multiple tabs open. Can you press Ctrl+T to open a new tab?

---

### Post by photodan on 2010-06-06
> **WorMzy said:**
> The tab bar only appears if you have multiple tabs open. Can you press Ctrl+T to open a new tab?

Yep, it will open another but that's all, the first and the last directories. In Mint you can click through several directories, each progressing to the right in it's own tab. That way you can go as deep into the directory structure as you want and then click back only as far as you want. I'm hoping it's possible in Lucid. Maybe not????

---

### Post by WorMzy on 2010-06-06
I'm not sure what you mean, but are you possibly talking about the breadcrumb trail, rather than tabs? Like this:
[IMG]http://www.ubuntu-pics.de/bild/78072/selection_041_Pz1FRT.png[/IMG]
Where clicking on home will take me back to the home folder, etc?

That's how Nautilus is by default on Lucid. If you're just seeing the location bar, then you need to open gconf-editor, browse to "/apps/nautilus/preferences/" and change "always_use_location_entry" to false.

You need to make the location bar visible too.

---

### Post by photodan on 2010-06-06
> **WorMzy said:**
> I'm not sure what you mean, but are you possibly talking about the breadcrumb trail, rather than tabs? Like this:
[IMG]http://www.ubuntu-pics.de/bild/78072/selection_041_Pz1FRT.png[/IMG]
Where clicking on home will take me back to the home folder, etc?

That's how Nautilus is by default on Lucid. If you're just seeing the location bar, then you need to open gconf-editor, browse to "/apps/nautilus/preferences/" and change "always_use_location_entry" to false.

You need to make the location bar visible too.

Thanks!

That's what I was trying to describe. Your instruction did it!

I've got to look around the gconfig-editor. It does a good job of hand-holding as you go through there. Impressive.

Again, thanks!

---

### Post by jacoboss on 2010-07-20
Isn't there a way to get back to to the "old fashion" way?
With a button to switch mode? ( like in 2.28 i.e. )
See here:

[http://upload.wikimedia.org/wikipedia/commons/7/7c/Nautilus_2-28-1_it.png](http://upload.wikimedia.org/wikipedia/commons/7/7c/Nautilus_2-28-1_it.png)

Or a way to keep them both?
And i'd also like to know where to find all the parameters of nautilus i can add/edit from gconf-editor, is there a reference manual out there somewhere?
and pleas dont say search in here: [http://live.gnome.org/Nautilus](http://live.gnome.org/Nautilus) i'd like a link to the right document / page possibly ( can't really waste too much time on it... )

thanks to everyone in advance :D

---

### Post by jacoboss on 2011-03-25
> **jacoboss said:**
> Isn't there a way to get back to to the "old fashion" way?
With a button to switch mode? ( like in 2.28 i.e. )
See here:
 
[http://upload.wikimedia.org/wikipedia/commons/7/7c/Nautilus_2-28-1_it.png](http://upload.wikimedia.org/wikipedia/commons/7/7c/Nautilus_2-28-1_it.png)
 
Or a way to keep them both?
And i'd also like to know where to find all the parameters of nautilus i can add/edit from gconf-editor, is there a reference manual out there somewhere?
and pleas dont say search in here: [http://live.gnome.org/Nautilus](http://live.gnome.org/Nautilus) i'd like a link to the right document / page possibly ( can't really waste too much time on it... )
 
thanks to everyone in advance :D
 
no way at all?
nothing like gconf or stuff like that?
( i think this could be useful to many people... )

---

