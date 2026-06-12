---
title: "Flip webcam horizontally"
date: 2011-11-02
forum: General Help
---

### Post by gwu777 on 2011-11-02
Hi there,

I know a lot has been writen about this issue, but I haven't found a clear answer. When using my webcam with cheese or skype, it drives my muts that my head goes right when I go left and vice versa!

How can I flip the video, I am using a microsoft HD300

Surely there must be an option somewhere, help...

---

### Post by Script Warlock on 2011-11-02
this is what i'm using to invert my a4tech webcams.

> export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so yourapps

---

### Post by gwu777 on 2011-11-02
Thank you for the help above, this is what I get:

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

Should I customised your code other than the app name, and if so how?

---

### Post by Script Warlock on 2011-11-02
yes it might be /v4lcompat.so cheese or whatever.

---

### Post by gwu777 on 2011-11-02
I replaced it with skype and/or cheese and I am upside down with cheese and nothing happen with skype...

I have replaced the 3 with 1 and the horizontal flip works with cheese, GREAT! But skype is still the same, ie no change.

Error with skype:
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

Error with cheese:
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
** Message: Error: Stream contains no data.
gsttypefindelement.c(954): gst_type_find_element_activate (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind:
Can't typefind empty stream

---

### Post by Script Warlock on 2011-11-02
try to check the webcam driver it might be or not using v4l anymore.

---

### Post by gwu777 on 2011-11-02
> **Script Warlock said:**
> try to check the webcam driver it might be or not using v4l anymore.

How do I do this? It does work with cheese though...

---

### Post by Script Warlock on 2011-11-02
be right back i need to take a nap it's almost 4am in my place.

---

### Post by gwu777 on 2011-11-02
> **Script Warlock said:**
> be right back i need to take a nap it's almost 4am in my place.

Definitely go and have a rest! Thank you for your help, see you tomorrow!

---

