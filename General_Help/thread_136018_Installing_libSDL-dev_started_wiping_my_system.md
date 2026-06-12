---
title: "Installing libSDL-dev started wiping my system"
date: 2006-02-25
forum: General Help
---

### Post by Dingo_aus on 2006-02-25
I've been using Kubuntu for about a week now, very inpressed.

Anyway I decided to start programming SDL apps, to that end I fired up adept and started installing dev packages left, right and center.

I believe I was installing libsdl-dev when it started removing (deleting) 402 packages. Ones such as Firefox, Acrobat Reader and a heap of other stuff not connected to SDL as far as I could see.

I killed it as soon as I could but it took down a lot of my system.

Yes I had enabled the Universe repository.

I tried to log back into KDE but was told no "x session manager" or similar.

Thankfully it didn't take out apt-get and I can start installing things from the command line again.

This bites as I just spent all day tweaking everything the way I wanted it.

So has anyone else found this with certain packages?
Is it a maliciously designed package? or an error or something else?

How can it be prevented in future?

Thanks,

Dingo_aus,
Brisbane, Australia

---

### Post by Perfect Storm on 2006-02-25
You proiperly choosed the wrong sdl-dev package. The reason it want to uninstall the other packages is that it will conflict with your defaults. So a chain reaction will happen (dependncy).
Where did you get this sdl-dev package?

You sure it was the right package?

libsdl1.2-dev
Just test it and works fine.

---

### Post by lamego on 2006-02-25
If you added non ubuntu repositories  to your list contaning a sdl dev package that could easly cause this problem.

---

### Post by Dingo_aus on 2006-02-25
hmmmm, interesting.

I'm not sure exactly what package it was - my best guess would be libsdl-dev

I've re-installed kde now, so I'm back up and running (and loving ubuntu).

What can I do to prevent this in future?

Is there an option in apt-get to prompt before removal etc?

---

