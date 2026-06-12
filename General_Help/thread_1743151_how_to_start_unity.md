---
title: "how to start unity??"
date: 2011-04-29
forum: General Help
---

### Post by sdowney717 on 2011-04-29
I upgraded to NN
I am running Nvidia 270 driver
The driver works.

As you can see, it is running classic.
At login I select ubuntu not classic

---

### Post by 3Miro on 2011-04-29
You are running classic with no effects. Try logout login again to make sure.

Otherwise, you can try Alt+F2 and then try starting Visual effect by:
```
compiz --replace
```
see what breaks.

If it doesn't work then, try it in a terminal and post the error that you get.

---

### Post by sdowney717 on 2011-04-29
That breaks EVERYTHING, it runs a few things as the screen shuts down and I get a greyish colored screen

Running in terminal does same so I cant post back any info whatsoever.

I have played around with this for an hour and have to force reboot with the power button everytime.
I did find a website that mentioned installing unity, so I did and that broke on reboot, so I had to goto root login and remove it. When removing unity package whatever that is, I removed a lot of other programs around 200 mb worth

This video card is 8400 PCI-e Nvidia and used to run compiz fine.

I did boot into another user and got a one time message saying the hardware does not support unity.

---

### Post by sdowney717 on 2011-04-29
so should I bother reinstalling unity?
is unity going to work with a 8400 gs nvidia card?

---

### Post by sdowney717 on 2011-04-29
[http://www.youtube.com/watch?v=JAVN9isBBok](http://www.youtube.com/watch?v=JAVN9isBBok)

maybe it needs unity2d

---

### Post by 3Miro on 2011-04-29
Install CCSM (compiz-config-setting-manager) and disable both Unity and the top panel. See if it works then.

There may be a bug associated with your specific video card.

---

### Post by sdowney717 on 2011-05-02
I had to do a fresh install.
Now unity works.

---

### Post by Aragant on 2011-09-27
[sdowney717]("http://ubuntuforums.org/member.php?u=209280")
You freshly install ubuntu or just unity..???

---

### Post by ntdoherty on 2012-09-23
> **3Miro said:**
> You are running classic with no effects. Try logout login again to make sure.

Otherwise, you can try Alt+F2 and then try starting Visual effect by:
```
compiz --replace
```see what breaks.

If it doesn't work then, try it in a terminal and post the error that you get.


Yup, this command broke window manager for me too, now I have no menus and no Unity...wtf...don't know how to fix this

---

### Post by sdowney717 on 2012-10-11
> **Aragant said:**
> [sdowney717]("http://ubuntuforums.org/member.php?u=209280")
You freshly install ubuntu or just unity..???

Ubuntu, a fresh install of the OS

I have been using gnome3 for a year and it works well.

---

