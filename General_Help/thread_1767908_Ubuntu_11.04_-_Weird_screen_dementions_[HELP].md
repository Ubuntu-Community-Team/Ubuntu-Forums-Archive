---
title: "Ubuntu 11.04 - Weird screen dementions [HELP]"
date: 2011-05-26
forum: General Help
---

### Post by BramTerlouw on 2011-05-26
I had 10.10, but as most of the users I upgraded my system to 11.04. Therefore I installed the NVIDEA graphics plugins for a better and smoother experience. However, when I upgraded to 11.04, the screen dementions gone completely mad. I think I have 800x600 now where I should have 1280x1024. Is there a way to reset this to 1280x1024. And most of all, does this have to do with the NVIDEA graphics plugins or the 11.04 update.

I am using:

NVIDEA GeForce 3--- series.
Intel Pentium 4
2GB DDR2 RAM.
Hatachi HD 320GB.

Please help me out, I can't normally visit webpages or anything.

---

### Post by tbrettschneider on 2011-05-26
I think I have the same problem. I am using an external Acer F20 monitor on my laptop and after the update the resolution is so strange that most applications that open in a partial window disappear from my screen.

---

### Post by fdrake on 2011-05-26
did u try to reinstall again nvidea after the update?

---

### Post by ankitmeena on 2011-05-26
Use the nvidia gui i think its nvidia settings or something and change it to what ever you want

---

### Post by Topsiho on 2011-05-26
sudo nvidia-settings

see man nvidia-settings.

Also to be found in (translated from Dutch) System>Administration>NVIDIA X Server Settings

Hope this helps :)

Topsiho

---

### Post by BramTerlouw on 2011-05-26
Ok, I wil try it. Thnx topshibo and others. Good to have some other dutch here. It says unknown monitor and it uses, read it good. 640x480 pixels. instead of 1280x1024...

---

### Post by BramTerlouw on 2011-05-26
O, and for the reinstall of the NVIDEA driver, how can you do that? Using terminal or just the program itself

---

### Post by BramTerlouw on 2011-05-26
Let me attach 2 pictures. [http://imageshack.us/g/853/screenshotph.png/]("http://imageshack.us/g/853/screenshotph.png/") Here you can see the 2 pictures..

---

### Post by Topsiho on 2011-05-26
Hello BramTerlouw,

I could answer you in Dutch, but this is an international forum of course.

I don't really know how to solve this, every time I am confronted with this I google a lot, and roam in forums such as this one. The problem is so common that this problem has been solved many times over and over again.

If you boot your computer, you could select Recovery mode or so (Herstelmodus of zo), and see if in the options you get, you find something like reconfiguring the X server (X-server opnieuw configureren) or something like that.

Probably someone else on this forum can help you better.

Topsiho

---

### Post by BramTerlouw on 2011-05-26
Yes I know. I deinstalled the drivers but now he keeps getting stuck at what he says: Checking battery state at startup, screen dementions are back to normal but it won't start anymore. I will try to get into safe-mode.

Thnx alot.

---

### Post by Topsiho on 2011-05-26
So the dimensions are OK, but something else is playing up now.
There must be somthing in your laptop that Ubuntu doesn't like :(

I wish you luck,

Topsiho

---

