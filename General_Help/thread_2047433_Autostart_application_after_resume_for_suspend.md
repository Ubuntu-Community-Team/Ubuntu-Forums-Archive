---
title: "Autostart application after resume for suspend"
date: 2012-08-24
forum: General Help
---

### Post by PT PinGuy on 2012-08-24
Hello all,

I have a script to enable the scroll with 2 fingers, that I add to autostart applications. It works fine, but when I resume for a suspend mode, the function of the touchpad don't work and I have do run the script manually.

What is the problem?

Thanks.

---

### Post by OM55 on 2012-08-24
I am not sure what the problem is but (or in case you cannot find a solution and yet are looking to bypass the problem), here is a quick workaround that may make your life easier:

Cuttlefish is a useful event driven monitor/launcher. It runs in the background and could easily lunch your script every time you unlock your screen.
Notice however that in your case the event it can sense is the action of unlocking the screen, not the waking of the laptop from suspend mode. Meaning, if you keep your screen regularly unlocked and do not require to type in a password after wake-up, this may not work for you. 

Anyway, to install:

```
sudo add-apt-repository ppa:noneed4anick/cuttlefish
sudo apt-get update
sudo apt-get install cuttlefish
```Hope that helps!

---

### Post by PT PinGuy on 2012-08-25
First I want to say tank you for this help.
I don't use the screen lock, but I use wireless, and I use this stimulus to start the script.

Thanks.

---

### Post by OM55 on 2012-08-25
You are very welcome.

(and now you can change this thread to 'Solved' for others to see...)

---

