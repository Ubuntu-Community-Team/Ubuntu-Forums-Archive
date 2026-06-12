---
title: "Making a fullscreen application with several buttons."
date: 2006-04-06
forum: General Help
---

### Post by steffennielsen on 2006-04-06
Hi There,

I'm making a "showroom"-application.

Starting slow, I just need a fullscreen-app, with buttons looking like the attached picture.

Each button has two states, on and off!

I off-state, they have to execute one command, and another command if on-state. (The application is a frontend for the sispm-project: [http://sourceforge.net/projects/sispm](http://sourceforge.net/projects/sispm) - Great app!)

Any ideas on where to start learning? (I have 24 days left of my Windows XP, before it requires activation! - It's in a store - we have to be clean considering licences.)

The day this application is done, I can install Kubuntu on the box instead! :D

Interested in buying Gembird's Power Manager (and you can read Danish), then buy it here: [http://www.elav.dk](http://www.elav.dk) (Any other danish suppliers?)

---

### Post by Neeko on 2006-04-17
There are lots of ways this could be done.

I would suggest either Python with Tk for the GUI, or C++ using QT. Both are quick and easy ways of getting a nice looking app up and running.

If you're in a real hurry you could also use a shell script with Kdialog:
```
kdialog --yesno "some text here"
```

---

