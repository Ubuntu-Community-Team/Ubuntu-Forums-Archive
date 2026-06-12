---
title: "A Few Questions About GOOBOX"
date: 2006-02-01
forum: General Help
---

### Post by gigi1234 on 2006-02-01
Hello All,

Have installed Goobox to rip cds to MP3, etc. and it works however when I start it in the terminal I see these messages when I begin the extraction process:

[B](goobox:10887): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(goobox:10887): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Couldn't find matching gstreamer tag for track-count
Couldn't find matching gstreamer tag for duration
Couldn't find matching gstreamer tag for encoder
Couldn't find matching gstreamer tag for encoder-version

(goobox:10887): Gtk-CRITICAL **: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed
[/B]

What do these messages mean? What can I do to fix what is wrong? The tracks rip and play fine but the messages are troubling.

Also, does anyone know how to set this up so you can launch it from GNOME instead of the terminal???

THANKS!

---

### Post by sbassett on 2006-02-01
gigi -

I have had this issue with many GTK programs. I usually have output concerning issues such as these, kde even more. For adding this to the menu, I would suggest SMEG (simple menu editor for gnome).

[QUOTE=gigi1234]Hello All,

Have installed Goobox to rip cds to MP3, etc. and it works however when I start it in the terminal I see these messages when I begin the extraction process:

[B](goobox:10887): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(goobox:10887): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Couldn't find matching gstreamer tag for track-count
Couldn't find matching gstreamer tag for duration
Couldn't find matching gstreamer tag for encoder
Couldn't find matching gstreamer tag for encoder-version

(goobox:10887): Gtk-CRITICAL **: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed
[/B]

What do these messages mean? What can I do to fix what is wrong? The tracks rip and play fine but the messages are troubling.

Also, does anyone know how to set this up so you can launch it from GNOME instead of the terminal???

THANKS![/QUOTE]

---

### Post by gigi1234 on 2006-02-02
Doesn't anyone know something about running GOOBOX in Ubuntu? I am still getting these messages and have looked everywhere I can think to find something out about it but I am stumped.

---

### Post by bonzodog on 2006-02-02
I suspect these are debug messages from bad code - you will see eclipse is in constant devlopment. They are probably small bugs which won't directly affect you. You ought to see some of the gtk errors that turn up on other programs .

---

### Post by matthew on 2006-02-02
[quote=gigi1234]Doesn't anyone know something about running GOOBOX in Ubuntu? I am still getting these messages and have looked everywhere I can think to find something out about it but I am stumped.[/quote]I have used goobox to rip at least 30 cds (I owned them all) and have had either the same or similar error messages each time. I have no idea what they refer to, but goobox has always worked perfectly and produced good rips. Also, totem and gxine do the same thing for me when I start them from the command line.

I say, don't worry about it. If it's working, ignore the messages.

---

### Post by xmastree on 2006-02-02
[QUOTE=gigi1234]when I start it in the terminal I see these messages when I begin the extraction process:[/QUOTE]A lot of programs give me errors if I run them from a terminal, but they work fine. The solution? don't run it from a terminal, use Alt-F2 instead, or create a launcher.

So long as it works, then it'll work.

What the eye does not see... :rolleyes:

Edit:

> Also, does anyone know how to set this up so you can launch it from GNOME instead of the terminal???Right click on the top (or bottom) panel, select **add to panel > Custom application launcher** click **+ Add** and enter the command in the relevant field.

Edit Mk II:
> Have installed Goobox to rip cds to MP3, Have you tried Sound Juicer? AFAIK it's part of the standard install (at least, I don't remember specifically installing it). And then there's Easytag for cleaning up the tags, if you like things neat and tidy.

---

### Post by gigi1234 on 2006-02-02
Thanks everybody!

I guess I'll not worry about it because it does work nicely for rips. I never had any success with Sound Juicer or Grip for MP3s, even though I had the right codecs, etc.

---

