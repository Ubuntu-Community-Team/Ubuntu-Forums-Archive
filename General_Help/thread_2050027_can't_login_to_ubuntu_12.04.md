---
title: "can't login to ubuntu 12.04"
date: 2012-08-29
forum: General Help
---

### Post by psidrum on 2012-08-29
when i login the user login screen, it would go back to the login screen,

im able to login in virtual terminal cntrl-alt-f1

but unable to login to graphical screen

how do i fix this?

---

### Post by beboylips on 2012-08-29
Smells like a video driver bug to me. X keeps crashing probably. Does your screen turn black and then turns on again at the login screen? If yes, it is very likely that the video driver you installed is not functioning well and X server crashes. Try changing default environment to Unity 2D (right next to the password field in the login screen).

---

### Post by pqwoerituytrueiwoq on 2012-08-29
as beboylips said definably a video driver issue, sounds like lightdm/mdm/gdm is crashing at login which kicks you back to the login screen
but t recommend a course of action we would need to know the hardware
this code will tell us what we need to know
```
lspci | grep VGA
```

---

### Post by Dunpostin on 2012-08-30
Happened to me. I ran ```
rm .Xauthority
``` from a virtual console. Problem was solved.

---

### Post by psidrum on 2012-08-30
after i login it would show a black screen with a line of text like ```
"mount Plymouth         [ok]"
```

then turns black and back to the login screen again,

sometimes it doesnt  turn black

i tried ```
rm .Xauthority 
```it didnt work,

the ```
lspci | grep VGA
``` is Nvidia  G96 GeForce 9600M GT

any other way to fix this?

---

### Post by va7dgp on 2012-09-05
I can't log into my Ubuntu has well. I can access Guest. I'm new at this and I'm at a loss. I have dual boot so I can access window dos and delete a file if I had the name. I used Wubi to load the file This also happen on a Flashdrive I had loaded it on. I just formatted it and loaded puppy on it.

I want to use Ubuntu as I can run Ham Radio Program on the flashdrive and small EeePc. So far this Pass word thing gets in the way

Don
VA7DGP

---

