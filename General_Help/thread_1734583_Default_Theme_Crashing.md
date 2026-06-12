---
title: "Default Theme Crashing"
date: 2011-04-20
forum: General Help
---

### Post by tylerjg33 on 2011-04-20
My default Ubuntu theme (and all the other smooth and new looking ones that ive tried) crash one or two minutes after logging in. My computer is up to date! The theme it gets set to is older and boxy looking. The question is, then, how do I get the default Ubuntu Theme to work when it crashes shortly after logging in? Thanks for your time.

(linux noob by the way):confused::confused::confused:

---

### Post by Krytarik on 2011-04-20
It seems to be related to this:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

Recent threads with summed-up workarounds:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

Greetings.

---

### Post by tylerjg33 on 2011-04-20
Thanks man. could it have anything to do with my radeon graphics card also?

---

### Post by Krytarik on 2011-04-20
> **tylerjg33 said:**
> could it have anything to do with my radeon graphics card also?
Not necessarily, this is apparently a very widespread bug. The cause of this is actually that the gnome-settings-daemon of the started session is run before those of the login screen has been stopped.

---

### Post by tylerjg33 on 2011-04-20
the startup application code works well, but every time I save a picture or download anything, it reverts back to the older theme...thanks for the continued help by the way. its really appreciated. :(. I just plug the code in the terminal to get it how i want it to look, but that gets tedious.

---

### Post by Krytarik on 2011-04-20
> **tylerjg33 said:**
> the startup application code works well, but every time I save a picture or download anything, it reverts back to the older theme
So, that's not the usual bug! When did it start? Also, I did assume that you are running 10.10. Is that correct?

---

### Post by tylerjg33 on 2011-04-21
Yes 10.10. It did it a few times over the last month or so, but yesterday it did it when i logged in (which is what it did before) so i restarted, and the problem persisted. If this means anything, when i start my computer it usually takes a second and i get a message saying that my graphics card turbo mode is disabled. it switched screens and ubuntu loads right after though, so i can never catch what the whole message is saying. I should try and write it down. Like I said, I am a linux/ubuntu novice :frown:](*,)](*,)

---

### Post by Krytarik on 2011-04-21
You can check "/var/log/messages" for the full error message.

Also, please check if those issue also occurs within a LiveCD, preferrably with the latest beta of Natty 11.04, to possibly not have the usual bug:
[http://www.ubuntu.com/testing/natty/beta](http://www.ubuntu.com/testing/natty/beta)

---

