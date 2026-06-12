---
title: "Utility to download entire site's content"
date: 2006-02-21
forum: General Help
---

### Post by christopher.pascual on 2006-02-21
I am looking for a utility in linux to download all of the content on a website....

i tried wget, but i am struggling a bit


any ideas?

---

### Post by Fred Doolie on 2006-02-21
That'd be cool. If I understand what you mean, the action is called "Snaking". Yo u  end up with a local copy of the entire site.

Or... do you mean mass downloading? The Firefox browser has an extention called "Down them all". It lets you grab ALL the links on a page or all the graphics or all the MP3 or just what you want....whatever.

---

### Post by KnottyMan on 2006-02-21
wget -m -np url

read the man page, it tells all.  Could be the way the site is designed too.

---

### Post by KnottyMan on 2006-02-21
Sounds more like he wants a site rip.  DTA is good too for um, erm, late night browsing.

---

### Post by christopher.pascual on 2006-02-21
[QUOTE=KnottyMan]Sounds more like he wants a site rip.  DTA is good too for um, erm, late night browsing.[/QUOTE]


yea i am looking to rip the entire contents of the site, not just the links and whatnot


basically i want to be able to browse the site offline

---

### Post by ekravche on 2007-01-14
You'll need to get some sort of proxy software then. I'm not sure what the name of the software is but if you search for proxy in the repository then you may find what you are looking for.

---

### Post by keyboardslave on 2007-08-25
Attn Chris,

On windows i use ANAWARE , WEBSNAKE , google websnak.

on linux to do the same thing i use,
 wget  -r -p -U Mozilla [http://www.stupidsite.com/restricedplace.html](http://www.stupidsite.com/restricedplace.html)

the -r downloads the entire site

the -U Mozilla tricks the site into thinking you are using Mozilla to browse (incase they dont let you wget there site)

hope this helps,
futex

---

### Post by bollix47 on 2007-08-25
If you are using Firefox you could try the [ScrapBook]("https://addons.mozilla.org/en-US/firefox/addon/427") extension.

---

### Post by Bothered on 2007-08-25
Is HTTrack like what you're looking for: [http://www.httrack.com/](http://www.httrack.com/)

It's in the ubuntu repositories (universe).

---

### Post by b20963a2 on 2007-08-25
[http://www.httrack.com/](http://www.httrack.com/)
I believe it's even in the repo's

---

