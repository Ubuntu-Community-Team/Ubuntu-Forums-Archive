---
title: "tvtime question"
date: 2012-09-28
forum: General Help
---

### Post by Louisraritan on 2012-09-28
Anyone else use tvtime with a tv tuner in Ubuntu?  I have a goofy question:  When running the app, there is header text at the top of the application window.  Ex; tvtime [60]: It's better with the butterfly.  Is there a way to edit a file and change that text to say something I want it to say or ever better...nothing?

---

### Post by aaalbatrosss on 2012-12-26
To not display tag message add this line to ~/.tvtime/tvtime.xml file:

<option name="ShowTaglines" value="0"/>

---

