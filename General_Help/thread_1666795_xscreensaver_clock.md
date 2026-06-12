---
title: "xscreensaver clock"
date: 2011-01-14
forum: General Help
---

### Post by ully-mick on 2011-01-14
I don't use screensavers apart from a blank screen, but if I had a clock one then that would be useful. So after a lot of searching I found a round screensaver clock, but it's for xscreensaver. so I've removed gnome-screensaver with "ubuntu software centre" and added xscreensaver the same way. I've got the file from :- 
[http://www.d8.dion.ne.jp/~pt2k/software/xscreensaver-clock/index_e.html](http://www.d8.dion.ne.jp/~pt2k/software/xscreensaver-clock/index_e.html)
but the install instructions on that page seem to be for a different distro.
could someone check this is compatible and show me the exact command to install it. I don't want to make a mess of it.

thank.

---

### Post by stinkeye on 2011-01-14
It works with the default gnome-screensaver.

---

### Post by ully-mick on 2011-01-14
ah right brilliant. so I've removed xscreensaver and installed gnome-screensaver again. erm, how do I install it please.

bit of a novice :rolleyes:

---

### Post by ully-mick on 2011-01-14
double post, sorry.

---

### Post by stinkeye on 2011-01-14
Firstly, I'm no compiling expert and don"t know what packages are included in the default Maverick install 
because I've just used a couple of scripts which
download, compile and install automatically.

Try this 
```
sudo apt-get install build-essential gcc
```

Now extract the folder **gnome-clock-screensaver-1.0.1** from the
**gnome-clock-screensaver-1.0.1.tar.gz** file you downloaded
and place in your home directory.

Open the terminal and enter(change if your folder has different name) 
```
cd ~/gnome-clock-screensaver-1.0.1
```

Then enter 
```
make
```
```
sudo make install
```

and hopefully there's no errors.

---

### Post by stinkeye on 2011-01-14
F#$@%n servers

---

### Post by stinkeye on 2011-01-14
--

---

### Post by stinkeye on 2011-01-14
--

---

### Post by stinkeye on 2011-01-14
Just found there are 2 clocks.
One for gnome-screensaver...[**_[COLOR="DarkRed"]http://www.d8.dion.ne.jp/~pt2k/software/gnome-clock-screensaver/index_e.html[/COLOR]_**]("http://www.d8.dion.ne.jp/~pt2k/software/gnome-clock-screensaver/index_e.html")

and

one for XScreenSaver...[**_[COLOR="#8b0000"]http://www.d8.dion.ne.jp/~pt2k/software/xscreensaver-clock/index_e.html[/COLOR]_**]("http://www.d8.dion.ne.jp/~pt2k/software/xscreensaver-clock/index_e.html")

---

### Post by ully-mick on 2011-01-14
Brilliant, Thank you very much

---

### Post by stinkeye on 2011-01-14
> **ully-mick said:**
> Brilliant, Thank you very much
The xscreensaver had a fix for making the clock not move which I would have
liked.
I sent an email to the author to see if there is a fix for the
gnome-screensaver version.

---

### Post by stinkeye on 2011-01-15
Ok, I just love the way open-source operates. :)
I sent an email to the author about making the clock static and got an answer.

```
gksudo gedit /usr/share/applications/screensavers/anclock.desktop
```
and change the lines 
```
Exec=anclock
TryExec=anclock
```


to read
```
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/anclock -p
TryExec=/usr/lib/gnome-screensaver/gnome-screensaver/anclock
```

You may have to change to another screensaver and back for changes to take effect.


He has also posted a new version @ [**_[COLOR="DarkRed"]http://www.d8.dion.ne.jp/~pt2k/software/gnome-clock-screensaver/index_e.html[/COLOR]_**]("http://www.d8.dion.ne.jp/~pt2k/software/gnome-clock-screensaver/index_e.html")

I installed the new version and it's basically the same (just minor documentation and path changes), and you still
need to edit the **/usr/share/applications/screensavers/anclock.desktop**
file to make the clock static.

---

### Post by ully-mick on 2011-01-15
ah, thats better. static and centred. cheers.

---

### Post by PetteriP on 2011-03-30
Woaaahh! This is EXACTLY what I've been looking for for a long time, brother!
And sorry to be adding on a solved thread.

> **stinkeye said:**
> Try this 
```
sudo apt-get install build-essential gcc
```
Done!
> **stinkeye said:**
> Now extract the folder **gnome-clock-screensaver-1.0.1** from the
**gnome-clock-screensaver-1.0.1.tar.gz** file you downloaded
and place in your home directory.

Open the terminal and enter(change if your folder has different name) 
```
cd ~/gnome-clock-screensaver-1.0.1
```

Then enter 
```
make
```...but I did get errors here

```
p@p:~/Downloads/gnome-clock-screensaver-1.0.1$ make
gcc `pkg-config gtk+-2.0 --cflags` -Wall -c gs-theme-window.c -o gs-theme-window.o
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
gs-theme-window.c:31:18: error: glib.h: No such file or directory
gs-theme-window.c:32:25: error: glib-object.h: No such file or directory
gs-theme-window.c:33:24: error: glib/gi18n.h: No such file or directory
gs-theme-window.c:35:22: error: gdk/gdkx.h: No such file or directory
gs-theme-window.c:36:21: error: gtk/gtk.h: No such file or directory
In file included from gs-theme-window.c:38:
gs-theme-window.h:43: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;typedef&#8217;
gs-theme-window.h:48: error: expected specifier-qualifier-list before &#8216;GtkWindow&#8217;
gs-theme-window.h:57: error: expected specifier-qualifier-list before &#8216;GtkWindowClass&#8217;
gs-theme-window.h:67: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;gs_theme_window_get_type&#8217;
gs-theme-window.h:68: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
gs-theme-window.c:40: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;static&#8217;
gs-theme-window.c:41: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
gs-theme-window.c:43: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
gs-theme-window.c:49: warning: return type defaults to &#8216;int&#8217;
gs-theme-window.c: In function &#8216;G_DEFINE_TYPE&#8217;:
gs-theme-window.c:51: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
gs-theme-window.c:66: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
gs-theme-window.c:94: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
gs-theme-window.c:100: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
gs-theme-window.c:114: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
gs-theme-window.c:198: error: expected declaration specifiers before &#8216;GtkWidget&#8217;
gs-theme-window.c:208: error: expected &#8216;{&#8217; at end of input
make: *** [gs-theme-window.o] Error 1
p@p:~/Downloads/gnome-clock-screensaver-1.0.1$
```

GTK+ is installed AFAIK.
Help appreciated!

---

### Post by PetteriP on 2011-03-30
> **PetteriP said:**
> ...but I did get errors here
Hold it!
I didn't have gtk2.0-dev package installed.
Installing that baby did it.

Love this thing!

---

