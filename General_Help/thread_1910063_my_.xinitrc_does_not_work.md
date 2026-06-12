---
title: "my .xinitrc does not work"
date: 2012-01-16
forum: General Help
---

### Post by epic.mint on 2012-01-16
my .xinitrc file does not work could someone please tell me why.
startx only works if i delete the file but then i only get the defualt session.

and could someone tell me how to make startx start a new session of kdm.

i'm using ubuntu 11.10.
 ```
!# /bin/bash

#nitrogen
wbar
#gmrun
terminator
ck-launch-session
exec openbox
#exec choosewm
#exec razor-session
#exec startxfce4
#exec startkde4
#exec tritium
#exec parti
#exec i3
#exec awesome
```

---

### Post by Cheesemill on 2012-01-16
Try changing
```
ck-launch-session
exec openbox

```
To
```
ck-launch-session openbox
```


AKAIK the command **ck-launch-session** should replace the **exec** command.

---

### Post by epic.mint on 2012-01-16
it still won't work
it starts wbar but not openbox so i only get an black screen with the wbar open and no mouse pointer

update: i tried with different window manages but none work.

---

### Post by Cheesemill on 2012-01-16
Try putting an ampersand after wbar and terminator:
```
wbar &
terminator &

```
Without this your .xinitrc will pause after executing wbar and wait for it to terminate before continuing with the rest of the script.

Adding an ampersand will fork the process in the background and immediately continue with the next line.

---

### Post by epic.mint on 2012-01-16
thank you it works now.
may the force be with you always

---

