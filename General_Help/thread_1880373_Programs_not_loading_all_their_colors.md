---
title: "Programs not loading all their colors"
date: 2011-11-13
forum: General Help
---

### Post by terezi on 2011-11-13
for some reason, pretty much any program that isn't chrome seems to have something wrong with it visually. for most programs, colors will be drained and there are weird tv bars across. i took a few screenshots of the effects:

in ren'py, there's the same tv bar look


in world of warcraft, pieces of my characters are flat out missing(not to mention creepy)

in VBA, everything is inverted and runs at less than 50%. the music is just as horrifying

taking pictures with my webcam either doesn't work at all or has the same tv bar effect as ren'py

does anybody have an idea how to fix this?

---

### Post by Cyclane on 2011-11-13
Ok, a problem with graphics. What graphics card and drivers are you using?
```
lspci | grep VGA
lsmod

```

---

### Post by terezi on 2011-11-13
> **Cyclane said:**
> Ok, a problem with graphics. What graphics card and drivers are you using?
```
lspci | grep VGA
lsmod

```

Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

aaaaaaaah, i hope things get worked out :[

---

### Post by Cyclane on 2011-11-13
Googling with the terms 'intel 945GM WoW' gave me the impression that this GPU isn't powerful enough to run WoW.

Best thread I've found is: [http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

---

### Post by terezi on 2011-11-13
it ran on this laptop pretty decently when i was running windows a few weeks ago. i'll try installing it from the how-to, thanks :]

do you know what the deal is with the crazy color bars is? :[

---

### Post by Cyclane on 2011-11-13
Ahh sorry I forgot about that part.

I'll look into that, but first waht is ren'py?

---

### Post by Cyclane on 2011-11-13
Never mind, I've googled it.

In my google search earlier on, I found that the intel GPU has problems with opengl. ren'py defaults to opengl: [http://www.renpy.org/doc/html/display_problems.html](http://www.renpy.org/doc/html/display_problems.html)
Try to choose a different renderer and see what happens

As for your webcam problem, what program do you use?

---

### Post by terezi on 2011-11-13
how do i go about switching my renderer? is it a program-to-program thing or is there a general way to change it?

i use cheese webcam booth. 

i haven't mentioned this yet, so thank you so much for your help so far!

EDIT: i read your link and fixed ren'py. everything else is still screwy unfortunately....

---

### Post by Cyclane on 2011-11-13
I also have a little problem with the webcam, when I load it up the first time after boot I need to go to preferences, change the resolution and then my cam will fire up. After this has happened I can switch it back to the highest resolution and everything is fine.

If this doesn't work for you. would you mind posting a screenshot of the output of the cam?

---

### Post by terezi on 2011-11-13
argh ren'py is being crewy. i guess i'll just give up the ghost on that one.

all pictures with my webcam look like this

sometimes the bars or color get worse, sometimes they're not as bad

[[IMG]http://img4.imageshack.us/img4/9823/webcamzu.jpg[/IMG]](http://imageshack.us/photo/my-images/4/webcamzu.jpg/)

---

### Post by Cyclane on 2011-11-13
```

sudo apt-get install guvcview
guvcview

```
Could you launch guvcview and go to the 'video & files' tab, now try the different options of 'camera output'

---

### Post by terezi on 2011-11-13
yaaaaay! it's fixed! thank you so very much!

---

### Post by Cyclane on 2011-11-13
your welcome, to be honest I didn't expect that to work, glad it did though. Have fun with your Ubuntu install.

Too bad ren'py isn't working for you. :(

---

