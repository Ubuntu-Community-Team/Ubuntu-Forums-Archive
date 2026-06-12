---
title: "Firefox fonts"
date: 2009-10-26
forum: General Help
---

### Post by arnab_das on 2009-10-26
All of a sudden I found that on sites where unread posts were in "bold", i am getting regular fonts. dont know how it happened. but its getting very irritating. :( can anyone help?

---

### Post by arnab_das on 2009-10-26
plz help if anyone has found a solution

---

### Post by arnab_das on 2009-10-27
okay here's a bit of elaboration of the problem.

the first pic (the one below) is when "Allow Pages To Choose Their Own Fonts" is enabled from firefox preferences. you'll find, the unread posts which should have been in bold (have been highlighted in red circles) is instead in regular style.

[IMG]http://farm3.static.flickr.com/2604/4049333540_14d8c8f4ab_b.jpg[/IMG]
the pic below, is when the "Allow pages to choose own fonts" have been disabled and Dejavu Sans font has been enabled. You'll find that the exact same unread posts have been clearly marked in bold, distinct from all the other regular styled characters. i dont know whats causing this problem, but plz help me out as i want to use the default fonts of web pages.

(PS - I have ttf-msscorefonts installed)

[IMG]http://farm4.static.flickr.com/3488/4049333542_1280d440c4_b.jpg[/IMG]

---

### Post by Living2007 on 2009-10-27
These here are the defaults, if the setting have being modified!
[ATTACH]133266[/ATTACH]

---

### Post by arnab_das on 2009-10-27
using the default settings depicts the font exactly as the first pic. :( dunno what the problem is.

---

### Post by Living2007 on 2009-10-27
What FF version are you running?

---

### Post by arnab_das on 2009-10-27
3.5.3 the default one which came with karmic RC.

---

### Post by arnab_das on 2009-10-27
sorry for resurrecting this topic again but any help would be great. am really stuck with these stupid font problems. :(

---

### Post by arnab_das on 2009-11-14
solved. uninstalling wine resolved the issue.

---

### Post by sillyfofilly on 2009-11-14
I think I had the same problem, and you don't need to uninstall wine completely. The package wine1.2 recommends a package named ttf-tahoma-replacement which will make any pages using the Tahoma font family look all thin and weird. If you just remove this package then things should look fine again.

---

### Post by arnab_das on 2009-11-14
> **sillyfofilly said:**
> I think I had the same problem, and you don't need to uninstall wine completely. The package wine1.2 recommends a package named ttf-tahoma-replacement which will make any pages using the Tahoma font family look all thin and weird. If you just remove this package then things should look fine again.

cool but how to do that? i mean wont it remove the tahoma font of the ubuntu restricted extras pack?

---

### Post by sillyfofilly on 2009-11-14
You're right. I didn't notice before because the pages I was seeing this on defaulted to Arial when Tahoma wasn't available. So, I've used Fonty Python to add the .ttf files I got from a Windows installation

---

### Post by andrewabc on 2009-11-18
I had same problem. Installed wine and it changed fonts in firefox, no idea how to change back.
I uninstalled wine, same problem. Uninstalled tamaho font, same thing.

While installing wine it downloaded maybe 10 fonts from the internet, so looks like I'm gonna have to install wine on fresh 9.10 and see what gets installed.

EDIT:
Hmm, seems that uninstalling ttf-mscorefonts-installer removes them (uninstalling wine does not uninstall everything it installed). Maybe that will work.

---

### Post by arnab_das on 2009-11-19
this is the solution. pictures given. go through the "Extra Tips" area at the lower part of the post.

[http://thoughtsndreams.wordpress.com/2009/11/18/install-wine/](http://thoughtsndreams.wordpress.com/2009/11/18/install-wine/)

---

### Post by puller on 2010-01-27
> **andrewabc said:**
> I had same problem. Installed wine and it changed fonts in firefox, no idea how to change back.
I uninstalled wine, same problem. Uninstalled tamaho font, same thing.

While installing wine it downloaded maybe 10 fonts from the internet, so looks like I'm gonna have to install wine on fresh 9.10 and see what gets installed.

EDIT:
Hmm, seems that uninstalling ttf-mscorefonts-installer removes them (uninstalling wine does not uninstall everything it installed). Maybe that will work.

thanks, deleting ttf-mscorefonts-installer worked!!!
Of course you have to logout and login again.

---

