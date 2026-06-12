---
title: "Trouble Installing Aleph One"
date: 2011-06-11
forum: General Help
---

### Post by kexus on 2011-06-11
I'm trying to install the Aleph One game engine on Ubuntu 11.04.  It came as a .tar.gz file so I tried the standard procedure, but when I tried to use the *make *command, it gave an error near the end.

Here is the full output.

make  all-recursive
make[1]: Entering directory `/home/alex/Downloads/AlephOne-20051119'
Making all in Source_Files
make[2]: Entering directory `/home/alex/Downloads/AlephOne-20051119/Source_Files'
Making all in CSeries
make[3]: Entering directory `/home/alex/Downloads/AlephOne-20051119/Source_Files/CSeries'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../Source_Files/Files -I../../Source_Files/GameWorld -I../../Source_Files/Input -I../../Source_Files/Misc -I../../Source_Files/ModelView -I../../Source_Files/Network -I../../Source_Files/Pfhortran -I../../Source_Files/RenderMain -I../../Source_Files/RenderOther -I../../Source_Files/Sound -I../../Source_Files/XML -I../../Source_Files/Network/Metaserver -I../../Source_Files/TCPMess  -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DSDL -I/usr/X11R6/include -L/usr/X11R6/lib  -g -O2 -MT csalerts_sdl.o -MD -MP -MF ".deps/csalerts_sdl.Tpo" -c -o csalerts_sdl.o csalerts_sdl.cpp; \
    then mv -f ".deps/csalerts_sdl.Tpo" ".deps/csalerts_sdl.Po"; else rm -f ".deps/csalerts_sdl.Tpo"; exit 1; fi
In file included from csalerts_sdl.cpp:37:0:
../../Source_Files/Misc/sdl_widgets.h:947:2: error: extra qualification ‘SelectorWidget::’ on member ‘SelectorWidget’
../../Source_Files/Misc/sdl_widgets.h:958:2: error: extra qualification ‘PopupSelectorWidget::’ on member ‘PopupSelectorWidget’
../../Source_Files/Misc/sdl_widgets.h:977:2: error: extra qualification ‘SelectSelectorWidget::’ on member ‘SelectSelectorWidget’
../../Source_Files/Misc/sdl_widgets.h:999:2: error: extra qualification ‘ColourSelectorWidget::’ on member ‘ColourSelectorWidget’
../../Source_Files/Misc/sdl_widgets.h:1031:2: error: extra qualification ‘StaticTextWidget::’ on member ‘StaticTextWidget’
make[3]: *** [csalerts_sdl.o] Error 1
make[3]: Leaving directory `/home/alex/Downloads/AlephOne-20051119/Source_Files/CSeries'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/alex/Downloads/AlephOne-20051119/Source_Files'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alex/Downloads/AlephOne-20051119'
make: *** [all] Error 2

I've done this kind of thing before, so I'm pretty sure I'm not doing anything wrong.  Does anyone know what to do, or what the error messages mean?

---

### Post by mistyautom on 2011-06-11
There are a couple of different versions of Alephone deb packages available for download at [http://www.dotdeb.com/rpg.php](http://www.dotdeb.com/rpg.php)

---

### Post by iamanidiot123 on 2011-07-24
You want to get the latest version of AlephOne first:
marathon.sourceforge.net






Is this a dead thread?

---

