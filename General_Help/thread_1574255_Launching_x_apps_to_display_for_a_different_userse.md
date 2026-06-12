---
title: "Launching x apps to display for a different user/session?"
date: 2010-09-14
forum: General Help
---

### Post by JamesA on 2010-09-14
Hey Guys,

I've tried googling this issue but not sure if I'm entering the correct keywords for what I want, so I'll try and and explain my situation here.

I have two boxes, BoxA and BoxB. BoxA is a laptop, and BoxB is a box connected to a massive screen (mostly used for media but irrelevant.).

Lets say BoxB is logged in with the user James, with x running. Also simultaneously I'm logged into BoxB over SSH on BoxA, also with the user James.

Via SSH, I want to run a GUI app that will open and display on BoxB's session, on the big screen. Not to be confused with tunneling X to BoxA from BoxB.

Rather run an app from James that is logged in via SSH, and the app will display for James running x.

I hope I've made myself clear. 

Many thanks for any advice.
James.

---

### Post by JamesA on 2010-09-14
Figured it out:

```
DISPLAY=0.0: <appname>
```

Or for a specific user

```
DISPLAY=0.0: XAUTHORITY/home/user/.Xauthority <appname> 
```

---

