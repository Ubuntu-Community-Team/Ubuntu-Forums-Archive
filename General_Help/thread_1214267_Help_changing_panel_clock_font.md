---
title: "Help changing panel clock font"
date: 2009-07-15
forum: General Help
---

### Post by emissman on 2009-07-15
I've been trying to change my panel clock font using instructions at [http://ubuntuforums.org/showthread.php?t=1033860&highlight=clock+panel+applet+font](http://ubuntuforums.org/showthread.php?t=1033860&highlight=clock+panel+applet+font) and also about halfway down on this page [http://www.gnome-look.org/content/show.php?content=74553&forumpage=17](http://www.gnome-look.org/content/show.php?content=74553&forumpage=17) and can't get the font to change. I've even tried typing the strings out instead of copy/paste.

I've tried removing and re-adding the panel clock applet, killall gnome-panel in a terminal, and also restarting. I don't get the code (instead of clock components) in the panel like someone in that first thread mentioned, it's just the font doesn't change. 

Is there any better way to do this? Any ideas why it wouldn't be working?

Thanks!

---

### Post by emissman on 2009-07-17
Bump.

Anyone?

---

### Post by vinutux on 2009-07-17
> **emissman said:**
> I've been trying to change my panel clock font using instructions at [http://ubuntuforums.org/showthread.php?t=1033860&highlight=clock+panel+applet+font](http://ubuntuforums.org/showthread.php?t=1033860&highlight=clock+panel+applet+font) and also about halfway down on this page [http://www.gnome-look.org/content/show.php?content=74553&forumpage=17](http://www.gnome-look.org/content/show.php?content=74553&forumpage=17) and can't get the font to change. I've even tried typing the strings out instead of copy/paste.

I've tried removing and re-adding the panel clock applet, killall gnome-panel in a terminal, and also restarting. I don't get the code (instead of clock components) in the panel like someone in that first thread mentioned, it's just the font doesn't change. 

Is there any better way to do this? Any ideas why it wouldn't be working?

Thanks!
 just follow that lik..its just nothing editing settings in gconf-editor

---

### Post by emissman on 2009-07-17
> **vinutux said:**
> just follow that lik..its just nothing editing settings in gconf-editor

I did, but the changes aren't applying. The panel clock still stays the default font/style.

---

### Post by vinutux on 2009-07-17
i think u need a restart...

---

### Post by emissman on 2009-07-17
> **vinutux said:**
> i think u need a restart...

From my first post, **I've tried removing and re-adding the panel clock applet, killall gnome-panel in a terminal, and also restarting.**

Thanks

---

### Post by irv on 2009-07-17
> **emissman said:**
> I've been trying to change my panel clock font using instructions at [http://ubuntuforums.org/showthread.php?t=1033860&highlight=clock+panel+applet+font](http://ubuntuforums.org/showthread.php?t=1033860&highlight=clock+panel+applet+font) and also about halfway down on this page [http://www.gnome-look.org/content/show.php?content=74553&forumpage=17](http://www.gnome-look.org/content/show.php?content=74553&forumpage=17) and can't get the font to change. I've even tried typing the strings out instead of copy/paste.

I've tried removing and re-adding the panel clock applet, killall gnome-panel in a terminal, and also restarting. I don't get the code (instead of clock components) in the panel like someone in that first thread mentioned, it's just the font doesn't change. 

Is there any better way to do this? Any ideas why it wouldn't be working?

Thanks!

I tried it and it works.
I just copied the link 
```
<span font = "Times New Roman Bold 12" color="green"> %a %b %d %I:%M </span> 
```
Make sure you put the <...> less then and greater then marks before and after your code and it will work.

---

### Post by emissman on 2009-07-17
> **irv said:**
> I tried it and it works.
I just copied the link 
```
<span font = "Times New Roman Bold 12" color="green"> %a %b %d %I:%M </span> 
```
Make sure you put the <...> less then and greater then marks before and after your code and it will work.

I copied and pasted as well. Still not changing anything. :(

---

### Post by irv on 2009-07-17
> **emissman said:**
> I copied and pasted as well. Still not changing anything. :(
As soon as I added it and closed the edit box by clicking on the [OK] button it changed. See my screen shot and you will see what I did and see the clock turn GREEN.
[ATTACH]121409[/ATTACH]

---

### Post by emissman on 2009-07-17
> **irv said:**
> As soon as I added it and closed the edit box by clicking on the [OK] button it changed.

I completely understand what you're doing to make the change, but it just isn't doing the same thing for me. That is why I started the thread. :confused:

---

### Post by irv on 2009-07-17
> **emissman said:**
> I completely understand what you're doing to make the change, but it just isn't doing the same thing for me. That is why I started the thread. :confused:

I understand, but I don't know what to tell you to do because I can't duplicate the problem. I know you said you did a copy/paste and tried typing so I am not going to ask you to do that again. I am sorry I ran out of options. Maybe your system setup is not exactly like mine, so what ever it is I can't tell.
Sorry:confused:
Irv

---

### Post by vinutux on 2009-07-18
yeh.............just spend some more time with patience.....you can....

---

### Post by ramaswamyps on 2010-05-14
you have to set the format key to custom.
i also struggled to find it.
after reading the edit customkey help shown i was successful

[http://omploader.org/vNGJrMw/Screenshot-1.png](http://omploader.org/vNGJrMw/Screenshot-1.png)

look there

---

