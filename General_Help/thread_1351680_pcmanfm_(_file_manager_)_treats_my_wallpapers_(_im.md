---
title: "pcmanfm ( file manager ) treats my wallpapers ( images ) as executables."
date: 2009-12-10
forum: General Help
---

### Post by Physical Hook on 2009-12-10
Why it treats my images as executables and doesn't show thumbnails ( works just fine in Nautilus ) ?

[[IMG]http://i46.tinypic.com/2cne1x3.png[/IMG]]("http://i49.tinypic.com/2mrffv6.png")

---

### Post by raktarok on 2009-12-10
Hi,

I am not sure what's the problem, but we can start with this:
```
ls -l <path to any jpg file in that folder>
```
without the brackets, of course.
Let's see what the permissions for the files are.

You can try this for a quick fix maybe - it removes the executable part of the files. Go to the folder and issue this command:
```
chmod -x *.jpg
```
This should probably fix the issue.
Or you can look at the permissions tab in the file manager and see if you can remove the executable bit.

---

### Post by Physical Hook on 2009-12-11
All it did was removed the executable icon - thumbnails are still not visible.

---

### Post by decomp on 2009-12-22
Hi Physical Hook,

Does it do this for all files or just images? I have the problem of PCManfm showing all my files as text or executable files. There was a but report filed on their source forge page in october, but it was closed. I just filed a new bug here 
[https://sourceforge.net/tracker/?func=detail&aid=2919515&group_id=156956&atid=801864](https://sourceforge.net/tracker/?func=detail&aid=2919515&group_id=156956&atid=801864)
maybe you can add that you are suffering the same issue (if so.)

---

### Post by Physical Hook on 2009-12-22
> **decomp said:**
> Hi Physical Hook,

Does it do this for all files or just images? I have the problem of PCManfm showing all my files as text or executable files. There was a but report filed on their source forge page in october, but it was closed. I just filed a new bug here 
[https://sourceforge.net/tracker/?func=detail&aid=2919515&group_id=156956&atid=801864](https://sourceforge.net/tracker/?func=detail&aid=2919515&group_id=156956&atid=801864)
maybe you can add that you are suffering the same issue (if so.)

I've already confirmed it by creating this thread.

---

