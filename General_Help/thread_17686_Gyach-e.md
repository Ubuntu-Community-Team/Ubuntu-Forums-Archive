---
title: "Gyach-e"
date: 2005-03-02
forum: General Help
---

### Post by Phosphoros on 2005-03-02
I just installed [gyach-E Enhanced](http://phpaint.sourceforge.net/pyvoicechat/index.php) and it runs fine for a couple minutes, then POOF!
I've never really seen this discussed here so I'm not sure anyone could help but I thought I'd ask anyhow.

Here's the Error code

```
tristan@ubuntu:/ $ gyach
Use of deprecated SAXv1 function endElement

(gyach:1642): Gtk-CRITICAL **: file gtktreemodel.c: line 998 (gtk_tree_model_get_iter_first): assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(gyach:1642): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

(gyach:1642): Gdk-CRITICAL **: file gdkdraw.c: line 771 (gdk_draw_pixbuf): assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gyach:1642): GLib-GObject-CRITICAL **: file gobject.c: line 1579 (g_object_unref): assertion `G_IS_OBJECT (object)' failed

(gyach:1642): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

(gyach:1642): Gdk-CRITICAL **: file gdkdraw.c: line 771 (gdk_draw_pixbuf): assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gyach:1642): GLib-GObject-CRITICAL **: file gobject.c: line 1579 (g_object_unref): assertion `G_IS_OBJECT (object)' failed
Segmentation fault
```

and after I restart it it gave me this........

```
tristan@ubuntu:/ $ gyach
Use of deprecated SAXv1 function endElement

(gyach:3005): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

(gyach:3005): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed
Segmentation fault
```

It's all greek to me.  lol  I was just desperately trying to find a program to have yahoo video chat with my family and this is the only thing I've found.  I tried net/gnomemeeting but does anyone actually use that anymore? No one I know does.

If anyone has any other suggestions for decent video conference software that is either available for Linux **and** windows or can connect to Yahoo for video I'm all ears.

Sadly, Gyach-e has absolutely NO support what-so-ever.  No forums, no nothing.  :(

Thanks

---

### Post by 0okami on 2005-12-03
[QUOTE=Phosphoros]I just installed [gyach-E Enhanced](http://phpaint.sourceforge.net/pyvoicechat/index.php) and it runs fine for a couple minutes, then POOF!
I've never really seen this discussed here so I'm not sure anyone could help but I thought I'd ask anyhow.

Here's the Error code

```
tristan@ubuntu:/ $ gyach
Use of deprecated SAXv1 function endElement

(gyach:1642): Gtk-CRITICAL **: file gtktreemodel.c: line 998 (gtk_tree_model_get_iter_first): assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(gyach:1642): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

(gyach:1642): Gdk-CRITICAL **: file gdkdraw.c: line 771 (gdk_draw_pixbuf): assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gyach:1642): GLib-GObject-CRITICAL **: file gobject.c: line 1579 (g_object_unref): assertion `G_IS_OBJECT (object)' failed

(gyach:1642): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

(gyach:1642): Gdk-CRITICAL **: file gdkdraw.c: line 771 (gdk_draw_pixbuf): assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gyach:1642): GLib-GObject-CRITICAL **: file gobject.c: line 1579 (g_object_unref): assertion `G_IS_OBJECT (object)' failed
Segmentation fault
```

and after I restart it it gave me this........

```
tristan@ubuntu:/ $ gyach
Use of deprecated SAXv1 function endElement

(gyach:3005): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

(gyach:3005): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed
Segmentation fault
```

It's all greek to me.  lol  I was just desperately trying to find a program to have yahoo video chat with my family and this is the only thing I've found.  I tried net/gnomemeeting but does anyone actually use that anymore? No one I know does.

If anyone has any other suggestions for decent video conference software that is either available for Linux **and** windows or can connect to Yahoo for video I'm all ears.

Sadly, Gyach-e has absolutely NO support what-so-ever.  No forums, no nothing.  :(

Thanks[/QUOTE]

Did you ever find a solution to this? My mother wont accept linux on her machine if it cant do yahoo (voice) chat. Go figure. GRR. She's so difficult sometimes but I guess that comes with age. 

I get the same errors as you here. I followed the guide, but I cant seem to get voice working at all. Do you know of any other yahoo chat applications win which voice is functional?

---

### Post by Phosphoros on 2005-12-03
Nope, I never found a solution that would work.  Never got Voice or the Cam to work for any length of time.
Just error after error and the person who wrote the program is sadly of **NO** help what-so-ever.
Sorry, wish I could help more.  I was fairly disappointed with the whole thing myself and finally gave up.

---

### Post by rem on 2005-12-04
Hi, same here too ... exactly the same error and no voice at all. Please let us know if you manage to find a decent replacement of yahoo voice/cam stuff, I know I'll do so. Thanks!

---

### Post by Phosphoros on 2005-12-04
[QUOTE=rem]Hi, same here too ... exactly the same error and no voice at all. Please let us know if you manage to find a decent replacement of yahoo voice/cam stuff, I know I'll do so. Thanks![/QUOTE]

Well that's the problem.  There really is no alternative.  If you just want generic chat Yahoo! has released a linux version but it's ugly as sin and it's pointless for anything other than simple chat.
I pretty much gave up as I already mentioned.
Infact, I've given up on having any IM that can do Voice or Cam.
I'm sure if anyone has a suggestion for an IM Cleint that will handle Voice or Cam for Linux they'll offer it.  Sadly though, from what I can tell Linux has poor support for Cams in general.  Atleast for me, since I'm still pretty much a newb to linux.

Good luck in your search.  :D

EDIT: Seems the maker of Gyach-e has a forum now.  It's located [here]("http://phrozensmoke.com/phpbb/viewforum.php?f=5").
A couple people have gotten it to work on Hoary(?).  still tons of errors though.  Hope that helps.

---

### Post by endangst on 2006-01-09
```
endangst@ubuntu:~/gyach$ gyach
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
/usr/local/share/gyach/pyvoice/pytsp.py:2: RuntimeWarning: Python C API version mismatch for module pytspc: This Python has API version 1012, module pytspc has version 1011.
  import pytspc
/usr/local/share/gyach/pyvoice/pyvoiceui.py:161: DeprecationWarning: use gtk.UIManager
  itemf=ItemFactory(MenuBar, "<main>", ag)
/usr/local/share/gyach/pyvoice/pyvoiceui.py:264: DeprecationWarning: use gtk.TreeView
  self.nmlist=CList(3,[' I ',' '+_('Name')+' ',' '+_('Alias')+' '])
/usr/local/share/gyach/pyvoice/pyvoiceui.py:298: Warning: unsupported arithmetic operation for flags type
  prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
Traceback (most recent call last):
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1027, in ?
    runApp()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1015, in runApp
    pyvoicegui()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 298, in __init__
    prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
TypeError: flag values must be strings, ints, longs, or tuples
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
/usr/local/share/gyach/pyvoice/pytsp.py:2: RuntimeWarning: Python C API version mismatch for module pytspc: This Python has API version 1012, module pytspc has version 1011.
  import pytspc
/usr/local/share/gyach/pyvoice/pyvoiceui.py:161: DeprecationWarning: use gtk.UIManager
  itemf=ItemFactory(MenuBar, "<main>", ag)
/usr/local/share/gyach/pyvoice/pyvoiceui.py:264: DeprecationWarning: use gtk.TreeView
  self.nmlist=CList(3,[' I ',' '+_('Name')+' ',' '+_('Alias')+' '])
/usr/local/share/gyach/pyvoice/pyvoiceui.py:298: Warning: unsupported arithmetic operation for flags type
  prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
Traceback (most recent call last):
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1027, in ?
    runApp()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1015, in runApp
    pyvoicegui()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 298, in __init__
    prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
TypeError: flag values must be strings, ints, longs, or tuples
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
/usr/local/share/gyach/pyvoice/pytsp.py:2: RuntimeWarning: Python C API version mismatch for module pytspc: This Python has API version 1012, module pytspc has version 1011.
  import pytspc
/usr/local/share/gyach/pyvoice/pyvoiceui.py:161: DeprecationWarning: use gtk.UIManager
  itemf=ItemFactory(MenuBar, "<main>", ag)
/usr/local/share/gyach/pyvoice/pyvoiceui.py:264: DeprecationWarning: use gtk.TreeView
  self.nmlist=CList(3,[' I ',' '+_('Name')+' ',' '+_('Alias')+' '])
/usr/local/share/gyach/pyvoice/pyvoiceui.py:298: Warning: unsupported arithmetic operation for flags type
  prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
Traceback (most recent call last):
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1027, in ?
    runApp()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1015, in runApp
    pyvoicegui()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 298, in __init__
    prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
TypeError: flag values must be strings, ints, longs, or tuples

(gyach:4757): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(gyach:4757): Gdk-CRITICAL **: gdk_draw_pixbuf: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gyach:4757): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
endangst@ubuntu:~/gyach$

```

Same crap here. hehheh..  no voice, even when I clicked on the voice buttons. ugh.

Their forums also have no support... just the blind leading the blind there.  I think the developer of this software should have called it "Gyach Alpha" or "beta" because it is so full of bugs.
 
Mine also terminates after 5 minutes... just POOF and it's gone like that.

---

### Post by sabitha on 2006-01-09
try edit the line expand+fill with EXPAND&FILL on /usr/local/share/gyach/pyvoice/pyvoiceui.py 
i see that on the gyach forums website

---

### Post by endangst on 2006-01-09
Thanks for the help.  It is a bit more stable now, but it never connects to voice.
The PY Voice chat box opens and says it is "Connecting", but it never happens.

There is a long list of voice servers and I tried some of them, but still won't get voice.

:???:

---

### Post by sabitha on 2006-01-09
PM aja deh yahoo ID: pitus212
sekarang ...!!!!

---

### Post by madzieph on 2008-02-22
Dunno where to ask this so I thought of posting it here...

Am using Gyachi 1.1.0 on Debian Etch (with Gyachi dependencies updated with Lenny and Sid) on an:

AMD K2-266 MHz
128 MB RAM
Fluxbox WM

It doesn't happen often but I get **Segmentation Fault Error** when I press the clear chat area button (broom icon). Usually it happens after say an hour of being online without the regular screen clearing... when chatting I do it about every 5 mins. 

Anything on this? Thanks.

---

### Post by fragimar on 2008-07-21
> **Phosphoros said:**
> Well that's the problem.  There really is no alternative.  If you just want generic chat Yahoo! has released a linux version but it's ugly as sin and it's pointless for anything other than simple chat.
I pretty much gave up as I already mentioned.
Infact, I've given up on having any IM that can do Voice or Cam.
I'm sure if anyone has a suggestion for an IM Cleint that will handle Voice or Cam for Linux they'll offer it.  Sadly though, from what I can tell Linux has poor support for Cams in general.  Atleast for me, since I'm still pretty much a newb to linux.

Good luck in your search.  :D

EDIT: Seems the maker of Gyach-e has a forum now.  It's located [here]("http://phrozensmoke.com/phpbb/viewforum.php?f=5").
A couple people have gotten it to work on Hoary(?).  still tons of errors though.  Hope that helps.

Skype

[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

---

