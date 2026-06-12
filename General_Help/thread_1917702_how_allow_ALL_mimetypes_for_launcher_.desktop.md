---
title: "how allow ALL mimetypes for launcher .desktop ?"
date: 2012-01-30
forum: General Help
---

### Post by poikiloid on 2012-01-30
*******************
Update:
The function I really need is to be able to drop any files on any window, not necessarily on any launcher. I realize the "spread" behavior which allows files to be dropped on any specific window is currently broken ([https://bugs.launchpad.net/unity/+bug/863408](https://bugs.launchpad.net/unity/+bug/863408)).
After that is fixed, would this mimetype-awareness of ubuntu launchers still prevent me from dropping any file on any window after drag-hovering the file over a launcher icon? I presume it would, so my question is probably still valid, but I just wanted to clarify my needs...
*******************



Hello,

I do not like Ubuntu's (new?) behavior of restricting what files can be dropped on a launcher.

I would like to be able to drop ANY and ALL file types on my terminal window.

Is there a way to specify this on the "MimeType=" line of the terminal's .desktop file (located in /usr/share/applications)?

I have tried

```
MimeType=*/*;
```

this does not work. a wildcard will work after a main class, such as

```
MimeType=text/*;
```

The above works for approving any type of text file. But apparently not the first approach. So, do I just need to add the mimetypes for all classes (as listed here: [http://www.iana.org/assignments/media-types/index.html](http://www.iana.org/assignments/media-types/index.html))

or is there some other way?

Actually, my preferred approach would be to just enable any file type to be dropped on any launcher globally, not having to add a mimetype list to all my launchers. i am a big boy--i don't need ubuntu to hold my hand on this.  Any ideas?

---

