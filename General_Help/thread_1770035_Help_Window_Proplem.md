---
title: "Help: Window Proplem"
date: 2011-05-28
forum: General Help
---

### Post by OpenTu on 2011-05-28
Hello Guys ,

why when i play video the system not target the mplayer window so when i press right arrow for forward i can't i should click first in mplayer window then i can forward

same thing when i press Ctrl + Alt + T 
for open terminal  
i can't write anything i should click first by mouse in terminal window  then i can write , Got it ?
  idk how i get this problem i was not have it .

srry for little speak  , please Help .

---

### Post by OpenTu on 2011-05-28
Befor click the window look like this  in every thing i open , video , terminal etc
[IMG]http://uppix.net/9/3/2/c1e44f32b19ac48528e8ed3e0f648.png[/IMG]

After click i can do what i want in the applocation window and the window look like this

[IMG]http://uppix.net/c/e/0/c0c6e25d0a959ee673cbd212a99ef.png[/IMG]


i want to make every window i open look like the 2nd picture wihtout click with my mouse
i was get like that but idk how i get the problem .

---

### Post by lmn. on 2011-05-28
my mouse has this problem upon first use of ubuntu, fixed with [this]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/615892")
bear in mind, depending on your mouse, the fix will be different --however the process will probably be the same..

---

### Post by Ichido on 2011-05-28
> **OpenTu said:**
> Befor click the window look like this  in every thing i open , video , terminal etc
[IMG]http://uppix.net/9/3/2/c1e44f32b19ac48528e8ed3e0f648.png[/IMG]

After click i can do what i want in the applocation window and the window look like this

[IMG]http://uppix.net/c/e/0/c0c6e25d0a959ee673cbd212a99ef.png[/IMG]


i want to make every window i open look like the 2nd picture wihtout click with my mouse
i was get like that but idk how i get the problem .

The ACTIVE window will have the "Full Color" whereas the In-ACTIVE windows will be "Grayed-Out".

---

### Post by OpenTu on 2011-05-28
> **Ichido said:**
> The ACTIVE window will have the "Full Color" whereas the In-ACTIVE windows will be "Grayed-Out".

i know , but i mean when i press Ctrl + alt + T for open terminal
the window will be grayed-out it should be full color without click on the window

other :

when i open video the window should be Active - full color automatic. it be in-Active then i should click with my mouse for make the window active , 

i want when i open apps the window of the app i open Active automatic withput click with my mouse .
srry for little speak

---

### Post by OpenTu on 2011-05-28
> **lmn. said:**
> my mouse has this problem upon first use of ubuntu, fixed with [this]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/615892")
bear in mind, depending on your mouse, the fix will be different --however the process will probably be the same..

the problem not in the mouse  !!

the problem is the system not active the window of the applocation when i run  .
i should click in the window of the app to active it .

Got it ????????????????????????????????

---

### Post by OpenTu on 2011-05-28
Sloooooooooooved !!!


in compiz setting manager 

General Options

Focus & Raise ...

Deselecte Click to Focus ..

Thanks anyway guys

---

### Post by lmn. on 2011-05-28
*:d

---

### Post by OpenTu on 2011-05-28
> **lmn. said:**
> not really, guessing the mouse works fine but the system doesn't know how what to do when you click.

when you click the window, is it activating or not?
or do you want activation on hover?

I did not understand  , anyway i fixed it .
i was when i open somthing the system won't active the window of the applocation i run .
i should click to active . that is .

---

### Post by OpenTu on 2011-05-28
Omg Not Sloved 

when i deselected the click to focus option now
when i move the mouse the window gonna be active . without click but i should move the mouse to the window , i want without do anything just when i press ctrl+alt+t the terminal window gonna be active please help  .

---

### Post by lmn. on 2011-05-28
it's a strange problem,
normally the window is activated upon opening the program, and if i understand you properly, it isn't doing this.

so it's not a case of changing settings to do with how the mouse interacts with the windows, instead how the system defines how the window is shown upon opening

I don't know where these settings can be changed, sorry :S

---

### Post by OpenTu on 2011-05-28
Fixed With this Command "gconftool-2 --recursive-unset /apps/compiz-1"

Thanks anyway guys 

thanks lmn.

---

