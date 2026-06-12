---
title: "Xsane preview selection problem"
date: 2009-12-31
forum: General Help
---

### Post by Ian Lowry on 2009-12-31
I'm unable to adjust the selection in the preview window in XSane in Karmic. I manage to grab the selection box but the line will not move, although it worked fine in Jaunty.

Anyone else seeing this problem?

Ian

---

### Post by lathanial on 2010-01-21
Since I upgrade to Karmic I can't get a preview at all. When I select show preview a blank window opens. If I drag the mouse across the window "fragments" appear where I think the edge of the viewing window should be. It worked fine in Hardy. Any ideas?

lathanial

---

### Post by emacdonald on 2010-01-29
Same problem here.... I have managed to get it to work by changing Visual Effects to None. (Though this has not be successful all the time.)

Based on the above I feel that it is a graphics driver issue. Though at the moment I am at a loss as to what can be done.

Driver used is NVIDIA Version 185 on a GEFORCE 8200. on a 9.10 platform

Sometime later! more news.
I have a work around, if you open Xsane, and then select the preview it does not work. But if you close xsane via Ctrl-Q while the Preview window is open. Then restart xsane the preview window is opened (as you have previously selected it) and lo and behold the preview pane is working.

---

### Post by bturig on 2010-02-02
> **emacdonald said:**
> 
I have a work around, if you open Xsane, and then select the preview it does not work. But if you close xsane via Ctrl-Q while the Preview window is open. Then restart xsane the preview window is opened (as you have previously selected it) and lo and behold the preview pane is working.

Yep. That works! Thanks!!!

---

### Post by bigchrisrogers on 2010-07-03
Thanks emacdonald, this has been bugging me for ages now and your workaround is truly effective.

---

### Post by wmichaelb on 2011-06-06
Works for me on 10.04 too, thanks so much. The weird thing is that it worked fine until just tonight. Maybe and update fouled it up?

---

### Post by logantracyo on 2012-01-04
> **emacdonald said:**
> 
I have a work around, if you open Xsane, and then select the preview it does not work. But if you close xsane via Ctrl-Q while the Preview window is open. Then restart xsane the preview window is opened (as you have previously selected it) and lo and behold the preview pane is working.

Wow, what a great tip!  That absolutely did the trick for me; the preview window was totally garbled after I closed Preview prior to closing XSane the last time I used it.  I just quit XSane with the funky preview window still open, and when I restarted XSane, the Preview window was perfect again.  Thanks so much for taking the time to post that!

=tracy

---

### Post by flint_ on 2012-04-05
Congratulations, the ctl-Q trick worked great!!!

---

