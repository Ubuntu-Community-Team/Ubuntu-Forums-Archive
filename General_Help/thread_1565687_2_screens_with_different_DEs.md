---
title: "2 screens with different DEs"
date: 2010-09-01
forum: General Help
---

### Post by Abhinavhardikar on 2010-09-01
Is this possible:
[IMG]http://i53.tinypic.com/51at8j.png[/IMG]

I tried everything but Gnome extends its desktop on screen2

I have an nvidia FX5500

---

### Post by ean5533 on 2010-09-01
This is a very interesting question, and something that I've never considered before. My immediate gut reaction to the question was "No", but I decided to do some Google'ing before I spat out an answer.

Unfortunately I couldn't find anyone even *talking* about the issue, let alone saying whether it was possible. I'm assuming the answer is no; having two desktop environments running at the same time seems pretty complicated. 

Still, I'll do a little more looking around and keep an eye on this thread too. Could be a fun project for someone more skilled than I.

---

### Post by Abhinavhardikar on 2010-09-01
Well this is possible but if i do that nautilus-elementary crashes! If somebody can help me with seperate X screens in X and nautilus elementary!

---

### Post by francf on 2010-09-01
There's an open bug about separate x-screens and nautilus-elementary
[https://bugs.launchpad.net/nautilus-elementary/+bug/596348](https://bugs.launchpad.net/nautilus-elementary/+bug/596348)
This gonna be fixed soon for Lucid. (at least that said ammonkey on a post)

---

### Post by sikander3786 on 2010-09-01
Really interesting question. Not possible so far I believe.

Still you can have one say GNOME based distro as a host and KDE based distro as a client in a Virtual Machine and vice versa, both running on two different screens. Functionality will be the same as you need.

Regards.

[COLOR="Red"]EDIT:[/COLOR] The client distro will be a little slower than the one on the actual hardware and will most probably have no 3D effects.

---

### Post by scorp123 on 2010-09-01
> **Abhinavhardikar said:**
> Is this possible: 

You could do a 2nd nested X11 server and then display KDE inside of it.

Read here for the basics:
[http://ubuntuforums.org/showthread.php?t=620003](http://ubuntuforums.org/showthread.php?t=620003)
[http://www.dedoimedo.com/computers/xephyr.html](http://www.dedoimedo.com/computers/xephyr.html)
[http://www.xs4all.nl/~matto/xnest.html](http://www.xs4all.nl/~matto/xnest.html)

... Once you have Xephyr (or Xnest) running you can change your $DISPLAY variable and launch processes inside that 2nd/nested X11 session.

```
export DISPLAY=:1.0
```

Whatever you launch after that should be launched inside the nested X11 server and not in your GNOME session anymore. Please try it e.g. by launching a clock?
```

export DISPLAY=:1.0
xclock 
```

If that works then KDE will work too ... KDE can be launched with the **startkde** command:
```
export DISPLAY=:1.0
startkde
```

Taddaaaaa ... KDE alongside GNOME.

The magic trick will now be to find the right parameters to get the Xephyr window into the right dimensions so it really does cover only the other screen. You'll have to play with it a little.

---

