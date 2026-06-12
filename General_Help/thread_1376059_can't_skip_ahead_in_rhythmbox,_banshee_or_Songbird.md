---
title: "can't skip ahead in rhythmbox, banshee or Songbird"
date: 2010-01-08
forum: General Help
---

### Post by DouglasAWh on 2010-01-08
I was told in the Fedora IRC channel that I needed to download a package to be able to skip ahead in audio files.  However, I was not told what package.  I searched the repos for rhythmbox and saw nothing that looked like it would be it.  I assume it's something with gstreamer or pulseaudio, but mp3s play, so something with those is working...

Even though this is a Fedora issue, you guys always seem more helpful. :) ...and hey, I put it in Community Cafe for a reason.

Also, trying to skip ahead in a song in Songbird actually crashes songbird!

---

### Post by Kingsley on 2010-01-08
Do you have gstreamer0.10-plugins-ugly installed? Or try installing the latest build of Rhythmbox from Koji.
[http://koji.fedoraproject.org/koji/](http://koji.fedoraproject.org/koji/)

---

### Post by cariboo on 2010-01-08
Please don't post help questions in the Cafe. Moved.

---

### Post by DouglasAWh on 2010-01-08
> **cariboo907 said:**
> Please don't post help questions in the Cafe. Moved.

I thought it was considered bad form to post about other distros in the help section?

Also, it appears gstreamer needed an update...but why did PackageKit not tell me this.  Seems odd that a regression like that would happen without an update...

Whatever, I don't care.  It's fixed.  Thanks!

---

