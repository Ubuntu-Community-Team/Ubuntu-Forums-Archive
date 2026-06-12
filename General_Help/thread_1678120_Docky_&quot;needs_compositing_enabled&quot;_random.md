---
title: "Docky &quot;needs compositing enabled&quot; random error"
date: 2011-01-29
forum: General Help
---

### Post by everluck on 2011-01-29
So I installed Linux Mint 10 yesterday, and decided to grab Docky. Looked to me like the best dock software on Linux. It worked fine for a while, perfectly well, and I was very impressed. About half an hour into use I was given a "Docky needs compositing enabled" error and I lost a section at the bottom of my screen (became blank space). Docky itself, however, never shut down. It was still active and usable, being in fact the only visible part of the bottom 1/8th of my screen.

Here is a screenshot to illustrate: [IMG]http://i51.tinypic.com/29bspk.png[/IMG]

I'm not sure why this is happening. It can be remedied by logging out. What I'm guessing is happening is a driver crash, as all Compiz effects are disabled after I receive the error message.

I have a Radeon 5870, and have the latest drivers installed. Is this a known problem? Any way to fix it? I googled the "compositing enabled" error, but none of the circumstances I found matched mine.

Prefixed this thread with Ubuntu, since as far as I know, Linux Mint is an Ubuntu derivative.

---

### Post by kerry_s on 2011-01-29
try using metacity composite in gconf-editor.

---

### Post by Habitual on 2011-01-29
Open the GNOME Configuration Editor; press Alt-F2 to open the Run Application dialog and type gconf-editor. Click Run. Navigate to Apps->metacity->general. Check the compositing_manager box, and Metacity will immediately restart with compositing!

---

### Post by sarsbretta on 2011-01-31
Worked for me.
Thanks!

> **Habitual said:**
> Open the GNOME Configuration Editor; press Alt-F2 to open the Run Application dialog and type gconf-editor. Click Run. Navigate to Apps->metacity->general. Check the compositing_manager box, and Metacity will immediately restart with compositing!

---

### Post by MrRichard on 2011-01-31
> **Habitual said:**
> Open the GNOME Configuration Editor; press Alt-F2 to open the Run Application dialog and type gconf-editor. Click Run. Navigate to Apps->metacity->general. Check the compositing_manager box, and Metacity will immediately restart with compositing!
It worked for me too! Thanks for the help :D

---

### Post by Habitual on 2011-01-31
Sure thing! x2.

Glad it worked out.

---

