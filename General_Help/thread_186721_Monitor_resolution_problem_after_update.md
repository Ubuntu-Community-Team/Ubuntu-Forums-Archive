---
title: "Monitor resolution problem after update"
date: 2006-06-02
forum: General Help
---

### Post by MasterEvilAce on 2006-06-02
Hey, I updated to KDE 3.5.3, but it may have been related to something else (I also updated to the final release of dapper).. 

Now when linux starts, it uses the max resolution, 19xx by xxxx.. Instead of the max resolution of my monitor (1600x1200)
i have selected 1600x1200 but the changes are lost whenever I reboot

i have tried removing all of the upper resolutions from my xorg.conf, but they reappeared after restart. so no help there.

Need some way to make it go back to how it was-- always using 1600x1200

dell inspiron 8000 (laptop)
kubuntu 6.06
KDE 3.5.3

---

### Post by apollyonis on 2006-06-02
Any chance you could post what the x.org file looks like on here?

---

### Post by redcyborg on 2006-06-02
Check ur xorg.conf file (/etc/X11/) and make sure the correct resolution is in there under the Selection "Screen" Section.

i run 1440x900 so i have

SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1280x1024" "1024x768"
    EndSubSection

u need to add in "####x####"

Hope it helps

---

