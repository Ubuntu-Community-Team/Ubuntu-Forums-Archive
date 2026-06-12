---
title: "Minor Issues when upgrading from 9.10 to 10.04"
date: 2010-05-02
forum: General Help
---

### Post by dfme on 2010-05-02
Hi,
I've just upgraded my laptop and desktop from 9.10 to 10.04.
Here are 2 minor annoyances that I have encountered after upgrading on both machines:
1. The boot splash screen is really ugly. It does not look anything like it should. This is what I would expect: [http://www.blogcdn.com/www.downloadsquad.com/media/2010/03/splash.png](http://www.blogcdn.com/www.downloadsquad.com/media/2010/03/splash.png) . But instead it looks like something from 1999 with garbled text all over the place.
2. Rhythmbox does not show the ubuntu one music store anywhere... why?

2 does not bother me too much. 1 is annoying. I have an Intel GM965 integrated graphics card on my laptop, while my desktop has a nvidia FeForce 8600GT.

Any ideas what went wrong during the update?
Cheers

---

### Post by dino99 on 2010-05-02
South African look and feel  :(

thats not mine too but Mark's one  :P

you can install something different anyway

---

### Post by dfme on 2010-05-02
Ok I figured out what the problem was with the boot splash screen.
Apparently the text plymouth theme was installed (plymouth-theme-text) which is not very nice. Removing this package and installing 'plymouth-theme-ubuntu-logo' got the nicer plymouth theme running :-)

---

