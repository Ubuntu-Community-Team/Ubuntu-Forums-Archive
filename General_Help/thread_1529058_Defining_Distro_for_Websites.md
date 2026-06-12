---
title: "Defining Distro for Websites"
date: 2010-07-11
forum: General Help
---

### Post by dodle on 2010-07-11
I have a project at sourceforge.net.  In the project settings I can set the default downloads for different platforms.  The options are Linux, Mac, Windows, BSD and Solaris.  So Sourceforge checks the system which is accessing the project and displays the default download for that system.  My question is about Linux distros.  Would there be any way for Sourceforge, and other sites, to check which type of distro the visitor is using?  

Here is why I ask:  I have two different downloads, a .deb for Debian systems, and an .rpm for Red Hat systems.  But I can only set one default download for Linux in general.  So, if I set the .deb as the default, Red Hat users will see the .deb.  

If this can be done, I'd like to recommend it to Sourceforge.  But, since they haven't done it yet, it makes me think that maybe it isn't possible right now.

Also:  I apologize if this is not a good forum in which to place this thread.  I wasn't sure where I should ask.  I don't think it is directly related to development or packaging and compiling.

---

### Post by Nonno Bassotto on 2010-07-11
The name of the distribution is usually available in the [user agent]("http://en.wikipedia.org/wiki/User_agent") of the browser. This is a string like
```

Mozilla/5.0 (X11; U; Linux i686; it; rv:1.9.2.6) Gecko/20100628 Ubuntu/10.04 (lucid) Firefox/3.6.6

```
(this is currently mine) which identifies the browser and gives some information. You can see yours [here]("http://whatsmyuseragent.com/").

Keep in mind that this string is sent by the browser while asking for a resource, like a web page, so the user can modify it at will. It follows that it is not completely reliable (but usually is).

The question, then, is whether SourceForge lets you access this bit of information. I don't know how customizable the SourceForge pages are. On a custom site you would be certainly able to do what you ask.

---

### Post by dodle on 2010-07-11
Interesting.  So if I had downloaded firefox and compiled it myself, it wouldn't have the Ubuntu information in it, would it?  So if Sourceforge did do something like this, they would be dependent on the users installing the distro's browser, correct?

No, the Sourceforge pages aren't that customizable.  That's why I would recommend it to them, so they could make the change themselves.

---

### Post by Nonno Bassotto on 2010-07-11
I think that they are getting the operating system from the user agent anyway. So using it to differentiate between distros would certainly not hurt.

---

### Post by dodle on 2010-07-11
I think I'll make that recommendation to them, thanks.

---

### Post by uRock on 2010-07-12
You may find more by asking on the [Fedora]("http://forums.fedoraforum.org/showthread.php?t=240131") site. Their forum shows what OS and browser a poster was using when the poster made a post.

---

