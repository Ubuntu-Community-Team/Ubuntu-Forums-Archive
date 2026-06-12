---
title: "How to call the X server from a batch file?"
date: 2011-05-29
forum: General Help
---

### Post by apollothethird on 2011-05-29
I'm trying to make a batch file that will create a new Xwindows for family members.  I have my session which I would like to keep running... then simulataneosly allow them to alt-ctrl-F(key) to their session.

I can do it by first going to a text screen and typing:

```
/usr/bin/X :1

or 

/usr/bin/X :2
```Then executing:

```
export DISPLAY=:2
gnome-session
```Then I can use the alt-ctrl-F(keys) to go to the new session.  While it's very simple for me it's complicated for lots of people in the household.  I would like to be able to have those commands performed in a batch file as in:

```
X :2&
sleep 10 # give X a time to start
export DISPLAY=:2
gnome-session&
```Then use the al-ctrl-F(keys) to find the session.

The problem is that the system won't allow me to call X from a batch file.  It errors:

```
User is not authorized to run the X server
```Can someone tell me the magic of being able to start X from a batch file?

I'm using Ubuntu 11.04.

Thanks in advance for input.

– L. James

– 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

