---
title: "Problems with sound in Rhythmbox..."
date: 2005-02-21
forum: General Help
---

### Post by wibbe on 2005-02-21
Hello.

I have a problem in rhythmbox; when I'm playing a song, I get theese error popups:

"Could not start pipeline playing"
"Could not open resource for writing"

XMMS can play files without a problem, anyone knows what to do?
Thanks,
W

---

### Post by hkctr on 2005-02-22
Are you using ALSA ?  If so select Custom as the Default Sink in System->Preferences->Multimedia Systems Selector and input [alsasink device=hw:0] as the Pipeline.  This fixed my Rhythmbox for me.

---

