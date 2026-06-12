---
title: "Need Bash Script Help."
date: 2010-11-10
forum: General Help
---

### Post by #1 GameMaster on 2010-11-10
I was wondering if it was possible to open pcsx without having to type padsp pcsx in a terminal every time. I want to be able to play it by just clicking on the icon to open it like normal. Someone told me this, 

"Just write a bash script. That's what I did for all third party games I have. Since I have all the games located in ~/Games I created a directory in there called Game_Scripts and I added that directory to $PATH."

So how would I go about doing that?:confused:

---

### Post by blur xc on 2010-11-10
Is that command really all you need it to do?  I don't know what pcsx is but you could just write something like this in gedit:

```
#!/bin/bash

padsp pcsx

```save it, and give it executable permissions

```
chmod +x scriptname.sh
```then when you find the file in nautilus you can double click it to run it, or you can create a custom panel launcher, menu launcher, keyboard shortcut, whatever...there are lots of options.

BM

---

### Post by Ancanus on 2010-11-10
Right click your top menu, Add To Panel, Custom Application Launcher,

Name = pcsx
Command = padsp pcsx

OK

---

### Post by #1 GameMaster on 2010-11-10
Thanks for all the info it worked. ;)

---

