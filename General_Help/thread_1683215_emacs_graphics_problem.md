---
title: "emacs graphics problem"
date: 2011-02-07
forum: General Help
---

### Post by kakk on 2011-02-07
Hi all,
I have a strange problem with emacs, which seems to appear only when my laptop is connected to external display(s). When I scroll emacs or click on text somewhere, the text becomes ugly and not readable, attached image should explain the problem. Problematic emacs version is 23-gtk, version 22-gtk does not have this problem. I do not also see a problem when running emacs on just the laptop screen, only on external. Laptop is dell latitude 420 with intel 945 graphics
[IMG]http://meteo.physic.ut.ee/~andres/emacs_sample.png[/IMG]

Any help welcome.

---

### Post by kakk on 2011-02-08
Any ideas, graphics card driver or gtk problem?

---

### Post by joonpy on 2011-04-26
I'm using openSUSE, and I have exact the same problem. 

[http://forums.opensuse.org/forums/english/get-technical-help-here/applications/456172-emacs-issues.html](http://forums.opensuse.org/forums/english/get-technical-help-here/applications/456172-emacs-issues.html)

I am using external monitor and intel graphics as well.

---

### Post by joonpy on 2011-04-26
Apparently xorg-x11-driver-video|7.6-53.56.1 update in update repo fixed this problem.

---

