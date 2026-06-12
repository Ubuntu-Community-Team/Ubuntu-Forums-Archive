---
title: "Last.FM and the mystery plugin."
date: 2010-05-24
forum: General Help
---

### Post by Hastor on 2010-05-24
I recently reinstalled and I found that not only did Last.FM not seem to work right off the bat for Ryhmbox or as a streaming system off the online site. To remedy this I went to the site and opened up the recommended plugin box and installed the adobe plug. This didn't seem to work so I went after the second recommended choice which all I can remember is it having something to do with GNOME specifically. All this seemed to do was enlarge the play icons (right-pointing arrow inside a circle) for every media online. I decided to go back and attempt a reinstallation of the JRE package which went very well and actually solved a couple of unrelated issues. In the end, though, Last.FM remains completely unusable. I'm sure there's a quick fix for this, but for whatever reason it seems to escape me. Thanks.

---

### Post by tgalati4 on 2010-05-24
I use vagalume to listen to last.fm.

sudo apt-get install vagalume

---

### Post by Hastor on 2010-05-25
Thanks, man. It worked out very well and it seems very well made. 
On another note, would you happen to have any idea what I could do about the mystery plugin? I hate having stuff lurking around inside my system without any knowledge of what it is. Thanks again, man.

---

### Post by cybrsaylr on 2010-05-25
> **tgalati4 said:**
> I use vagalume to listen to last.fm.

sudo apt-get install vagalume

Thanks for the tip on vagalume!
Used to listen to Last FM a lot till it wouldn't play on newer Ubuntu versions very well. Vagalume seems to play nice the little I used it so far.

---

### Post by tgalati4 on 2010-05-25
From what I understand it has to do with changes to the last.fm streaming protocol.  The vagalume developer modified his code to work properly with the last.fm server.  The rhythmbox plugin has some bugs which cause track jumping and other weirdness.  I'm not sure if it's being maintained because the bug has been around a long time.

It's working for me on rhythmbox 0.12 under Linux Mint 8 (based on Jaunty).  

I like vagalume because I use it on my nokia n800 and it has a simple interface that works well under gnome.

---

