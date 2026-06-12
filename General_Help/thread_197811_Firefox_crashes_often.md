---
title: "Firefox crashes often"
date: 2006-06-16
forum: General Help
---

### Post by eighthate on 2006-06-16
what can i do to fix this?

---

### Post by zxee on 2006-06-16
Have you tried opening firefox from a shell and then checking the output there-after a crash? You could also check the specific log files. Personally if I was having this problem I would download firefox directly from the mozilla-firefox site and install it by hand. There is also a forum at mozilla that addresses problems specific to ff. Hope that helps.

---

### Post by magomago on 2006-06-16
I complained about this the other day as well...Even with crash recovery it is plain annoying.  I'm apalled at how this got through testing.

Just use epiphany...its based on firefox and faster.  

type

'sudo apt-get install epiphany"

in shell to get it

---

### Post by jonrkc on 2006-06-16
[QUOTE=zxee]Personally if I was having this problem I would download firefox directly from the mozilla-firefox site and install it by hand. There is also a forum at mozilla that addresses problems specific to ff. Hope that helps.[/QUOTE]
What I've always done is to install by hand (it's almost automatic) the latest stable version of Firefox from mozilla.org.  I found the version included in Ubuntu to be not to my taste, and it wouldn't pick up my hard-won preferences and settings.  The official version does, and does not crash--I can't remember the last time it crashed.  

There's just one problem with the installer from Mozilla (at least the last time I used it): It is hard to get it to accept the directory you try to specify to put Firefox into.  But after two or three tries I manage to get it done.  

Firefox will update itself automatically now, too.  And it no longer loses the list of search engines you've put in.  (Used to have to go get them one-by-one again.)

---

### Post by bruce89 on 2006-06-16
```
sudo apt-get install epiphany
``` won't work
```
sudo apt-get install epiphany-browser
``` will.

---

### Post by aysiu on 2006-06-16
[HowTo Get Rid of a Corrupt Firefox Profile (and keep the bookmarks)](http://www.ubuntuforums.org/showthread.php?t=103930)

---

### Post by lucidite on 2006-06-24
[QUOTE=zxee]Have you tried opening firefox from a shell and then checking the output there-after a crash?[/QUOTE]
I've had the same problem & I've done that.
This is what Konsole tells me:

[HTML]`pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox-bin:7120): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `gdk_window_is_viewable (src)' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox-bin:7120): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `gdk_window_is_viewable (src)' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox-bin:7120): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `gdk_window_is_viewable (src)' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(firefox-bin:7120): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
[/HTML]

I think there was more to that, however that's all that was listed.
So does this help anyone? Anything I can do to get Firefox stable?

---

### Post by jonrkc on 2006-06-24
You've probably already tried this, but I think it's worth a shot: using aptitude, reinstall firefox, and specify the "fix-broken" option on the command line:

```

aptitude --fix-broken reinstall firefox

```

I think your personal settings will be untouched, but when I do things similar to this, I generally backup my  ~/.mozilla file just in case.  (I wish firefox had a separate file for customization and preferences, like Thunderbird.)

If it doesn't work, I do again strongly recommend going to mozilla.com and getting the latest package of Firefox and installing it by hand, which is really, really easy except for one step you may have to ask it to do over (naming the directory you want it in).  It only takes a few seconds, and as I said earlier, I can't even remember the last time my Firefox, installed that way, crashed--for any reason.

Good luck.  I know how annoying it is to have the browser crash esp. when you're hot on the trail of something--and probably haven't kept notes!  :)  (Though with "session restore," you will get back exactly the tabs, etc. you had when it crashed, really nice sometimes.)

---

### Post by lucidite on 2006-06-24
> Good luck. I know how annoying it is to have the browser crash esp. when you're hot on the trail of something--and probably haven't kept notes!

Oh yeah, it's annoying. Especially because it was crashing every minute of so.

This said, I reinstalled firefox like you suggested & so far, it's fine. 

Thanks!

---

### Post by flipkick on 2006-06-24
try using the tar.gz from mozilla.org or see this thread. maybe that satisfies you

[http://ubuntuforums.org/showthread.php?t=196805](http://ubuntuforums.org/showthread.php?t=196805)

---

### Post by tommcd on 2006-06-24
If you install firefox by hand, do you need to uninstall the version of FF that comes with Ubuntu first? Won't you have 2 firefoxes if you do not?

---

### Post by aysiu on 2006-06-25
You'll have two Firefoxes, and that's fine--as you'll be using only one, effectively.

---

### Post by flipkick on 2006-07-12
I had no crash in the last 10 days. Using FireFox 1.5.2 from mozilla.org.

Something fixed this buggy thing ?

---

### Post by jonrkc on 2006-07-12
As I recall--it's been a year now--I used the Ubuntu-supplied Firefox and it crashed or just didn't work right, so I went back to installing from Mozilla.org and got my normal operation back.  So I always get my updates and new versions from there.  BTW, they just released a release candidate for version 2.0 today or yesterday.  I haven't been to get it because I figure their servers are so busy I might as well wait a week or so.  

The thing I like best about Firefox is its rigid adherence to international HTML and other publishing standards.  It backfires sometimes because so many sites are either sloppily written, or written only for MS Explorer--or both!  In which case I turn to Opera or Konqueror, both a lot more forgiving.   But I like the principled stance the Mozilla people have stuck to on this issue.

P. S. (Edit)  I think Firefox may have crashed on me twice, maybe only once, in 2.5 years, and I use it every day, for at least a couple or hours, often many more, every day I'm home.  Not a bad record for a complex piece of software.

---

### Post by flipkick on 2006-07-13
Yeah! FF is the best. I don't like Opera a lot because it now has this "fancy-stylish" image campaign going on. but well, I have the choice :)

---

