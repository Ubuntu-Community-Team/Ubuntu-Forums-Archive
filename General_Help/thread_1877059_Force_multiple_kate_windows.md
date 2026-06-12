---
title: "Force multiple kate windows"
date: 2011-11-07
forum: General Help
---

### Post by akwatve on 2011-11-07
Hi

I am trying to use kate to open 4 files simultaneously. I have two monitors so the plan is to open two separate windows each having a split screen.

However no matter how much I try kate is adamant and opening only one window. If I want two separate sessions running simultaneously, then there seems to be no way to do it. If I use the command line option -s <SESSION NAME>, it just closes the existing session and starts a new one, which is outrageous.

Any tips on how to open multiple windows using kate (or gedit for that matter) will be greatly appreciated.

Thanks,

---

### Post by oldos2er on 2011-11-07
Have you tried Settings, Configure Kate, Application Sessions, tick the box next to Start new session ?

---

### Post by akwatve on 2011-11-07
That option is already selected.

There are three radio buttons in there.
"Start new session"
"Load last-used session"
"Manually choose a session"

Out of the three "start new session" is checked by default.

---

### Post by supertallrich on 2012-06-05
System Settings -> File Associations -> text -> plain -> Kate -> edit -> Application Tab -> Command -> add "-n" to parameters

---

