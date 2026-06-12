---
title: "how to set a default workspace"
date: 2011-01-27
forum: General Help
---

### Post by &gt;hankim&lt; on 2011-01-27
Hello, 
As the caption says I wonder If there's a way to set a default workspace, I mean for when I boot my PC to be in a determined workspace.
Thx a lot.
By the way what does it mean that I've spilled my beans? I'm sorry for that...

---

### Post by AlphaLexman on 2011-01-27
> **>hankim< said:**
> By the way what does it mean that I've spilled my beans? I'm sorry for that...

It is just a silly quote about how many posts you have. Although it is not very logical I have noticed, so don't worry about the words to beans ratio, it is inconsistent.

---

### Post by Frogs Hair on 2011-01-27
Hi,

Could you be a little more specific , I consider the user account to be a default workspace . Do you mean via the workspace switcher ? or a group of programs to be opened automatically when you log in.

---

### Post by Krytarik on 2011-01-27
Unfortunately I didn't find a way to *start* on a given workspace, but there is a quite simple way to automatically *switch* to it after login: use the program "wmctrl".
```
sudo apt-get install wmctrl
```As of now, the usual option "-s WORKSPACE" to switch to a given, numbered workspace doesn't work. You have to use "-o x,y" instead.

Example: I have a resolution of 1152x864
```
wmctrl -o 1152,0
```switches to the workspace left of the first, default one
```
wmctrl -o 0,864
```switches to the workspace below of the first, default one

Then simply put the desired command in "System -> Preferences -> Startup Applications".

---

### Post by MrZarq on 2011-03-16
I tried this in 10.04, and the command worked. But it didn't do anything when I placed it in StartUp-programs. 
I put some testscripts in there and they ran, so it isn't my StartUp that's the problem.

I'm thinking maybe the command is run before the windows manager is fully started perhaps?

Does anybody know how to solve this decently?

---

### Post by Krytarik on 2011-03-16
> **MrZarq said:**
> 
I'm thinking maybe the command is run before the windows manager is fully started perhaps?
Exactly. If you run it from Startup Applications, you need to delay its execution until the desktop is loaded, for me it's some 13 secs. To do so, you have to put the command in the launcher like this:
```
sh -c "sleep 13;wmctrl -o 1152,0"
```
Greetings.

---

### Post by MrZarq on 2011-03-16
That what I thought about. I thought there was perhaps a more elegant solution. Thanks anyway!

---

### Post by Krytarik on 2011-03-16
> **MrZarq said:**
> I thought there was perhaps a more elegant solution.
Nope, unfortunately it isn't.

---

