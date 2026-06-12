---
title: "How to output GNOME terminal log to a file?"
date: 2010-09-10
forum: General Help
---

### Post by RRRay on 2010-09-10
I want to output the log to a file in GNOME terminal, and I tried ">" operator to save the log but it didn't save the debug messages print on the GNOME terminal to the log file.
I used the command to play an audio file by gstreamer and try to save the log to /home/debuglog as below: 

**GST_DEBUG=3 gst-launch playbin uri=file:///home/16khz.wma > "/home/debuglog"**

and the debug messages weren't contained in the debuglog file.
It seems like ">" only to save some specific messages to the log file.
How do I save the complete log to a file?

---

### Post by TeoBigusGeekus on 2010-09-10
Try this
```
GST_DEBUG=3 gst-launch playbin uri=file:///home/16khz.wma | tee ~/Desktop/file.log
```

---

