---
title: "How to view older laptop's screen on new laptop over Network"
date: 2011-08-24
forum: General Help
---

### Post by dpacmittal on 2011-08-24
Sorry for the bad title, didn't have any better words to explain what I want.

So I have 2 laptops. The older one's screen is non-functional but everything else works. What I'd like to do is use Xorg to forward its display to newer laptop's screen. I know this is possible, but just don't know how? 

For eg; when I press Ctrl+Alt+f9, older laptop's display comes up. Ctrl+Alt+f8 would show the normal display.

Any help would be appreciated. Thanks :)

---

### Post by linkageless on 2011-08-24
Although I'm sure many find it easy, I've often encountered problems using remote X displays. I would use VNC for this job, in this case with x11vnc to serve up the console using something like: ```
x11vnc -display :0
```

---

