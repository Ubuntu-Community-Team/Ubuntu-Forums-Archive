---
title: "utouch works - and now?"
date: 2010-10-12
forum: General Help
---

### Post by eNoVa on 2010-10-12
Got the Meerkat running, utouch works and now i would like to have some Multitouch fun ;P
What can i do?

How can i link functions to gestures?
How can i use MPX and xinput to create a Cursor for each finger touching the screen(saw something like this on youtube...) ? - is there a script out ?

thanks in advance
eNoVa

---

### Post by Gargoulf on 2010-10-12
Hi,
How can you test utouch? I have installed it but
 then?

---

### Post by eNoVa on 2010-10-15
type "gesturetest 0 0 0xfff" in the terminal and try to make some utouch gestures 
[IMG]http://t0.gstatic.com/images?q=tbn:ANd9GcQdMcuWntl8lKFRvkF79WaSkKB9Y2oh2y80dRmYCooBkKapPnM&t=1&usg=__Gzc7Y9OlyGVbUnz858EUGJwnYN4=[/IMG]  [IMG]http://www.swissitmagazine.ch/imgserver/bdb/316800/316819/420x420.jpg[/IMG]

---

### Post by Captain_Glen on 2010-10-21
Nothing happens.

:'(

What is suppose to happen?

---

### Post by Gargoulf on 2010-10-23
same here. nothing happens.



> **Captain_Glen said:**
> Nothing happens.

:'(

What is suppose to happen?

---

### Post by Cobuntu on 2010-10-28
My HP tx2 runs UNE 10.10 and the only multitouch gesture I could find was tapping with FOUR fingers on the screen brings up the Unity Application menu or makes it go away when it is already open. I can repeat this behaviour anytime, it works flawless.
Can anyone else confirm this gesture?

---

### Post by Tyson S on 2010-10-28
This works on my asus eeetop very much like the mac functions

---

### Post by LtPitt on 2010-10-28
No luck here too...
Any app supporting it?

---

### Post by eNoVa on 2010-10-29
> **Gargoulf said:**
> same here. nothing happens.

Something like that you could see (Attachment).

Today ive found [that (Click!)]("http://ubuntuforums.org/showpost.php?p=10027229&postcount=1272").

I will report after testing it...

greets eNoVa

---

### Post by Cobuntu on 2010-10-30
Yes, apparently as long as there are no multitouch-aware apps you have to have this "GINN" to trick multitouch gestures into keyboard output. On my tx2 this works very well, e.g. for scrolling in every application with two fingers.
Go to [http://ubuntuforums.org/showthread.php?t=1252492&page=128](http://ubuntuforums.org/showthread.php?t=1252492&page=128) and check out post #[**1274**]("http://ubuntuforums.org/showpost.php?p=10037639&postcount=1274") as there was something missing. It only works when you start ginn manually or put it in autostart.

---

### Post by Blubmt on 2011-02-09
Sorry for bumping this, but I just don't get it to work.
I can run grail-gesture on my device and it seem to detect it well, but ginn, utouch-gesturetest etc. just stay silent.
I'm on natty, using packages from here: [https://wiki.edubuntu.org/Multitouch/XDevelopment](https://wiki.edubuntu.org/Multitouch/XDevelopment)

and am transferring my android's touch-screen over to my ubuntu using uinput.

I usually use archlinux where I successfully tested the uinput-created touch device with xi2.1 code, but since I couldn't get ginn to do anything I installed ubuntu in virtualbox and got the repos from the above mentioned link.

Am I missing something? The "touch"-down event seems to be noticed by xorg, as the "Applications" menu entry on top opens up. But ginn still stays silent when I try out gestures. And so does utouch-gesturetest.

EDIT:
Of course this had to happen *after* posting here...:
Found out that when I unmaximize my terminal so that my touches can hit the "root" window, ginn suddenly seems to recognize gestures. Which isn't really that useful because it really only works in the root window, but not in inkscape or firefox...
Any ideas?

---

