---
title: "How to recovery Ubuntu 11.04"
date: 2011-06-05
forum: General Help
---

### Post by figigigi on 2011-06-05
Hi,

I really messed up my ubuntu 11.04 while i was playing with the features of compiz.I can only see a few folders of mine and nothing else on my screen.I can't access anything.No left hand pannel or top pannel. Even though i restart it.It stayed same and that's very annoying.Can you tell me what terminal codes should i write to make recovery?

Thank you.

---

### Post by yetiman64 on 2011-06-05
> **figigigi said:**
> Hi,

I really messed up my ubuntu 11.04 while i was playing with the features of compiz.I can only see a few folders of mine and nothing else on my screen.I can't access anything.No left hand pannel or top pannel. Even though i restart it.It stayed same and that's very annoying.Can you tell me what terminal codes should i write to make recovery?

Thank you.

If you can get a terminal up try the code,

```
unity --reset
```

Try the keyboard combination of CTRL + ALT + T to bring up a terminal if you can't access the sidebar.

---

### Post by ghostborg on 2011-06-05
Using CompizConfig Settings Manager
To launch it from terminal: ccsm
I found when you mess with the compiz settings in 11.04 it resets some basic items and you need to re-select them.
General -> Composite and OpenGL
Extras -> Window Decoration .
Window Management -> Maximize, Move Window, Resize Window.

Additional:
I am running 11.04 Gnome Classic desktop from which I understand that Unity runs on top of.
You could login at the login screen click on your user name and then at the bottom alternative installed desktops will appear. Select the one you want and then your password.

---

### Post by IWantFroyo on 2011-06-05
Log into Ubuntu Classic before ghostborg's suggestion. It will make it easier.

---

### Post by figigigi on 2011-06-05
i just recovered and come to the old version 10.10 with the all software i have in 11.04. Now i tried that code unity--reset.It seems something is happening but then it turns to the 10.10 again

there are those on terminal lastly

Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected
Compiz (bailer) - Info: Ensuring a shell for your session
figen@figen-Satellite-A350:~$ Cannot register the panel shell: there is already one running.

---

### Post by figigigi on 2011-06-05
> **IWantFroyo said:**
> Log into Ubuntu Classic before ghostborg's suggestion. It will make it easier.

I tried that but nothing changed.

---

### Post by figigigi on 2011-06-05
> **ghostborg said:**
> Using CompizConfig Settings Manager
To launch it from terminal: ccsm
I found when you mess with the compiz settings in 11.04 it resets some basic items and you need to re-select them.
General -> Composite and OpenGL
Extras -> Window Decoration .
Window Management -> Maximize, Move Window, Resize Window.

Additional:
I am running 11.04 Gnome Classic desktop from which I understand that Unity runs on top of.
You could login at the login screen click on your user name and then at the bottom alternative installed desktops will appear. Select the one you want and then your password.

I did what you said but it didn't turn to 11.04. If you have a skype,can i show my screen to you?

---

### Post by IWantFroyo on 2011-06-05
The panels are missing? That's a different issue.

What I meant is that it would be easier to open ccsm in Ubuntu Classic.

So are the panels missing in Ubuntu Classic? If not, open ccsm in there and try to change the settings to how they were before.

---

### Post by figigigi on 2011-06-05
> **IWantFroyo said:**
> The panels are missing? That's a different issue.

What I meant is that it would be easier to open ccsm in Ubuntu Classic.

So are the panels missing in Ubuntu Classic? If not, open ccsm in there and try to change the settings to how they were before.

I don't remember how they were before. I opened ubuntu classic and now it is in the 10.10 format.I want to change it to the 11.04 version again.Will it change it if i just delete compiz? I hate it now,I can  do that:)

---

### Post by figigigi on 2011-06-05
i type that 
```
unity --reset
```

and it turned back to 11.04 but the terminal is still processing and seems like never finished please check the picture out.

---

