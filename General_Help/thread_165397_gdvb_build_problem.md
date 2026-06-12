---
title: "gdvb build problem"
date: 2006-04-24
forum: General Help
---

### Post by mtron on 2006-04-24
Hi hope sb can help me out here. i'm trying to build gdvb 0.3 (java gtk2) [http://www.nopcode.org/blog/gdvb.html](http://www.nopcode.org/blog/gdvb.html)

libgtk-java is installed, configure runs ok:

```
mtron@workstation:~/work/gdvb-0.3$ ./configure
checking build system type... i686-unknown-linux-gnu
checking host system type... i686-unknown-linux-gnu
checking target system type... i686-unknown-linux-gnu
checking for working directories... current
using prefix /usr/local
checking for javac... javac
checking for mplayer... /usr/bin/mplayer
filtering META-INF/MANIFEST.MF
creating ./Makefile
creating src//Makefile
cleaning temporally files... done
mtron@workstation:~/work/gdvb-0.3$
```

but when running "make" i get:
```
make
cd src && make
make[1]: Entering directory `/home/mtron/work/gdvb-0.3/src'
javac *.java
About.java:21: package org.gnu.gtk does not exist
import org.gnu.gtk.*;
^
About.java:22: package org.gnu.gdk does not exist
import org.gnu.gdk.Pixbuf;
                   ^
About.java:23: package org.gnu.gtk.event does not exist
import org.gnu.gtk.event.*;
^
About.java:25: cannot find symbol
symbol: class DialogListener
public class About implements DialogListener
                              ^
About.java:27: cannot find symbol
symbol  : class AboutDialog
location: class About
AboutDialog ad = null ;
^
About.java:29: cannot find symbol
symbol  : class DialogEvent
location: class About
public boolean dialogEvent(DialogEvent ev)
                           ^
About.java:39: cannot find symbol
symbol  : class ButtonEvent
location: class About
public void buttonEvent(ButtonEvent event)
                        ^
AddEvent.java:21: package org.gnu.gtk does not exist
import org.gnu.gtk.*;
^
AddEvent.java:22: package org.gnu.gtk.event does not exist
import org.gnu.gtk.event.*;
^
AddEvent.java:25: cannot find symbol
symbol: class ButtonListener
public class AddEvent implements ButtonListener
                                 ^
AddEvent.java:27: cannot find symbol
symbol  : class TreeSelection
location: class AddEvent
TreeSelection ts;
^
AddEvent.java:28: cannot find symbol
symbol  : class ListStore
location: class AddEvent
ListStore ls;
^
AddEvent.java:29: cannot find symbol
symbol  : class DataColumnString
location: class AddEvent
DataColumnString dcs;
^
Favorites.java:22: package org.gnu.gtk does not exist
import org.gnu.gtk.*;
^
Favorites.java:23: package org.gnu.gtk.event does not exist
import org.gnu.gtk.event.*;
^
Favorites.java:25: cannot find symbol
symbol: class ButtonListener
class Favorites implements ButtonListener,DialogListener
                           ^
Favorites.java:25: cannot find symbol
symbol: class DialogListener
class Favorites implements ButtonListener,DialogListener
                                          ^
AddEvent.java:31: cannot find symbol
symbol  : class ListStore
location: class AddEvent
ListStore _ls;
^
AddEvent.java:32: cannot find symbol
symbol  : class DataColumnString
location: class AddEvent
DataColumnString _dcs;
^
AddEvent.java:33: cannot find symbol
symbol  : class DataColumnBoolean
location: class AddEvent
DataColumnBoolean _dcb;
^
AddEvent.java:35: cannot find symbol
symbol  : class TreeSelection
location: class AddEvent
public AddEvent(Favorites fv, TreeSelection ts,ListStore ls, DataColumn dcs,ListStore _ls,DataColumn[] _dcs)
                              ^
AddEvent.java:35: cannot find symbol
symbol  : class ListStore
location: class AddEvent
public AddEvent(Favorites fv, TreeSelection ts,ListStore ls, DataColumn dcs,ListStore _ls,DataColumn[] _dcs)
                                               ^
AddEvent.java:35: cannot find symbol
symbol  : class DataColumn
location: class AddEvent
public AddEvent(Favorites fv, TreeSelection ts,ListStore ls, DataColumn dcs,ListStore _ls,DataColumn[] _dcs)
                                                             ^
AddEvent.java:35: cannot find symbol
symbol  : class ListStore
location: class AddEvent
public AddEvent(Favorites fv, TreeSelection ts,ListStore ls, DataColumn dcs,ListStore _ls,DataColumn[] _dcs)
                                                                            ^
AddEvent.java:35: cannot find symbol
symbol  : class DataColumn
location: class AddEvent
public AddEvent(Favorites fv, TreeSelection ts,ListStore ls, DataColumn dcs,ListStore _ls,DataColumn[] _dcs)
           ^
AddEvent.java:58: cannot find symbol
symbol  : class ButtonEvent
location: class AddEvent
public void buttonEvent(ButtonEvent ev)
                        ^
Favorites.java:27: cannot find symbol
symbol  : class ListStore
location: class Favorites
private ListStore ls;
        ^
Favorites.java:28: cannot find symbol
symbol  : class DataColumnString
location: class Favorites
private DataColumnString dc;
        ^
Favorites.java:29: cannot find symbol
symbol  : class DataColumnBoolean
location: class Favorites
private DataColumnBoolean dcb;
        ^
Favorites.java:30: cannot find symbol
symbol  : class StatusBar
location: class Favorites
private StatusBar sb;
        ^
Favorites.java:33: cannot find symbol
symbol  : class MessageDialog
location: class Favorites
private MessageDialog d = null;
        ^
Favorites.java:35: cannot find symbol
symbol  : class StatusBar
location: class Favorites
public Favorites(String satName, StatusBar sb,ListStore ls,DataColumn[] dc)
                                 ^
Favorites.java:35: cannot find symbol
symbol  : class ListStore
location: class Favorites
public Favorites(String satName, StatusBar sb,ListStore ls,DataColumn[] dc)
                                              ^
Favorites.java:35: cannot find symbol
symbol  : class DataColumn
location: class Favorites
public Favorites(String satName, StatusBar sb,ListStore ls,DataColumn[] dc)
                                                           ^
Favorites.java:50: cannot find symbol
symbol  : class DialogEvent
location: class Favorites
public boolean dialogEvent(DialogEvent event)
                           ^
Favorites.java:126: cannot find symbol
symbol  : class ButtonEvent
location: class Favorites
public void buttonEvent(ButtonEvent ev)
                        ^
AddRemote.java:22: package org.gnu.gtk does not exist
import org.gnu.gtk.*;
^
AddRemote.java:23: package org.gnu.gtk.event does not exist
import org.gnu.gtk.event.*;
^
AddRemote.java:25: cannot find symbol
symbol: class Dialog
public class AddRemote extends Dialog
                               ^
AddRemote.java:31: cannot find symbol
symbol  : class Entry
location: class AddRemote
        Entry e;
        ^
AddRemote.java:32: cannot find symbol
symbol  : class Entry
location: class AddRemote
        Entry e2;
        ^
DebugPoller.java:21: package org.gnu.gtk does not exist
import org.gnu.gtk.TextBuffer;
                   ^
DebugPoller.java:25: cannot find symbol
symbol  : class TextBuffer
location: class DebugPoller
TextBuffer mp;
^
DebugPoller.java:26: cannot find symbol
symbol  : class TextBuffer
location: class DebugPoller
TextBuffer sz;
^
DebugPoller.java:30: cannot find symbol
symbol  : class TextBuffer
location: class DebugPoller
public DebugPoller(TextBuffer mp, TextBuffer sz)
                   ^
DebugPoller.java:30: cannot find symbol
symbol  : class TextBuffer
location: class DebugPoller
public DebugPoller(TextBuffer mp, TextBuffer sz)
                                  ^
DebugWindow.java:21: package org.gnu.gtk does not exist
import org.gnu.gtk.*;
^
DebugWindow.java:22: package org.gnu.gtk.event does not exist
import org.gnu.gtk.event.ButtonListener;
                         ^
DebugWindow.java:23: package org.gnu.gtk.event does not exist
import org.gnu.gtk.event.ButtonEvent;
                         ^
DebugWindow.java:25: cannot find symbol
symbol: class ButtonListener
public class DebugWindow implements ButtonListener
                                    ^
DebugWindow.java:27: cannot find symbol
symbol  : class Window
location: class DebugWindow
private Window w;
        ^
DebugWindow.java:28: cannot find symbol
symbol  : class TextView
location: class DebugWindow
private TextView mp;
        ^
DebugWindow.java:29: cannot find symbol
symbol  : class TextView
location: class DebugWindow
private TextView sz;
        ^
DebugWindow.java:30: cannot find symbol
symbol  : class TextBuffer
location: class DebugWindow
private TextBuffer tmp;
        ^
DebugWindow.java:31: cannot find symbol
symbol  : class TextBuffer
location: class DebugWindow
private TextBuffer tsz;
        ^
DebugWindow.java:32: cannot find symbol
symbol  : class Entry
location: class DebugWindow
private Entry mpe;
        ^
DebugWindow.java:105: cannot find symbol
symbol  : class ButtonEvent
location: class DebugWindow
public void buttonEvent(ButtonEvent ev)
                        ^
DelEvent.java:21: package org.gnu.gtk does not exist
import org.gnu.gtk.*;
^
DelEvent.java:22: package org.gnu.gtk.event does not exist
import org.gnu.gtk.event.*;
^
DelEvent.java:24: cannot find symbol
symbol: class ButtonListener
public class DelEvent implements ButtonListener
                                 ^
DelEvent.java:26: cannot find symbol
symbol  : class TreeSelection
location: class DelEvent
TreeSelection ts;
^
DelEvent.java:27: cannot find symbol
symbol  : class ListStore
location: class DelEvent
ListStore ls;
^
DelEvent.java:29: cannot find symbol
symbol  : class DataColumnString
location: class DelEvent
DataColumnString dcs;
^
DelEvent.java:31: cannot find symbol
symbol  : class TreeSelection
location: class DelEvent
public DelEvent(Favorites fv, TreeSelection ts,ListStore ls, DataColumn dcs)
                              ^
DelEvent.java:31: cannot find symbol
symbol  : class ListStore
location: class DelEvent
public DelEvent(Favorites fv, TreeSelection ts,ListStore ls, DataColumn dcs)
                                               ^
DelEvent.java:31: cannot find symbol
symbol  : class DataColumn
location: class DelEvent
public DelEvent(Favorites fv, TreeSelection ts,ListStore ls, DataColumn dcs)
                                                             ^
DelEvent.java:39: cannot find symbol
symbol  : class ButtonEvent
location: class DelEvent
public void buttonEvent(ButtonEvent ev)
                        ^
Gdvb.java:30: package org.gnu.gdk does not exist
import org.gnu.gdk.Pixbuf;
                   ^
Gdvb.java:31: package org.gnu.gtk does not exist
import org.gnu.gtk.*;
^
Gdvb.java:32: package org.gnu.gtk.event does not exist
import org.gnu.gtk.event.*;
^
Gdvb.java:34: cannot find symbol
symbol: class ActionEntryListener
class Gdvb implements ActionEntryListener,DialogListener,ButtonListener,TreeViewListener,TreeViewColumnListener
                      ^
Gdvb.java:34: cannot find symbol
symbol: class DialogListener
class Gdvb implements ActionEntryListener,DialogListener,ButtonListener,TreeViewListener,TreeViewColumnListener
                                          ^
Gdvb.java:34: cannot find symbol
symbol: class ButtonListener
class Gdvb implements ActionEntryListener,DialogListener,ButtonListener,TreeViewListener,TreeViewColumnListener
                                                         ^
Gdvb.java:34: cannot find symbol
symbol: class TreeViewListener
class Gdvb implements ActionEntryListener,DialogListener,ButtonListener,TreeViewListener,TreeViewColumnListener
                                                                        ^
Gdvb.java:34: cannot find symbol
symbol: class TreeViewColumnListener
class Gdvb implements ActionEntryListener,DialogListener,ButtonListener,TreeViewListener,TreeViewColumnListener
          ^
Gdvb.java:36: cannot find symbol
symbol  : class Window
location: class Gdvb
public static Window w = null;
              ^
ViewChannel.java:21: package org.gnu.gtk does not exist
import org.gnu.gtk.*;
^
ViewChannel.java:22: package org.gnu.gtk.event does not exist
import org.gnu.gtk.event.*;
^
ViewChannel.java:24: cannot find symbol
symbol: class ButtonListener
public class ViewChannel implements ButtonListener,TreeViewListener
                                    ^
ViewChannel.java:24: cannot find symbol
symbol: class TreeViewListener
public class ViewChannel implements ButtonListener,TreeViewListener
                                                   ^
QuitProgram.java:23: package org.gnu.gtk does not exist
import org.gnu.gtk.*;
^
QuitProgram.java:24: package org.gnu.gtk.event does not exist
import org.gnu.gtk.event.*;
^
QuitProgram.java:26: cannot find symbol
symbol: class ButtonListener
public class QuitProgram implements ButtonListener,LifeCycleListener
                                    ^
QuitProgram.java:26: cannot find symbol
symbol: class LifeCycleListener
public class QuitProgram implements ButtonListener,LifeCycleListener
                                                   ^
Gdvb.java:39: cannot find symbol
symbol  : class StatusBar
location: class Gdvb
private StatusBar sb=null;
        ^
Preferences.java:21: package org.gnu.gtk does not exist
import org.gnu.gtk.*;
^
Preferences.java:22: package org.gnu.gtk.event does not exist
import org.gnu.gtk.event.*;
^
Preferences.java:23: package org.gnu.gdk does not exist
import org.gnu.gdk.Pixbuf;
                   ^
Preferences.java:27: cannot find symbol
symbol: class TreeSelectionListener
public class Preferences implements TreeSelectionListener, LifeCycleListener, ButtonListener
                                    ^
Preferences.java:27: cannot find symbol
symbol: class LifeCycleListener
public class Preferences implements TreeSelectionListener, LifeCycleListener, ButtonListener
                                                           ^
Preferences.java:27: cannot find symbol
symbol: class ButtonListener
public class Preferences implements TreeSelectionListener, LifeCycleListener, ButtonListener
                                                                              ^
Gdvb.java:45: cannot find symbol
symbol  : class MessageDialog
location: class Gdvb
private static MessageDialog md = null;
               ^
Mplayer.java:22: package org.gnu.gtk does not exist
import org.gnu.gtk.*;
^
Mplayer.java:23: package org.gnu.gtk does not exist
import org.gnu.gtk.StatusBar;
                   ^
Gdvb.java:49: cannot find symbol
symbol  : class FileChooserWidget
location: class Gdvb
private FileChooserWidget fcw = null;
        ^
Gdvb.java:50: cannot find symbol
symbol  : class Button
location: class Gdvb
private static Button remote_play = null;
               ^
Gdvb.java:51: cannot find symbol
symbol  : class TreeView
location: class Gdvb
private static TreeView tv = null;
               ^
Gdvb.java:52: cannot find symbol
symbol  : class ListStore
location: class Gdvb
private static ListStore ls = null;
               ^
Gdvb.java:53: cannot find symbol
symbol  : class DataColumn
location: class Gdvb
private static DataColumn[] dc = null;
               ^
Gdvb.java:95: package org.gnu.gtk.event does not exist
public boolean dialogEvent(org.gnu.gtk.event.DialogEvent e)
                                            ^
Note: Gdvb.java uses unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
100 errors
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/mtron/work/gdvb-0.3/src'
make: *** [all] Error 2
mtron@workstation:~/work/gdvb-0.3$
```

Anyone an idea what is the cause for this? 

Cheers & thanks in advance
mtron

---

### Post by mtron on 2006-06-21
never mind, dapper package in the repositories now.

---

### Post by MattiViljanen on 2006-08-30
I have the same problem still, I'm trying to compile version 0.5...

---

