---
title: "VirtualBox Icon"
date: 2009-07-27
forum: General Help
---

### Post by nmaster on 2009-07-27
I use the closed source version of VirtualBox.  I have no problems with it, but how do I get an icon for the launcher?  I want the virtualbox icon instead of that spring-board thing.

---

### Post by lukeiamyourfather on 2009-07-27
I had the same problem with the closed source version 3.0.0 a few weeks ago. After restarting or logging out there should be an icon for VirtualBox on the applications menu, then right click it and add it to the launch panel from there. It won't show up right after an install though which is a little weird. Cheers!

---

### Post by nmaster on 2009-07-27
i've been using it for about a week now and nothing like that has happened.  is there a *.svg i can download and put in the directory with the other icons?

---

### Post by nmaster on 2009-07-27
bump.

---

### Post by nmaster on 2009-07-29
bump.  does anyone know how i can get the icon?  can't i just 'wget' it from somewhere?

---

### Post by spcwingo on 2009-07-29
It's not under /usr/share/pixmaps?

---

### Post by For The People on 2009-07-29
There is a high quality png you can dl off of google. It's a rather large image so scaling should not be a problem unless your going to make it huge! 
[http://37prime.files.wordpress.com/2009/07/virtualbox.png](http://37prime.files.wordpress.com/2009/07/virtualbox.png)

or

[http://i170.photobucket.com/albums/u248/nagayanobu/RequestZGitRDun8705-ByNagaya.png](http://i170.photobucket.com/albums/u248/nagayanobu/RequestZGitRDun8705-ByNagaya.png)

---

### Post by nmaster on 2009-07-29
> **For The People said:**
> There is a high quality png you can dl off of google. It's a rather large image so scaling should not be a problem unless your going to make it huge! 
[http://37prime.files.wordpress.com/2009/07/virtualbox.png](http://37prime.files.wordpress.com/2009/07/virtualbox.png)

or

[http://i170.photobucket.com/albums/u248/nagayanobu/RequestZGitRDun8705-ByNagaya.png](http://i170.photobucket.com/albums/u248/nagayanobu/RequestZGitRDun8705-ByNagaya.png)

I had no problem finding those, but I can't set those as the icon for the launcher.  When I go to Properties and click on the spring-thing to change it icon it takes me to /usr/share/icons/hicolor/scalable/apps/  All the icons there are *.svg and a *.png doesn't seem available as an icon.  How can I change the image format and size? I have (but am not familiar with) GIMP.

---

### Post by Olav on 2009-07-29
> **neal.m.master said:**
> it takes me to /usr/share/icons/hicolor/scalable/apps/  All the icons there are *.svg and a *.png doesn't seem available as an icon.
That is because you are in the "scalable" directory, and PNG isn't scalable. But you can browse to any other directory you want, and it will find all graphics files that reside there.

The open source Virtual Box places its icon in /usr/share/pixmaps/VBox.png, have you looked there? Just to be sure I'll attach the icon I have to this post.

---

### Post by nmaster on 2009-07-29
wow, duh.  i guess when i browsed i didn't see the files.  i thought i was browsing for the files, not the directory that the files were in.  thanks!

---

### Post by Olav on 2009-07-29
> **neal.m.master said:**
> i thought i was browsing for the files, not the directory that the files were in.
I agree it is somewhat counter-intuitive. I believe it is done this way for a reason though. If by navigating around you would happen upon a directory with hundreds of icons/graphic files that you would have to wait for to be displayed, you can see how that could become annoying quite quickly.

So this is just one of those little compromises in user-friendliness that we have to live with I guess.

---

### Post by Pierre Thibault on 2012-12-14
> **For The People said:**
> There is a high quality png you can dl off of google. It's a rather large image so scaling should not be a problem unless your going to make it huge! 
[http://37prime.files.wordpress.com/2009/07/virtualbox.png](http://37prime.files.wordpress.com/2009/07/virtualbox.png)

or

[http://i170.photobucket.com/albums/u248/nagayanobu/RequestZGitRDun8705-ByNagaya.png](http://i170.photobucket.com/albums/u248/nagayanobu/RequestZGitRDun8705-ByNagaya.png)

Using virtualbox.png by changing the icon for Virtualbox using alacarte has solved the problem for me.

Thank you.

---

