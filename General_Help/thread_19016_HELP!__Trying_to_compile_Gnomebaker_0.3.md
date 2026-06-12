---
title: "HELP!  Trying to compile Gnomebaker 0.3"
date: 2005-03-09
forum: General Help
---

### Post by Mark Marple on 2005-03-09
I'm trying to compile gnomebaker 0.3 and getting this error at the end of the ./configure:

checking for pkg-config... /usr/bin/pkg-config
checking for libgnomeui-2.0 gtk+-2.0 >= 2.4.0 glib-2.0 >= 2.4.0 libglade-2.0 vorbisfile... Package libgnomeui-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomeui-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomeui-2.0' found

where do I start to look at the pkg-config?  Also, I have installed (by default) the "libgnomeui-0" from apt-get.  Not sure if this can be used as the missing libgnome-2.0 or not. I don't see the -2.0 dependancy

1 quick note:  I have tried to use the .deb file that is on the wiki pages, but it is for Warty it says and I'm running Hoary 5 with all the updates.  The problem I have with the .deb is that it seems to install fine and start up fine, but when I select the mp3s to burn to cd, it just sits there.  I look in the "system monitor" area and it says the gnomebaker process is sleeping.  If I minimize the program and then maximize it, there is no text for the program, only the outside borders.  I can grab the burning window and move it around on my screen, and it like washes away the graphics behind it.

This is why I thought I would try to compile my own from source.  If anyone has a solution to the .deb file issue (the sleeping thing) I would welcome any advice.  Otherwise I guess I will try the compile route.

---

### Post by cutOff on 2005-03-14
Hi

I guess you need install development package libgnomeui-dev.

Regards!

---

### Post by Mark Marple on 2005-03-15
[QUOTE=cutOff]Hi

I guess you need install development package libgnomeui-dev.

Regards![/QUOTE]

I installed dev. package and many others being a new install of Preview (hoary) and not having make or anything like that.  Things compiled ok and when i started , it was the same as stated previously.  The whole problem was that I didn't have mpg123 installed.  Damn the simple things.  I wish this would have something saying that dependency is required.  Not sure why it didn't with the .dwb file.

Oh well, I have it compiled for my system and it's working now so I'm HAPPY...............yeah!

thanks for getting me on the right track.

---

