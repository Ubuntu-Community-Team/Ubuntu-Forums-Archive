---
title: "Annoying video playback freezes"
date: 2009-08-04
forum: General Help
---

### Post by Lockheed on 2009-08-04
When I watch movies (xvid mostly) video freezes every few dozens of seconds for 5-10 seconds but sounds keeps rolling along just fine. 

It has no relation to CPU load and the same movies in windows play just fine. What is that?

---

### Post by Lockheed on 2009-08-06
Bump

---

### Post by philinux on 2009-08-06
If you are running compiz try setting desktop effects to none.

Also check in sys>admin>hardware drivers. Is the graphics driver installed?

---

### Post by Lockheed on 2009-08-09
I do use Compiz and I do have newest 190 nvidia drivers installed.
I did not disable compiz to verify because that would mess with my screenlets. But isn't there any other possible causes and solutions?

I use compiz for its superior ergonomy rather than eyecandy.

---

### Post by Barafu Albino Cheetah on 2009-08-09
There can be many ways to output video to screen. Among them are: x11, dri, gl, glx2 and others. There must be such setting in the video player somewhere. Try them all, start with GL.  Additionally, chech for too high deinterlacing algorythms enabled - even my ultra-turbo-core-quad can't handle some of them.

---

### Post by Lockheed on 2009-08-09
Well, that helped a little. I am using VLC and it was on "default". I checked all other options and the only one which does not cause 1+ second freezes is "X11 video". Still, the freezes are there but much shorter. No more than 0.5 sec. I also think they are more often but I am not sure about it.

Any ideas on hot to totally remove those freezes?

---

### Post by Lockheed on 2009-08-10
Well, the problem is back. I am running on VLC X11 and the long freezes are still there if the movie is in a window. When fullscreened, most of the time it freezes just for up to 0.5 sec which is not as bad but long freezes still happen.

Any ideas?

---

### Post by Lockheed on 2009-08-12
Some updates.

I discovered those problems do not exist in mPlayer even if it plays movies using the same output method. However, I have always used VLC because it is much more ergonomic. Besides, it takes 1 minute before mPlayers starts after I click on avi.

Does that gives you any clues?

---

### Post by gardara on 2009-08-12
Try mplayer + smplayer... It's better than vlc imo.

[http://smplayer.sf.net](http://smplayer.sf.net)
[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

---

### Post by Lockheed on 2009-08-12
Thanks! So far so good. Will test is some more.

Two questions, though.
Is there a way to set volume on mouse scroll and to grab and drag movie window just with a mouse?

---

### Post by gardara on 2009-08-12
Open Smplayer 

Options > Preferences > Keyboard and Mouse > Mouse tab 
and set the "wheel function" to  "Volume control"

---

### Post by Lockheed on 2009-08-12
Thanks. Great player. Finally, something comparable to SubEdit.

---

### Post by P4man on 2009-08-12
Smplayer FTW!

Although I have to admin, VLC 10.0.1 cured most, if not all of my VLC headaches (including stuttering playback).

---

