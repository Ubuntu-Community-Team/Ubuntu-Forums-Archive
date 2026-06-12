---
title: "Missing Window Frames"
date: 2012-05-27
forum: General Help
---

### Post by gprestonmoto on 2012-05-27
The frames around windows have disappeared. Driving me nuts. Trying to figure out what's going on as I didn't change anything. It's really frustrating and doesn't allow me to move any windows around my screen, nor minimize them. I posted a video of how it looks here.

[http://youtu.be/zLvZ2AHLwD4](http://youtu.be/zLvZ2AHLwD4)

---

### Post by zombifier25 on 2012-05-27
Are you sure you didn't do anything in CompizConfig Setting Manager? Either case, open a terminal and type this command:
```
unity --reset
```
It should reset Compiz's profile.

---

### Post by jrisreal on 2012-05-27
> **zombifier25 said:**
> Are you sure you didn't do anything in CompizConfig Setting Manager? Either case, open a terminal and type this command:
```
unity --reset
```It should reset Compiz's profile.
I agree with this.  You probably unchecked "Window Decoration" in Compiz or something.

---

### Post by JOHNNYG713 on 2012-05-27
```
compiz --replace
```

---

### Post by gprestonmoto on 2012-05-27
> **JOHNNYG713 said:**
> ```
compiz --replace
```


WIN. thanks bro

---

