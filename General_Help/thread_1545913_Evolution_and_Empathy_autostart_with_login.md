---
title: "Evolution and Empathy autostart with login"
date: 2010-08-04
forum: General Help
---

### Post by homerhomer on 2010-08-04
Here's a neat trick on how to get Evolution and Empathy to start up when you log into gnome. This also hides Evolution to the Indicator Applet, the way it should be. 

--------------

Install alltray
apt-get install alltray

then

Go to System:Preferences:Startup Applications and add the following

Name: Empathy
Command: empathy -h

Name: Evolution
Command: sh -c "sleep 10 ; alltray -na -nt evolution"

---

### Post by dcstar on 2010-08-05
> **homerhomer said:**
> Here's a neat trick on how to get Evolution and Empathy to start up when you log into gnome.
........

Apart from simply putting things in the Startup Applications?

---

### Post by homerhomer on 2010-08-05
If you do that then Evolution will also show up in the task bar and won't be hidden. Yes, with Empathy you can do it, but without the "-h" it will be in the foreground. 

I like to have my communication tools up and running when I log in. I also like them to be out of the way so I can get some work done.

---

### Post by diverbelow on 2010-08-23
> **homerhomer said:**
> Here's a neat trick on how to get Evolution and Empathy to start up when you log into gnome. This also hides Evolution to the Indicator Applet, the way it should be. 

--------------

Install alltray
apt-get install alltray

then

Go to System:Preferences:Startup Applications and add the following

Name: Empathy
Command: empathy -h

Name: Evolution
Command: sh -c "sleep 10 ; alltray -na -nt evolution"

Big Thanks for this. This is what I have been looking for a very LONG time. This saves me so much time and effort.

---

