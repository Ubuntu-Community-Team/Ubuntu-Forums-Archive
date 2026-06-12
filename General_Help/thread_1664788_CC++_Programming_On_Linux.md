---
title: "C/C++ Programming On Linux"
date: 2011-01-11
forum: General Help
---

### Post by doctorzeus on 2011-01-11
Hey,

I'm a Computing Student and have been learning/using C/C++ for about 2 years now, I use Visual Studio 2010 which as many of you may know utilises the .Net framework along with various special headers specific to the windows operating system with the most obvious one being "Windows.h" which has a lot of usefull functions inside to call upon.

I have both Windows 7 and Ubuntu on my laptop and I was wanting to start using my C/C++ skills on Linux and was wondering is there a linux header that is equivelent/similar to Windows.h?

Also how easy is the transaction when progamming in C/C++? (obviouslly the C++ std library is the same across all OS's)

---

### Post by TeoBigusGeekus on 2011-01-11
Search for POSIX.

---

### Post by 3Miro on 2011-01-11
You can use std under C++, but I do recommend iostream. From from C to C++ is not hard objects are the big new thing. Overall you can do the same things in both.

---

### Post by veggen on 2011-01-11
I know very little, but I know of [this](http://ubuntuforums.org/showthread.php?t=533304) (see the last post). Apart from that option, I think you'd need to go something like OpenGL.
Also, check [this](http://www.google.com/url?sa=t&source=web&cd=3&ved=0CDIQIDAC&url=http%3A%2F%2Fwebcache.googleusercontent.com%2Fsearch%3Fq%3Dcache%3AKgMt-o_3ogMJ%3Awww.gamedev.net%2Fcommunity%2Fforums%2Ftopic.asp%253Ftopic_id%253D211621%2Bwindows.h%2Blinux%26cd%3D3%26hl%3Den%26ct%3Dclnk%26client%3Dopera&ei=pLcsTb7UAoyLswbHvfmGCA&usg=AFQjCNFCzb8a2SvtT7AjgmI2CxLNQ5NS8A&sig2=_Kt9Ro8RigTUPz-G0rb56Q) (it's from google's cache as the real thing is inaccessible at the moment).

> **3Miro said:**
> You can use std under C++, but I do recommend iostream. From from C to C++ is not hard objects are the big new thing. Overall you can do the same things in both.
I think you completely missed missed the topic here. He was talking about Windows to Linux transition here, not C to C++.

---

### Post by doctorzeus on 2011-01-11
> **3Miro said:**
> You can use std under C++, but I do recommend iostream. From from C to C++ is not hard objects are the big new thing. Overall you can do the same things in both.

Thanks for the Reply :)

Like Veggen said you must have misread my initial question ;)

Windows is very simple in Window handling and the like, e.g. "HWND WindowID = Findwindow(NULL, "WindowName");" was wondering how easy this was when it comes to Linux especially with GUI's and forms. Although I love the CLI of Linux compared to the frankly rubbish (putting it politely) CLI of dos in Windows..

I remeber a while back my friend ask why the "cls" command does not work in the Linux terminal..in a couple of minutes I made a simple program that did it when you typed in cls...Can't do that on Windows :)

---

### Post by TeoBigusGeekus on 2011-01-11
> **doctorzeus said:**
> Windows is also very simple in Window handling and the like, e.g. "HWND WindowID = Findwindow(NULL, "WindowName");" was wondering how easy this was when it comes to Linux especially with GUI's and forms. 

[Gtk programming with C.]("http://library.gnome.org/devel/gtk-tutorial/2.90/")

[Gtk programming with C++(gtkmm).]("http://library.gnome.org/devel/gtkmm-tutorial/2.21/")

I hate Qt and everything related to KDE. :P

---

### Post by doctorzeus on 2011-01-11
> **TeoBigusGeekus said:**
> [Gtk programming with C.]("http://library.gnome.org/devel/gtk-tutorial/2.90/")

[Gtk programming with C++(gtkmm).]("http://library.gnome.org/devel/gtkmm-tutorial/2.21/")

I hate Qt and everything related to KDE. :P

Thanks for the reply :)

That looks really usefull, I'll check it out thanks!

Yeah I know what you mean with KDE, tried it and didn't like it especially when moving from VS2010 which despite what people say about Microsoft it is the best IDE around...The small amounts I've done I've used Codelite..

Cannot wait until the .Net frameworks fully work on Wine :)

---

### Post by doctorzeus on 2011-01-11
> **veggen said:**
> I know very little, but I know of [this](http://ubuntuforums.org/showthread.php?t=533304) (see the last post). Apart from that option, I think you'd need to go something like OpenGL.
Also, check [this](http://www.google.com/url?sa=t&source=web&cd=3&ved=0CDIQIDAC&url=http%3A%2F%2Fwebcache.googleusercontent.com%2Fsearch%3Fq%3Dcache%3AKgMt-o_3ogMJ%3Awww.gamedev.net%2Fcommunity%2Fforums%2Ftopic.asp%253Ftopic_id%253D211621%2Bwindows.h%2Blinux%26cd%3D3%26hl%3Den%26ct%3Dclnk%26client%3Dopera&ei=pLcsTb7UAoyLswbHvfmGCA&usg=AFQjCNFCzb8a2SvtT7AjgmI2CxLNQ5NS8A&sig2=_Kt9Ro8RigTUPz-G0rb56Q) (it's from google's cache as the real thing is inaccessible at the moment).


I think you completely missed missed the topic here. He was talking about Windows to Linux transition here, not C to C++.

Thanks thats pretty much what I guessed involving the Windows.h header file :(

Sure I can improvise though with other header files :popcorn:

---

