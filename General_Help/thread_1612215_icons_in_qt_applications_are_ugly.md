---
title: "icons in qt applications are ugly"
date: 2010-11-02
forum: General Help
---

### Post by Lin0 on 2010-11-02
I guess I did not use the correct key words to search for a solution. So if it is a silly question, please don't laugh at me :P

Here is the screenshot for normal outlook in my ubuntu 10.04, with theme Ambiance. They are fine.
[IMG]http://i334.photobucket.com/albums/m402/lynn1653/coding/Screenshot-ThemeDock.png[/IMG]

But for the application written by myself in Qt, the buttons seem to be ugly.
[IMG]http://i334.photobucket.com/albums/m402/lynn1653/coding/RenderEffEdi.png[/IMG]

How can I deal with it?

Thank you very much!

---

### Post by Lin0 on 2010-11-03
up :)

---

### Post by Lin0 on 2010-11-04
:cry:

---

### Post by Lin0 on 2010-11-08
Still have not found the solution ...:(

---

### Post by mister_playboy on 2010-11-09
Do you have QT installed on your machine?  Do other QT apps look OK?  If you start your app from the terminal, do you get any errors?

Looks like the window is being displayed with an ugly X default rather than calling QT.

I've seen this same behavior with windows opened by a Adobe Flash interface.

---

### Post by Lin0 on 2010-12-10
Thank you for the reply :D
Finally I find a way to solve it, but perhaps not a good one ...
Use qtconfig to set a special GUI Style for Qt Applications. I choose "Cleanlooks". 
When it is "Desktop Settings (default)", it is still the X default style ... :cry:

Every time I install ubuntu, I met such problem. Last time I forgot what package did I install and after that, qt application use the same theme as the system. I am sure there is something I should have done while updating the system after installation ...

---

### Post by 4Orbs on 2010-12-10
Just a guess... maybe try adjusting the qt settings as root (sudo). That way they will always remain as cleanlooks regardless of which gnome theme you choose.

---

