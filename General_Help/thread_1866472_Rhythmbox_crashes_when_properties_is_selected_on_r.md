---
title: "Rhythmbox crashes when properties is selected on removable media menu"
date: 2011-10-21
forum: General Help
---

### Post by splinter701 on 2011-10-21
Hi guys
I just recently upgraded from 11.01 to Ubuntu 11.10, and with it came this bug.
When I load my iPod nano 5g or any other removable media player device  (I tried a few) into rhythmbox and go to 'properties on the menu, the  program just crashes.

'segmentation fault' is the only seemingly useful thing printed to the  terminal when this happens, though if necessary I will post a full log.  There have been a few bug reports on this subject on launchpad as well  though.

I've also tried purging and reinstalling rhythmbox and still no luck, still just segmentation faults.

I'd really appreciate it if anyone could tell me why this is happening and how I can fix it.

---

### Post by splinter701 on 2011-10-21
bump for justice

---

### Post by duke.tim on 2011-10-21
Try using another music player
Clementine
Exaile
Banshee
Amarok

If I remember right, rhythmbox is not actively being developed.


Please wait 24 hours before bumping

---

### Post by splinter701 on 2011-10-21
Banshee is not really ok, it will only sync only 1 playlist or the whole music library (or only 1 podcast or the whole lot of them). While banshee looks nicer, rhythmbox has better capability.

Clementine and Amarok dont seem to be able to actually sync a playlist, you just copy songs through them, if i wanted to do that i'd just use nautilus.

Exaile might work, as long as it recognises the ipod. I'll give it a try.

But, what does 'segmentation fault' mean? I've seen it in bug reports for other programs as well, but never found out what it meant.

---

### Post by splinter701 on 2011-10-22
There seems to be conflicting information over the rhythmbox development. Ubuntu software centre claims that canonical is maintaining it, and several threads say that there has been updates. A lot of people are convinced it is out of development.

The fact is, there is really no better music manager for Ubuntu, it is organised and has plenty of features along with more plugins if necessary.
It's a little sad to see it be abandoned if development has stopped.

---

### Post by duke.tim on 2011-10-22
A segfault is where there is an attempt to access memory that can't be accessed. 

Wikipedia for the win
[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

I personally like rhythmnbox and clementine best :)

Out of curiosity I took a look at rhythmnbox's developer site, and looks like little to no progress has happened in the last year. That doesn't mean they haven't been working on it though. The newest commit is 9 months old (except for a polish translation 3 days ago).

I'm guessing that you would be able to see the segfault in your syslog, try posting what is happening in your log. I don't know if I can help with the segfault problems though hopefully someone more knowledgeable than myself will show up -_-'  8-[

---

### Post by splinter701 on 2011-10-24
Thanks for the reply. 
I guess i'll try seeing if I can sync to the ipod as root, might take a bit of work since rhythmbox doesnt recognise the attached device as root.

here is the log 
I ran 'rhythmbox'
This happened when i selected the ipod from the menu
```
(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:17942): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

```This happened when i selected properties from the right-click menu
```
 (rhythmbox:17942): GLib-GObject-CRITICAL **: g_value_set_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Segmentation fault 
```
Thanks a lot for your replies

---

### Post by DexterP17 on 2011-10-26
Rhythmbox is still being developed just look at the git and you'll see that it IS.

[http://git.gnome.org/browse/rhythmbox/](http://git.gnome.org/browse/rhythmbox/)

---

### Post by splinter701 on 2011-10-26
I haven't seen any updates for the users lately though :(
Anyone know how to make sense of the logs I posted?

---

### Post by nyex on 2011-11-02
well, darn. i'm having this same problem. i like rhythmbox. banshee can't handle my music collection (for some mysterious reason) and it won't let me browse music by genre. snif snif :(

---

### Post by splinter701 on 2011-11-02
[LEFT]Yeah, I still cant get it to work. Personally, I'm thinking of downgrading back to the LTS release of ubuntu, since 11.10 just seems to handle external devices really badly. 

...and of course I wont have to deal with unity or 'gnome classic'. I'll get back the gnome I know and love.
[/LEFT]

---

### Post by nyex on 2011-11-02
banshee crashes with the ipod as well (for different reasons, it seems, but hey). reminds me why i stayed with rhythmbox to begin with. but now they are talking about bringing it back in the next ubuntu release, so we'll see how that goes :)

rhythmbox also crashes when i try to delete a playlist in the ipod, by the way. only gtkpod saves now.

---

### Post by splinter701 on 2011-11-02
For me in the end I stopped using the ipod all together. Since I have an android phone which supports samba filesharing I just copy the songs to a folder on that. 

Advantages: wireless filesharing, supports way more music formats, easy to search for songs, podcasts can be downloaded direct to device
Disadvantages: shorter battery life.

Now that I've started using this, I dont know if I will go back to using the ipod, except for long travels...
Still, having rhythmbox not work is a source of frustration...

---

