---
title: "Playing music from command line in rhythmbox"
date: 2011-02-11
forum: General Help
---

### Post by Spyderkid on 2011-02-11
if im in the right directory and I want to play a piece of music called example.ogg in rhythmbox what command could I give?

---

### Post by I&#9829;HTML5 on 2011-02-11
Enter into terminal:
```
rhythmbox /path/to/example.ogg
```

---

### Post by Spyderkid on 2011-02-12
I did what you said and this happened...

```

bob@Ubuntu:~/Music$ rhythmbox /path/to/Josh\Woodward\-\Swansong.ogg

(rhythmbox:2877): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
** (rhythmbox:2877): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
** (rhythmbox:2877): DEBUG: Loading the real store page

** (rhythmbox:2877): WARNING **: Got less number of items in credentials hash table than expected!
** (rhythmbox:2877): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token

(rhythmbox:2877): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:2877): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:2877): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed
** (rhythmbox:2877): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=34&partner=983


```

---

### Post by Spyderkid on 2011-02-12
any ideas what went wrong?

---

### Post by stinkeye on 2011-02-12
Don't literally use  **/path/to**
That's a description of what to use.

> if im in the right directory and I want to play a piece of music called example.ogg in rhythmbox what command could I give?
If you mean while in the terminal,you're in the directory where the song is located, just use.
```
rhythmbox "Swansong.ogg"
```


....and if you are in the right directory the /path/to will be shown.

---

### Post by Spyderkid on 2011-02-13
this is what i've got now...
```

bob@Ubuntu:~/Music/queen/greatest hits$ rhythmbox "01 - Track 01"
Failed to load file:///home/bob/Music/queen/greatest%20hits/01%20-%20Track%2001: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.bob@Ubuntu:~/Music/queen/greatest hits$ 


```

---

### Post by Animal X on 2011-02-13
> **Spyderkid said:**
> this is what i've got now...
```

bob@Ubuntu:~/Music/queen/greatest hits$ rhythmbox "01 - Track 01"
Failed to load file:///home/bob/Music/queen/greatest%20hits/01%20-%20Track%2001: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.bob@Ubuntu:~/Music/queen/greatest hits$ 


```

you have spaces in your filename, edit the spaces out, or use backslash to comment out the spaces:
> rhythmbox "01\ -\ Track\ 01"

or use tab complete to find the name

---

### Post by Spyderkid on 2011-02-13
I use " " istead its easier and using \ doesn't seem to work for me :S

---

### Post by Animal X on 2011-02-16
actually i c wut u mean, i tried playing a file and i got a page and a half of messages and errors, but my file played. I doubt you can use this but this was my out put:
> 

(rhythmbox:14559): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
** (rhythmbox:14559): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
** (rhythmbox:14559): DEBUG: Loading the real store page

** (rhythmbox:14559): WARNING **: Got less number of items in credentials hash table than expected!
** (rhythmbox:14559): DEBUG: navigation requested to [https://one.ubuntu.com/music/store-no-token](https://one.ubuntu.com/music/store-no-token)

(rhythmbox:14559): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:14559): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:14559): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:14559): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:14559): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:14559): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:14559): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:14559): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:14559): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:14559): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:14559): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:14559): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:14559): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:14559): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:14559): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:14559): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(rhythmbox:14559): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:14559): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(rhythmbox:14559): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:14559): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:14559): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(rhythmbox:14559): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:14559): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(rhythmbox:14559): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:14559): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed
** (rhythmbox:14559): DEBUG: navigation requested to [http://stores.7digital.com/default.aspx?shop=480&partner=983](http://stores.7digital.com/default.aspx?shop=480&partner=983)

(rhythmbox:14559): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


---

### Post by tgalati4 on 2011-02-16
sudo apt-get install moc
mocp

---

### Post by Spyderkid on 2011-02-18
what does that do i don't want to install it without knowing what it is

---

### Post by I&#9829;HTML5 on 2011-02-18
[http://moc.daper.net/]("http://moc.daper.net/")

---

### Post by Swagman on 2011-02-18
cd to dir first

```
paul@pauls-desktop:~$ cd /home/paul/Music/10cc
paul@pauls-desktop:~/Music/10cc$ rhythmbox "10cc - Donna.mp3"
```

---

### Post by I&#9829;HTML5 on 2011-02-18
> **Swagman said:**
> cd to dir first

```
paul@pauls-desktop:~$ cd /home/paul/Music/10cc
paul@pauls-desktop:~/Music/10cc$ rhythmbox "10cc - Donna.mp3"
```

From the sound of the original post, he is already in the right directory...

---

### Post by williamts99 on 2011-02-18
If you want to do this all from the terminal, I would install music123 with:
```
sudo apt-get install music123
```

If you want the manual:
man music123

and then just use:
```
music123 filename.mp3
```

---

### Post by Spyderkid on 2011-02-19
did what you suggested installed it but nothing played heres what i got in terminal (no errors)

```

@Ubuntu:~ cd Music
@Ubuntu:~ Music$ ls -l
total 64
drwxr-xr-x 3  4096 2011-02-12 16:45 Andrew Strong
drwxr-xr-x 3  4096 2011-02-12 16:45 Angeline Ball
drwxr-xr-x 3  4096 2011-02-12 16:43 Billy Taylor
drwxr-xr-x 3  4096 2011-02-12 16:43 Bobby "Boris" Pickett
drwxr-xr-x 3  4096 2011-02-12 16:43 Habib Koité and Bamada
drwxr-xr-x 3  4096 2011-02-12 16:43 Herbie Hancock
drwxr-xr-x 4  4096 2011-02-12 17:13 iTunes
drwxr-xr-x 7  4096 2011-02-12 16:42 Jamiroquai
drwxr-xr-x 3  4096 2011-02-12 16:41 jools holand
drwxr-xr-x 5  4096 2011-02-12 16:41 Jools Holland
drwxr-xr-x 4  4096 2011-02-12 16:40 Kool & The Gang
drwxr-xr-x 3  4096 2011-02-12 16:40 queen
drwxr-xr-x 3  4096 2011-02-14 16:41 System of a Down
drwxr-xr-x 3  4096 2011-02-12 16:40 The Partisans
drwxr-xr-x 4  4096 2011-02-12 16:40 The Police
drwxr-xr-x 3  4096 2011-02-12 16:39 Trijntje Oosterhuis
@Ubuntu:~/Music$ cd Jamiroquai
@Ubuntu:~/Music/Jamiroquai$ ls -l
total 20
drwxr-xr-x 2  4096 2011-02-12 16:41 A Funk Odyssey
drwxr-xr-x 2  4096 2011-02-12 16:43 High Times: Singles 1992-2006
drwxr-xr-x 2  4096 2011-02-12 16:41 Rock Dust light star
drwxr-xr-x 2  4096 2011-02-12 16:42 The Return of the Space Cowboy [Sony Soho Square]
drwxr-xr-x 2  4096 2011-02-12 16:42 Travelling Without Moving [Bonus Track]
@Ubuntu:~/Music/Jamiroquai$ cd "Rock Dust light star"
@Ubuntu:~/Music/Jamiroquai/Rock Dust light star$ ls -l
total 47028
-rw-r--r-- 1  3930201 2011-02-12 16:41 01 - Rock Dust Light Star
-rw-r--r-- 1  3263057 2011-02-12 16:41 02 - White Knuckle Ride
-rw-r--r-- 1  4415157 2011-02-12 16:41 03 - Smoke and Mirrors
-rw-r--r-- 1  3188474 2011-02-12 16:41 04 - All Good In The Hood
-rw-r--r-- 1  3968776 2011-02-12 16:41 05 - Hurtin'
-rw-r--r-- 1  3394009 2011-02-12 16:41 06 - Blue Skies
-rw-r--r-- 1  4233051 2011-02-12 16:41 07 - Lifeline
-rw-r--r-- 1  4871836 2011-02-12 16:41 08 - She's A Fast Persuader
-rw-r--r-- 1  3969008 2011-02-12 16:41 09 - Two Completely Different Things
-rw-r--r-- 1  4007608 2011-02-12 16:41 10 - Goodbye To My Dancer
-rw-r--r-- 1  3710790 2011-02-12 16:41 11 - Never Gonna Be Another
-rw-r--r-- 1  5087754 2011-02-12 16:41 12 - Hey Floyd
@Ubuntu:~/Music/Jamiroquai/Rock Dust light star$ music123 Hurtin'.mp3
> 

```

---

### Post by hakermania on 2011-02-19
Ok, the format is the following. If you do it right it will work.
1) cd to the prefereble dir
2) type rhythmbox songname.ogg
IF song name has spaces use " "
that's all.
[IMG]http://uppix.net/0/a/2/9d54c4ebab60e4542d14e56fc5749.png[/IMG]

---

### Post by Spyderkid on 2011-02-19
music123 worked for another piece of music so never mind.

Is it safe though because when you play it, it says "THERE IS NO WARRANTY FOR THIS PROGRAM"

---

### Post by hakermania on 2011-02-19
> **Spyderkid said:**
> music123 worked for another piece of music so never mind.

Is it safe though because when you play it, it says "THERE IS NO WARRANTY FOR THIS PROGRAM"
there is no warranty for any open source software program under gpl [http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)
***_(For the developers' and authors' protection, the GPL clearly explains that there is no warranty for this free software)_***

---

### Post by Spyderkid on 2011-02-19
okay thanks

---

### Post by stinkeye on 2011-03-04
> **tgalati4 said:**
> sudo apt-get install moc
mocp
Thanks tgalati4, great little progam.
All I need, really.

---

