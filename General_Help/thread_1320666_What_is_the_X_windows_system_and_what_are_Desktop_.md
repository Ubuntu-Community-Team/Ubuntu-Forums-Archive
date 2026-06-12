---
title: "What is the X windows system and what are Desktop Environments?"
date: 2009-11-09
forum: General Help
---

### Post by mahela007 on 2009-11-09
What is the X window system and what are Desktop Environments?

---

### Post by bobsmithmoodeyit on 2009-11-09
take a look at wikipedia, it will explain it better here...[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

---

### Post by Giblet5 on 2009-11-09
The X window system is a client/server graphics interface.

Client software provides the GUI, while the X server provides the graphics capabilities and interaction with input devices (keyboard, mouse, tablet, joystick, racing wheel, flight-sim rig, etc)

Imagine Microsoft Windows if networking weren't just a clumsy half-baked add-on afterthought, and you have X.


Desktop environments are usually provided by a "display manager" (code that provides a session), a window manager (provides window management), and a desktop manager (provides menus, desktop icons, etc).

Popular Desktop Environments: Gnome, KDE, XFCE, Motif, VUE, OpenWindows, etc.

---

### Post by mahela007 on 2009-11-10
Thanks for your replies.. 
Could you please explain the X window system with a little more detail?  I don't' see how it would be like windows with or without networking
After reading the wikipedia articles (or the paragraphs at the top atleast) I understood that the keyboard and mouse send signals which are received by the X server. It then sends that information on to the other applications that need it in order to make create output.

That description is pretty brief and leaves a lot of holes (assuming that it is correct in the first place) but I didn't understand much more than that... Could you please tell me more about the details I've missed?

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
The way I understand it is this....
The OS is installed onto your machine as a server. When you log in it initiates a client session where it creates a desktop environment that has remote connection to the OS.... that allows for ultra stable network access (if you needed it) to your install.... thus windows with network support fully integrated. Kind of.

---

### Post by mahela007 on 2009-11-10
What? The OS itself is a server? I though it was only the X windows thing.. 
When you say OS, are you referring to the everything above the kernel?

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
If I understand correctly, then yes, your observations are correct.... however, read my sig.... let someone much more experienced give you a definitive.

---

### Post by JKyleOKC on 2009-11-10
> **mahela007 said:**
> Thanks for your replies.. 
Could you please explain the X window system with a little more detail?To put an image on your monitor screen (any image, whether it's of type or a photo) the machine must specify the color and brightness for each of more than a million picture elements or pixels. To do this in real time so that you can see motion in the image requires many thousands of specific machine instructions. Your video card has specialized hardware which reduces the number of instructions to some degree, but it's still extremely complex and the timing is critical. This collection of video instructions forms a major part of the X Windows System.

The remaining parts deal with the keyboard and with the mouse, which are much less involved but still not at all obvious. When you press a key, the keyboard sends an interrupt signal to the system, which responds by asking for the code that tells which key was pressed. When you release it, the process repeats. The pressed-released cycle then triggers a lookup that translates the keyboard code to an internal code (usually Unicode or ASCII but not always) that's passed on to the running program.

Mouse movement works in much the same way except that the X routines must remember the previous location, determine the current location, and translate this into movement codes to pass on.

To get an idea of what's involved, use Google to locate the xorg source code and have a look. I think you'll agree that trying to understand the whole thing at once is pushing the limit for human cognitive ability!

---

