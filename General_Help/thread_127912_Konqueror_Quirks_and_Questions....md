---
title: "Konqueror Quirks and Questions..."
date: 2006-02-10
forum: General Help
---

### Post by Jucato on 2006-02-10
Ok, so far I've been using Konqueror as a web browser and file manager for a few weeks now. Actually, the experience is quite pleasing (personally, that is). But there are a few issues that I really can't find some answers to. Hope somebody around here knows.

1. Rendering: I'm having a bit of problem with certain sites. they appear quite wrong. One of them is the [KDE Myths]("http://kdemyths.urbanlizard.com/") site. There are some text missing, that display quite properly in Firefox/Opera. I find it quite ironic that a site devoted to KDE would display wrong. Another sight is [blog]("http://blog.mornfall.net/") from one of the devs of Adept (I think). The archives list on the right side display over the main text. I don't know if I'm the only one having these problems. If anyone can check them for me, I'd greatly appreciate it.

2. Download problems: Specially from [KDE-look]("http://www.kde-look.org"). I guess it's quite related to PHP files. When I click a download link, Konqueror displays the PHP in Kate. When I try to right-click and Save Link As, only the PHP page is saved. This does not happen always. Sometimes, the links work well. Does anyone have any idea what the problem is?

Lastly, this is more of wondering rather than asking: Are there any news of what the Konqueror devs are up to? Are there any plans of developing extensions for Konqueror, something like Firefox's? Or how about making KHTML better?

Thanks for any input that you could give to help. :D

---

### Post by niviche on 2006-02-10
I am pretty happy with Konqueror, and haven't noticed the quirks you mention. But for the second question:

[QUOTE=Fenyx]2. Download problems: Specially from [KDE-look]("http://www.kde-look.org"). I guess it's quite related to PHP files. When I click a download link, Konqueror displays the PHP in Kate. When I try to right-click and Save Link As, only the PHP page is saved. This does not happen always. Sometimes, the links work well. Does anyone have any idea what the problem is?[/QUOTE]

I have installed Kget (through Synaptic) and do not have this problem. Give it a try, it might solve your issues with this.

---

### Post by dresnu on 2006-02-10
Hm, those pages you mentioned work just fine in my konqueror. The rendering is exactly the same as in firefox(except for the fonts). I'm using version 3.5.1.
I really like konqueror too, but I mainly use firefox these days because I find it too be a little bit faster than konqueror(especially using fasterfox). But the big deal that stops me from using konqueor is that pages "feel" alot sluggish, particularly when scrollig up and down. Firefox(or maybe I should say Gecko) is much smoother.

---

### Post by niviche on 2006-02-10
[QUOTE=dresnu]But the big deal that stops me from using konqueor is that pages "feel" alot sluggish, particularly when scrollig up and down. Firefox(or maybe I should say Gecko) is much smoother.[/QUOTE]

I don't know if Konqueror is actually slower, but it feels a bit sluggish at times. However, compared to the time one (or at least I) has to wait for Firefox to boot up, I'd rather stick with Konqueror on KDE (not to mention the better integration with the rest of the desktop).

---

### Post by Neo Ex on 2006-02-10
[QUOTE=Fenyx]Ok, so far I've been using Konqueror as a web browser and file manager for a few weeks now. Actually, the experience is quite pleasing (personally, that is). But there are a few issues that I really can't find some answers to. Hope somebody around here knows.

1. Rendering: I'm having a bit of problem with certain sites. they appear quite wrong. One of them is the [KDE Myths]("http://kdemyths.urbanlizard.com/") site. There are some text missing, that display quite properly in Firefox/Opera. I find it quite ironic that a site devoted to KDE would display wrong. Another sight is [blog]("http://blog.mornfall.net/") from one of the devs of Adept (I think). The archives list on the right side display over the main text. I don't know if I'm the only one having these problems. If anyone can check them for me, I'd greatly appreciate it.

2. Download problems: Specially from [KDE-look]("http://www.kde-look.org"). I guess it's quite related to PHP files. When I click a download link, Konqueror displays the PHP in Kate. When I try to right-click and Save Link As, only the PHP page is saved. This does not happen always. Sometimes, the links work well. Does anyone have any idea what the problem is?

Lastly, this is more of wondering rather than asking: Are there any news of what the Konqueror devs are up to? Are there any plans of developing extensions for Konqueror, something like Firefox's? Or how about making KHTML better?

Thanks for any input that you could give to help. :D[/QUOTE]
1. I don't have your problems, so I can't help you;
2. KControl -> KDE Components -> File associations -> application -> x-php -> add Konqueror (it must be above Kate). I think this will work.

---

### Post by Jucato on 2006-02-10
I have KGet but still not working. my PHP's are also associated w/ Konqueror only (no Kate). I guess my problems are just an isolated case. Which makes it all the more harder to trace and solve. Thanks for trying to help! I really appreciate the effort.

I love Konqueror because of its ability to act as both web browser and file manager, and also because of its wonderful integration with KDE. Not to mention the fact that it's very light, probably owing to the fact that its integrated. I do feel sometimes that it's a bit slow or sluggish, but not enough to make a huge difference when put side by side with Firefox. So until the time that Firefox slims down and can access KDE's KParts/KIOslaves, I'm sticking to Konq.

(BTW, any news of any future features for Konqueror?)

---

### Post by tikal26 on 2006-02-10
Fenyx:
I have the same problem when downloading from kde-look. 
Neo EX:
How do I find the file association. I don't have Kcontrol, but I do have system setting, but they don't have that under kde components.
thanks for the help

---

### Post by Jucato on 2006-02-10
System Settings and KControl are the same. KControl is the app that runs System Settings.
KControl > KDE Components > File Associations.
Alternatively, you can go to Konqueror > Settings > Configure Konqueror > File Associations. they do the same thing.

---

