---
title: "Rhythmbox crashes an awful lot"
date: 2010-11-22
forum: General Help
---

### Post by Legeril on 2010-11-22
I find that every time I use rhythmbox on 10.04 I inevitably have to re-start my computer, it just crashes out on about 1/4 of my songs. I use force kill but it doesn't clear the program completely and finally have to kill it with a restart if I want to listen to music again on that session.

Is there any reason why it will be crashing so much? I'm sure the files aren't corrupt

---

### Post by carl4926 on 2010-11-22
Are all the files the same format and what is that? (mp3, flac, ?)

---

### Post by Legeril on 2010-11-22
Now some vary in format, but usually it will play one song from an album and pick one that it doesn't like - so it doesn't usually happen when going from format-to-format. Though the most common format to crash on is mp3 as I have more of them than any other format.

---

### Post by carl4926 on 2010-11-22
If you start rhythmbox from the terminal, leave the terminal open, use RB, wait for the crash and report any info from the terminal.

BTW: Are the music files located on a external HD and what format is it?

---

### Post by Legeril on 2010-11-22
> **carl4926 said:**
> If you start rhythmbox from the terminal, leave the terminal open, use RB, wait for the crash and report any info from the terminal.

BTW: Are the music files located on a external HD and what format is it?

I have no external media.

I'll look into this now, and post when I have the info. Thanks

---

### Post by Legeril on 2010-11-22
when I try to open rhythmbox from the terminal I get this

```
** (rhythmbox:1952): DEBUG: Loading the real store page
** (rhythmbox:1952): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token

(rhythmbox:1952): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:1952): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:1952): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:1952): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:1952): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:1952): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:1952): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:1952): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:1952): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed
** (rhythmbox:1952): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=496&partner=983

```

and it just hangs there, doesn't return to @Lucid :~$

I'm assuming that isn't normal

---

### Post by carl4926 on 2010-11-22
Try a new RB config file.
Add no plugins - I think it something to with that

[https://one.ubuntu](https://one.ubuntu)
[http://stores.7digital](http://stores.7digital)

---

### Post by Legeril on 2010-11-22
how do I download a new config file?

neither of those links work for me :(

---

### Post by carl4926 on 2010-11-22
Those links were points I was drawing your attention to from your error info

It looks like RB is running some plugins like ubuntu one and is having trouble with them

Config files are hidden
I'm not sure ATM because I'm on a openSUSE machine but probably in .config

To get there go to file manager at /home/*username
press Ctrl+H
Go to .config
In there look for rhythmbox folder and rename it to rythmbox-old

try RB again

---

### Post by SlugSlug on 2010-11-22
not a fix but gmpc + mpd   is a really good Music player

---

### Post by Legeril on 2010-11-22
I don't have any folders for RB in my .config file..

Maybe I should try a new media player

---

### Post by t4thfavor on 2010-11-22
Yup, I stopped using it a while ago, as I have TONS of music on external storage, and couldn't get through more than a few songs before a crash.

I also tried the music local, though on SSD not a real HDD, so that may also have been a factor.

---

### Post by carl4926 on 2010-11-22
> **Legeril said:**
> I don't have any folders for RB in my .config file..

Maybe I should try a new media player
It's .gconf/apps/

---

### Post by antonvrg on 2010-11-22
easy fix!

just use vlc

---

