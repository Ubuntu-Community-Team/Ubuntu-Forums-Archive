---
title: "Installing IronAhk on Ubuntu"
date: 2011-08-25
forum: General Help
---

### Post by redaler1 on 2011-08-25
Hello ubuntu community,

I've been trying ubuntu for the past couple of months and so far the only thing that I miss from the windows realm is autohotkey (great hotkey and scripting app).

I learned that there is a .net port called IronaAhk which should work on linux (mono). I have managed to install it following the guide on 
[http://brendonrobinson.wordpress.com/2011/04/10/building-ironahk-from-source-on-ubuntu-10-10-maverick-meerkat/](http://brendonrobinson.wordpress.com/2011/04/10/building-ironahk-from-source-on-ubuntu-10-10-maverick-meerkat/)

Using ubuntu 11.04 I noticed the strange thing that the GUI part works (msgbox and similar), however hotstrings and hotkeys which are the core part of autohotkey does not work.
Expanding abbreviation from the examples
::btw::by the way
produces the following output
3513
The send/sendInput commands have the same effect. Any ideas on what might be the problem?

Can anyone confirm that they were able to install and run IronAhk without similar issues on ubuntu?

---

