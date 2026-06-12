---
title: "I am on stuck"
date: 2006-06-06
forum: General Help
---

### Post by User-007 on 2006-06-06
Hi,

I installed firestarter according to [http://www.ubuntuforums.org/showthread.php?p=1102721&posted=1#post1102721](http://www.ubuntuforums.org/showthread.php?p=1102721&posted=1#post1102721) .


Unfortunately this doen't work with me. When completed all the tasks above and restarted, the firestarter won't open. Furthermore i'll get this:

--------------------------------------------------------------------------------------------
$ sudo firestarter

(firestarter:5526): Gtk-WARNING **: cannot open display:

--------------------------------------------------------------------------------------------

Same problem occurs when trying to start anything with "sudo":

---------------------------------------------------------------------------------------------
$ sudo gedit /etc/sudoers
cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.

---------------------------------------------------------------------------------------------

Now I am really on stuck. Please someone help me to get this solved.

Thanks!
User JB

---

### Post by User-007 on 2006-06-06
Does anyone have any ideas?

User JB

---

### Post by Ramses de Norre on 2006-06-06
There seems to be a problem with gksudo and NOPASSWD lines in /etc/sudoers.
I don't know a fix for it..

---

### Post by xtacocorex on 2006-06-06
Try typing this:

export DISPLAY=:0.0

in the command line before typing:

sudo firestarter. That may fix the display problem, but I'm not sure.

---

### Post by User-007 on 2006-06-06
Thanks but:

------------------------------
$ export DISPLAY=:0.0
$ sudo firestarter

(firestarter:5347): Gtk-WARNING **: cannot open display:
-----------------------------------

Also

----------------------------------
$ sudo gedit
cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.
---------------------------------------

Please give me suggestions

User JB

---

### Post by xtacocorex on 2006-06-06
Evidently the problem is something different than I thought.

Have you tried running it with gksudo instead of regular sudo? I know that some apps won't run if you just use sudo.

Also, you have to use the visudo command to edit your /etc/sudoers file.

---

### Post by User-007 on 2006-06-06
I think it is best to give my typing history for all. Maybe this gives somebody some ideas to give me help

$ export EDITOR=gedit
$ sudo visudo
$ sudo ln -fs /home/USERNAME/.Xauthority /root/.Xauthority (At this point I did a mistake- I forgot to replace USERNAME with my own login name)
$ sudo ln -fs /home/user/.Xauthority /root/.Xauthority
$ sudo chown user.root /home/user/.Xauthority

Thanks
User JB

---

### Post by User-007 on 2006-06-06
I solved the ptoblem. I had a spelling mistake in sudoers file. Now everything works like a charm.

User JB

---

