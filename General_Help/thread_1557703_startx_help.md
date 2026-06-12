---
title: "startx help"
date: 2010-08-21
forum: General Help
---

### Post by Zirts on 2010-08-21
Hi,

Whenever I try to use startx 'which wine' WoW.exe

I get the error: No protocol specified
And when that comes I always have to restart the machine as theres no way to stop the Alt-Ctr-F2 telling me that error.

Is there anyway to fix this? And is there a way to start other games too like that not just WoW, for instance Doom3.

---

### Post by orethrius on 2010-08-21
Why are you starting the game as an X session?

Honestly, if the games installed properly, they should be under Applications > Wine > Programs in the Main Menu.  If Wine isn't installed, **which wine** will display nothing, and the program will fail to start (no 'Wine' present).

---

### Post by Zirts on 2010-08-21
Wine is installed, I want to try out the performance when a game is started like that, atm I'm having a nice 6FPS when walking outdoors in WoW, and people say you get a sweet ca20FPS increase when starting it like that.

Mby I'm using wrong sybols around which wine? I do it like that:

startx 'which wine' WoW.exe

But on the WoW on Ubuntu page it's like this: startx `which wine` WoW.exe

The sybols are a bit different. But I have no idea where I can get them on my own keyboard...

---

### Post by orethrius on 2010-08-21
> **Zirts said:**
> Wine is installed, I want to try out the performance when a game is started like that, atm I'm having a nice 6FPS when walking outdoors in WoW, and people say you get a sweet ca20FPS increase when starting it like that.

Mby I'm using wrong sybols around which wine? I do it like that:

startx 'which wine' WoW.exe

But on the WoW on Ubuntu page it's like this: startx `which wine` WoW.exe

The sybols are a bit different. But I have no idea where I can get them on my own keyboard...

Aye, I was wondering about that.  It should literally be
```
startx `which wine` WoW.exe
```
where WoW.exe has the full path to WoW.exe if it's not in your PATH (which usually includes /usr/bin or your home directory).  The single-quote is actually a "backtick", which is typically found to the left of the '1/!' key, or at the upper-right on certain laptop keyboards.  Wherever it's located, it'll be the same key that you'd use Shift to produce the character '~'.  Copy-pasting the above line should work fine (ctrl-shift-v to paste in Terminal).

---

### Post by Zirts on 2010-08-21
Well, sadly I can#t copy paste it in the Ctrl + Alt + F2 mode...

Tried setting keyboard to GBr Winkeys and someothers too, I can make the sybol now when in the GUI but when in the Ctrl + Alt + F2 mode, it just makes some stupid   &#728;

Edit: oky, I made a executeable now with the text I need to say in it, I'm gonna try executing it now in that non X mode.

Edit2: Was a good idea but didn't work sadly, I get some notices about the fact that xorg.conf gets loaded and some stuff is missing and being ignored, and then it goes to the command i executed,  saying:

Waiting for X server to begin accepting connections.
No protocol specified
No protocol specified
No protocol specified
No protocol specified
No protocol specified
No protocol specified
No protocol specified
No protocol specified
No protocol specified and so on...

EDIT3: After startx gets dont with the xorg.conf it says something about xkbcomp problem but says it's not critical for X and can continue nevertheless.

---

### Post by Zirts on 2010-08-21
Just mentioning that I'm using open-source drivers and the KMS with Radeon card function. Don't know if that does change anything.
I still have the xorg.conf file in X11 folder with all of it's settings in there also.

Video card: Radeon 9550
CPU: Sempron 3000+ 1.8Ghz
RAM: 1GB

---

### Post by Zirts on 2010-08-21
I got the problem fixed, I renamed all .Xauthority folders and files to B_Xauthority(made a backup) and the eroor I talked about was gone, but now a new one arised... Now it gets to the point where it tryes to start Wow.exe,
but then it gives me an error that in the system32 folder where the Wow.exe shortcut is also must also be some Divxthingy.
Any fix for that?

---

### Post by Zirts on 2010-08-21
Bump!!!!

It tells me that some dll.Divx files are missing when trying to execute /home/kaspar/.wine/dosdevices/c:/windows/system32/Wow.exe

Where can I get my hand on such files and where do I have to put them?

And why is it required anyway as I can run WoW from GUI with no errors just horrible performance..

---

