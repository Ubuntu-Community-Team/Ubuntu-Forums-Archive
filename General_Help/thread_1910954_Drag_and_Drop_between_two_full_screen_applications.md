---
title: "Drag and Drop between two full screen applications"
date: 2012-01-18
forum: General Help
---

### Post by gepponline on 2012-01-18
...ma ciao!

  I'm an Ubuntu 11.10 user on a asus netbook so i use quite always full screen windows for every program.
I found that if i want to drag and drop a file from a windows to another behind, there's no way to do it.
Is this correct?
I expected that if I drag a file to the unity bar, the bar should appear to show me applications and get windows in full screen mode to drop the file but it's not.
So, should i report this as a bug? I have to ask for a new feature or there's an unknown solution for this problem?

thank you!

---

### Post by sudodus on 2012-01-18
Most of the time but not always you can copy (mark or ctrl c) and paste (if marked: press middle button, if ctrl c: press ctrl v) instead of drag and drop.

But it is possible to drag from a window and drop into a fullscreen application, so you can exit fullscreen of the 'source' application just during the operation.

---

### Post by gepponline on 2012-01-18
I don't have problem on how to drag and drop files.
There are many alternative ways to place a file in another window/application.
The "problem" is that the drag and drop functionality is "corrupted". With the bottom application bar (before unity) i can do this.
Now i can not and I think it is a step backward.
If there is no way to do what i want to do maybe i should open a bug report.

---

### Post by sudodus on 2012-01-18
I see what you mean.

Well, there are ways to tweak Unity. And you can install another desktop environment, that might be more convenient for your way to run a computer. Have you tried Kubuntu (or KDE)?

---

### Post by ptsubin on 2012-01-18
I haven't used unity much as I immediately switched to gs. Doesn't the sidebar come up if i move the mouse pointer to screen bottom left? Will it give me a switched window if i keep the mouse pointer still holding the dragged file on the required application icon?

---

### Post by gepponline on 2012-01-18
> **ptsubin said:**
> Doesn't the sidebar come up if i move the mouse pointer to screen bottom left? 

No It doesn't I expected it to do so, but it doesn't.

> **ptsubin said:**
> Will it give me a switched window if i keep the mouse pointer still holding the dragged file on the required application icon?

No sidebar, so no application icon :(

---

### Post by gepponline on 2012-01-18
> **sudodus said:**
> Have you tried Kubuntu (or KDE)?

I don't want to change my desktop envoironment.

I'd like to know if there is a way (that i don't know,for example i have to drag a file holding a keyboard key or something similar..) to do what i want or if i have to report this problem to the Ubuntu devloopers.

---

### Post by apochry on 2012-01-18
Hello there,

You can drag and drop a file from window on a  app icon in the launcher, which supports this file format. This will open the file in new window of the application.
But dragging a file to an icon of a running app will not show you the window of this app. This functionality is not implemented.  I do not think that you have to report a problem or bug. You should give an idea at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) or something like that.
I guess that the Unity developers think that this feature is not that necessary, so they didn't provide it. This is something what I used to miss to when i moved do Unity.

Regards,
Christo

---

### Post by gepponline on 2012-01-18
> **apochry said:**
> 
You can drag and drop a file from window on a  app icon in the launcher, which supports this file format. 

NO I DON'T!

If the window is full screen, the sidebar with launchers do not appear when i drag the file to the left of the screen.

---

### Post by apochry on 2012-01-18
Well, it should do this. It does it for me. Install MyUnity and try the different options under launcher/Behavior. With fixed launcher the drag and drop will work for sure. :) For me the launcher appears with both of the "Smart" & "Avoid windows" options when dragging a file. If it doesn't work for you, you may try reinstalling the ubuntu-desktop.

---

### Post by gepponline on 2012-01-19
Yes, with fixed launcher all works fine,
 but with all other options the launcher doesn't appear when i drag a file to the side of the screen... :(

---

### Post by apochry on 2012-01-19
Try ```
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
```

---

### Post by gepponline on 2012-01-20
I've reinstalled ubuntu-desktop and it seems to work now (even if sometimes it doesn't).

However, it is a good thing that it show me only applications compatible with the file I'm dragging, but it consider them as applications and not as windows, so if i want to drag a file to the VLC playlist for example, dragging a file on the VLC icon make it open a new instance of VLC.
I think it should be more friendly if it opens a preview of the VLC windows let me choosing in which window drop the file. Like i used to do with the old application bar.

---

### Post by apochry on 2012-01-20
I know, this what I miss with Unity too. Unfortunately it's not like that. Although this not a bug, it's simply not implemented.  You may submit this as an idea at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) and tell your Ubuntu friends to vote. :) Good luck! If you do it let me know, so I can vote too.

Regards,
Christo

---

