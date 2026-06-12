---
title: "Amarok works for gnome???"
date: 2009-08-14
forum: General Help
---

### Post by franar on 2009-08-14
i installed from repositors amarok on ubuntu 9.04, but as i mentioned before i have not sound, then when i click on mp3 files it shows sometime like 'too many errors'..... 

Amarok works for gnome?

---

### Post by mjwalfredo on 2009-08-14
Amarok definitely works in gnome, I used to run it until I realized that Rhythmbox does everything I really need in a music player.  Can you give any more details on the errors?

---

### Post by credobyte on 2009-08-14
Yes, it works, however, you need to install additional libraries to get it up and running as in Kubuntu ( tip: libxine ).

---

### Post by franar on 2009-08-14
not right now, because at work (where i am now) we use Microsoft, also, yesterday i drop off amarok, 
does Rhythmbox download lyrics? and cd covers?

---

### Post by philinux on 2009-08-14
> **credobyte said:**
> Yes, it works, however, you need to install additional libraries to get it up and running as in Kubuntu ( tip: libxine ).

According to synaptic libxine is not a dependency or suggested. :confused:

---

### Post by franar on 2009-08-14
> **philinux said:**
> According to synaptic libxine is not a dependency or suggested. :confused:

this confuse me again....

---

### Post by colau on 2009-08-14
> **franar said:**
> i installed from repositors amarok on ubuntu 9.04, but as i mentioned before i have not sound, then when i click on mp3 files it shows sometime like 'too many errors'..... 

Amarok works for gnome?
Amarok works fine in ubuntu 9.04.
You can try this too.
```

sudo aptitude install audacious

```

---

### Post by franar on 2009-08-14
> **colau said:**
> Amarok works fine in ubuntu 9.04.
You can try this too.
```

sudo aptitude install audacious

```

i'll try, 
thanks
(what is this for?)

---

### Post by colau on 2009-08-14
> **franar said:**
> i'll try, 
thanks
(what is this for?)
Mp3 player like Amarok.

---

### Post by jocko on 2009-08-14
> **franar said:**
> i'll try, 
thanks
(what is this for?)
Audacious is a music player, similar to old winamp.

---

### Post by credobyte on 2009-08-14
> **philinux said:**
> According to synaptic libxine is not a dependency or suggested. :confused:

I know, I wasn't able to play Mp3 files in Amarok for months ( indeed, I didn't got any errors ). Someone told me about libxine and upon installing it, everything works like a charm :)

---

### Post by mjwalfredo on 2009-08-14
> **credobyte said:**
> I know, I wasn't able to play Mp3 files in Amarok for months ( indeed, I didn't got any errors ). Someone told me about libxine and upon installing it, everything works like a charm :)

I vaguely remember having this same problem with my Amarok install.

Yes, Rhythmbox does download cover art through the use of a plugin.  It also appears to have a plugin  for downloading Lyrics as well but I don't have it installed so I can't say how well it works.

The plugins are easy to set up. It's just a matter of checking a box in the Plugin configuration panel.  In fact, I just turned on the Lyric plugin right now.

I also like the way that Rhythmbox handles my iPods better.  I could never get the eject feature to work quite right in Amarok.

---

### Post by Nate Shoffner on 2009-08-14
It works for me, I use it for my iPod. :guitar:

---

### Post by philinux on 2009-08-14
I bet some people have no problem with amarok because they installed some other player or app that pulled in libxine. Maybe needs a bug report.

---

### Post by jocko on 2009-08-14
> **philinux said:**
> I bet some people have no problem with amarok because they installed some other player or app that pulled in libxine. Maybe needs a bug report.
No bug. Amarok is dependent on kdelibs-runtime, which is dependent on libxine1, which brings the rest of xine.

---

### Post by jmexia on 2009-08-14
try installing this package: phonon-backend-xine.  i was getting the same error ("too many errors encountered on playlist"), and this solved my problem.  it is referenced here in this thread:

[http://ubuntuforums.org/showthread.php?t=270648](http://ubuntuforums.org/showthread.php?t=270648)

good luck!
j.

---

