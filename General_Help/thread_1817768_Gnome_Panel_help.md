---
title: "Gnome Panel help"
date: 2011-08-03
forum: General Help
---

### Post by ghost45 on 2011-08-03
First I would like to say that I do apologize if there is already a thread for this problem on the website, I looked for a bit but could not find what I was looking for.

I am trying to get rid of the gnome panel shadow in ubuntu 11.04(classic, not using unity). I know that I can get rid of it using compiz but I do not want to use that. I suppose my question would be, where is the "panel-shadow.png" file located that I can edit and make transparent? I found it before but cannot for the life of me now. 

Any help is appreciated, again sorry if this has already been discussed, if it has just post the link to the thread. Thanks =]

---

### Post by plucky on 2011-08-04
> **ghost45 said:**
> First I would like to say that I do apologize if there is already a thread for this problem on the website, I looked for a bit but could not find what I was looking for.

I am trying to get rid of the gnome panel shadow in ubuntu 11.04(classic, not using unity). I know that I can get rid of it using compiz but I do not want to use that. I suppose my question would be, where is the "panel-shadow.png" file located that I can edit and make transparent? I found it before but cannot for the life of me now. 

Any help is appreciated, again sorry if this has already been discussed, if it has just post the link to the thread. Thanks =]

From a terminal ```
locate panel-shadow.png
``` gives me ```
/usr/share/unity/3/panel-shadow.png
```

Good Luck

---

### Post by WhiteHorse on 2011-08-04
sudo apt-get remove gnome

---

### Post by ghost45 on 2011-08-04
I want to continue using gnome, so I do not think I should remove it, and the panel-shadow.png that you (plucky) are referring to is for unity, which I do not use... Is it possible it is labeled something else? I was pretty sure it was labeled that but if the only thing that is coming up is for unity then I guess not? =/ Is anyone aware of a .png that controls the shadow of the gnome panel shadow? (the top bar). Thanks in advance.

---

### Post by CatKiller on 2011-08-04
> **ghost45 said:**
> I know that I can get rid of it using compiz but I do not want to use that.

If you've got a shadow on the panel, you're probably already running Compiz.

---

### Post by CatKiller on 2011-08-04
> **WhiteHorse said:**
> sudo apt-get remove gnome

Don't be stupid.

Anyway, the *gnome* metapackage isn't installed.

---

### Post by ghost45 on 2011-08-04
Sorry I should have been more specific, I am using compiz, I do not want to use the compiz method to remove it. Also, what exactly does the metapackage do?

---

### Post by CatKiller on 2011-08-04
> **ghost45 said:**
> Sorry I should have been more specific, I am using compiz, I do not want to use the compiz method to remove it.

:confused:

It's Compiz that's drawing the shadow. It's very simple to tell it not to. There is no image, it's procedurally generated.

>  Also, what exactly does the metapackage do?

WhiteHorse was trying to be malicious and failing terribly. You should probably just ignore all of that.

If you're interested, though, a metapackage is a package that doesn't install anything. Its only function is to depend on other packages, so that you can install all of them in one step. The *ubuntu-desktop* package, for example, is a metapackage. It depends on all the things that are in the default install so you can get the default install just by installing that. Similarly, if you found that you wanted everything in the default Kubuntu install, you could install the *kubuntu-desktop* metapackage, and so on.

---

### Post by ghost45 on 2011-08-04
Oh I see, and I remember adding an alpha channel to a png image and then erasing the other crap so that the image was just a blank transparent image, then saved it and did logout/login and the shadow was gone....maybe it was for something else?? =/

Also, thanks for telling me about the metapackages. I am still learning a bit about linux so all the help/advice I get helps =]

---

### Post by CatKiller on 2011-08-04
> **ghost45 said:**
> Oh I see, and I remember adding an alpha channel to a png image and then erasing the other crap so that the image was just a blank transparent image, then saved it and did logout/login and the shadow was gone....maybe it was for something else?? =/

Before Compiz was installed by default (and on machines that can't run Compiz) the window manager was Metacity. Metacity themes *are* based on images (it's pretty basic). Perhaps it was for one of those?

> Also, thanks for telling me about the metapackages. I am still learning a bit about linux so all the help/advice I get helps =]It's what we're here for :)

EDIT: Just remembered that although I told you that it was simple to do, I didn't actually tell you how to do it. Install *compizconfig-settings-manager*. Go to the Window Decoration plugin settings and in the "Shadow windows" box, you'll want something like

```
(any) & !(class=Gnome-panel)
``` Play around if there are other windows that you don't want shadows on.

---

