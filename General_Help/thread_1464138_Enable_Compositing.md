---
title: "Enable Compositing"
date: 2010-04-27
forum: General Help
---

### Post by Dportner on 2010-04-27
Hi so i was fooling around in CCSM and trying to get docky to have blur, then i turnd up a setting too high i guess and now docky is telling me to Enable Compositing?
there must be an easy fix to this but i just dont know it.


*UPDATE*
k so i went into gconfig-editor and searched for compositing and found it, and turnd it on, but now iv lost all my compiz effects???


*2nd update*
k. i firgured it out lol. all i had to do was go into appearance and turn "extra" effects back on.
someone please delete this thread

---

### Post by midnight93933 on 2010-05-04
Can you please tell me how you did that Docky is telling me that I need to enable compositing help

---

### Post by b3nny_mac on 2011-02-06
I was having the same problem, not knowing how to "enable compositing,"  I downloaded dock, and it was great except there was an about 2 inch black bar on the bottom of my screen when I launched the app, and a message would pop-up saying I would need to "enable compositing."  I searched hi and lo on the web to find a solution, and posters said I just needed to go into compliz or meta-something.   I have been using linux for two days now, and I do not have the nomenclature down.  Anyway, I finally stumbled acorss this forum posting:

[http://ubuntu-tutorials.com/2009/02/25/update-enable-compositing-the-easier-way/](http://ubuntu-tutorials.com/2009/02/25/update-enable-compositing-the-easier-way/)

followed the instructions and the black bar behind Docky is gone.  Also whenever I tab between applications, a more detailed screen appears, so that was a nice little gift.  

Really enjoy Linux/Ubuntu/Gnome; still not sure of the correct wording.  Glad to be out of the clutches of window.

---

### Post by Habitual on 2011-02-06
FYI: re: Docky and compositing


Open the GNOME Configuration Editor; press Alt-F2 to open the Run Application dialog and type gconf-editor. Click Run. Navigate to Apps->metacity->general. Check the compositing_manager box, and Metacity will immediately restart with compositing!

---

