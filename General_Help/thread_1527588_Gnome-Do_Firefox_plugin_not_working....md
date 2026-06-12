---
title: "Gnome-Do Firefox plugin not working..."
date: 2010-07-09
forum: General Help
---

### Post by rmflagg on 2010-07-09
Hi everyone,

   I just installed Gnome Do and for the most part, it works great!

   The only problem is that it does not search my Firefox bookmarks.  Every other search seems to work just fine.
   I ran Do in a terminal and this is what came up:

(Do:13821): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: System.NullReferenceException: Object reference not set to an instance of an object
  at Mono.Data.SqliteClient.SqliteDataReader.GetString (Int32 i) [0x00000] 
  at Firefox.PlacesItemSource+<LoadPlaceItems>c__Iterator3.MoveNext () [0x00000] 
  at System.Collections.Generic.List`1[Firefox.PlaceItem].AddEnumerable (IEnumerable`1 enumerable) [0x00000] 
  at System.Collections.Generic.List`1[Firefox.PlaceItem]..ctor (IEnumerable`1 collection) [0x00000] 
  at System.Linq.Enumerable.ToArray[PlaceItem] (IEnumerable`1 source) [0x00000] 
  at Firefox.PlacesItemSource.UpdateItems () [0x00000] 
  at Do.Universe.Safe.SafeItemSource.UpdateItems () [0x00000] .

   After that, I went in a disabled the Firefox plug in and ran it again and the only alert was the "Wnck-CRITICAL" message, which seems to always be there.

   I am running 10.04, with Compiz.

Thanks,
RMFlagg

---

### Post by rmflagg on 2010-07-12
**bump**

---

### Post by hibob on 2010-12-05
Same Problem here.
Though it wasn't caused by an update. It started when I cleared my personal information (history, cookies etc.) on firefox.

Could use some help on this.

---

### Post by wilee-nilee on 2010-12-05
> **hibob said:**
> Same Problem here.
Though it wasn't caused by an update. It started when I cleared my personal information (history, cookies etc.) on firefox.

Could use some help on this.

If you really want help you start your own thread. That is the basic tenet of using the forum.;)

---

### Post by hibob on 2010-12-05
Well, I didn't want to open a new thread if I have the same problem. The two posts should be connected somehow. I figured just drawing some attention to this thread should do the trick.

---

### Post by vanadium on 2011-01-15
This is a problem for a long time. I even found a thread where I was not yet aware it was an issue: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1083456](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1083456) The issue was also not solved there.

---

### Post by vanadium on 2011-01-15
Yet another post here, [http://ubuntuforums.org/showthread.php?t=1565119](http://ubuntuforums.org/showthread.php?t=1565119), that includes a link to a bug report.

---

### Post by pros on 2011-01-15
[https://bugs.launchpad.net/do/+bug/205824](https://bugs.launchpad.net/do/+bug/205824)
This works...

[https://bugs.launchpad.net/do/+bug/205824/+attachment/1776862/+files/Firefox.dll]("https://bugs.launchpad.net/do/+bug/205824/+attachment/1776862/+files/Firefox.dll")

The proposed patch, solves this problem in Lucid and Maverick.
Just replace the file in /usr/lib/gnome-do/plugins.

---

### Post by vanadium on 2011-01-15
I tried this already, but I am glad you did me try again. When activitating the plugin, a cross appears instead of the Firefox icon. I interpreted this as a problem with the plugin, but it is just a cosmetical issue: indeed, it works.

The cosmetical issue can be fixed providing a firefox-3.5.png icon ([https://bugs.launchpad.net/ubuntu/+source/gnome-do-plugins/+bug/444171):](https://bugs.launchpad.net/ubuntu/+source/gnome-do-plugins/+bug/444171):)

```

sudo ln -s /usr/share/pixmaps/firefox.png /usr/share/pixmaps/firefox-3.5.png

```

Thank you for having me try again! Indeed, this solved this six months old thread.

---

### Post by pros on 2011-01-15
:)
All the credit goes to [https://bugs.launchpad.net/do/+bug/205824/comments/6]("https://bugs.launchpad.net/do/+bug/205824/comments/6")
I just compiled gnome-do plugins, to obtain the working firefox.dll

---

