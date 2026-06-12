---
title: "Howto clear re4cent documents ?"
date: 2010-01-23
forum: General Help
---

### Post by MooPi on 2010-01-23
Embarrassing porn in recent documents ? How do you clear recent documents cache ?

---

### Post by stinkeye on 2010-01-23
> **MooPi said:**
> Embarrassing porn in recent documents ? How do you clear recent documents cache ?
Easiest way is to install [_**[COLOR="DarkRed"]Ubuntu Tweak[/COLOR]**_]("http://blog.ubuntu-tweak.com/downloads")
and disable recent documents.
You'll find it in Ubuntu Tweak under gnome settings.

---

### Post by jamesisin on 2010-01-23
Easy enough:

Places --> Recent Documents --> Clear Recent Documents

Of course, it looks a little suspicious when that list is EMPTY!  Just click on ten text files and fill it up with something uninteresting.

---

### Post by MooPi on 2010-01-23
I'm using gnome-shell and it seems to be missing. I'm going to drop out of shell and edit.

---

### Post by MooPi on 2010-01-23
I guess what I was really asking is where are the recent documents stored ? Or how can I control them through CLI.

---

### Post by c0mput3r_n3rD on 2010-01-23
> **MooPi said:**
> I guess what I was really asking is where are the recent documents stored ? Or how can I control them through CLI.

I believe it stored at ~/.recently-used

---

### Post by MooPi on 2010-01-23
Removing or editing the ".recently-used" doesn't seem to affect the recent documents preview.

---

### Post by fisheater on 2010-01-23
Try BleachBit from repos. It does more than just recent docs.

Here is some info on it: [http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

### Post by MooPi on 2010-01-23
Found a solution to turn off recent documents. Create a text file if you don't already ```
.gtkrc-2.0
```insert ```
gtk-recent-files-max-age=0
```Upon restart recent documents should be gone from view.

---

### Post by jamesisin on 2010-01-23
Excellent solution.

---

### Post by scouser73 on 2010-01-23
> **MooPi said:**
> Embarrassing porn in recent documents ? How do you clear recent documents cache ?

To permanently disable the Recent Document listings, paste the following commands into Terminal.

**1** - > **rm ~/.recently-used.xbel**

**2** - > **touch ~/.recently-used.xbel**

**3** - > **sudo chattr +i ~/.recently-used.xbel**

---

### Post by jamesisin on 2010-01-23
scouser73 - And why does that work?

---

### Post by scouser73 on 2010-01-24
> **jamesisin said:**
> scouser73 - And why does that work?

You can see here why is works. [http://www.watchingthenet.com/ubuntu-tip-clear-disable-recent-documents.html](http://www.watchingthenet.com/ubuntu-tip-clear-disable-recent-documents.html)

---

### Post by MooPi on 2010-01-24
Nice solution scouser73 but I believe my solution eliminates all recent documents and with nothing left to hide. So when this is enabled later your only going to display what actually is recent.

---

### Post by jamesisin on 2010-01-24
From man chattr:

> A file with the &#8216;i&#8217; attribute cannot be modified: it cannot be  deleted or  renamed,  no  link  can  be created to this file and no data can be written to the file.  Only the superuser or a  process  possessing  the CAP_LINUX_IMMUTABLE capability can set or clear this attribute.

That method can be reversed/disabled by simply running:

sudo chattr -i ~/.recently-used.xbel

Which changes the removes the previously added attribute (- instead of +).

---

