---
title: "Einstein Puzzle Frozen Karmic"
date: 2009-11-27
forum: General Help
---

### Post by Ichido on 2009-11-27
I got hooked on Einstein Puzzle two days ago.
Now the game has "Frozen" my 9.10.
Nothing I do effects this problem.
My mouse and keyboard works.
When I power off my laptop with the power button and reboot, the Einstein Puzzle Screen is there and I cannot shut it down nor take control of my laptop.
Thanks to Puppy 4.3, I here asking for help.
I've tried Crtl+Alt+X, Crtl+Alt+Del with no effects.
I do not want to Re-Install 9.10, but that is looking like my only option.
Thanks for anyone even just reading this post.

---

### Post by bruno9779 on 2009-11-27
Try 
```
control+alt+F1
```
that should open a TTY session.
Log in, then:
```
sudo killall name_of_process
``` If you don't know the name of the process press tab twice instead of writing the name, and it will list all the processes running

(you may have to do it twice)

Then press 
```
ctrl+alt+F7
```

to go back to your desktop

---

### Post by Ichido on 2009-11-27
Thanks bruno9779 :D

---

### Post by bruno9779 on 2009-12-03
No problem.

It is a very powerful key combination, I used to reboot a lot as a linux noob, but never had to do so anymore.

---

