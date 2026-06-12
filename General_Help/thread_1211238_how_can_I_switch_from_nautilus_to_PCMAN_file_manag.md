---
title: "how can I switch from nautilus to PCMAN file manager?"
date: 2009-07-12
forum: General Help
---

### Post by sdowney717 on 2009-07-12
PCMan works so fast. Everything Nautilus is solw. It takes 30 seconds to open windows. So if you right click save as, it will open the file save dialog box, but it is too slow. Who wants to sit there waiting on it.

I would like to switch all the normal functions away from Nautilus to that.
I want to able to click on files and have the programs open just like they eventually do in nautilus.

---

### Post by sdowney717 on 2009-07-12
[http://www.ubuntugeek.com/how-to-replace-nautilus-with-pcman-file-manager-in-ubuntu.html](http://www.ubuntugeek.com/how-to-replace-nautilus-with-pcman-file-manager-in-ubuntu.html)

tried this and it does not work anymore?
there files named that in the folder, BUT they are listed as backup files. Editing them has no effect on nautilus opening or not.
I ended up cutting and pasting 4 files into a "test" folder. then when I renamed them they turned into icons saying "open folder" and "computer"
Those files are not even used, when gone fron usr, nautilus still opens.

---

### Post by sdowney717 on 2009-07-12
[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)
also tried this and it does not work

now when clicking on places home folder it opens VLC player and all my desktop icons are gone.

at least the restore put it back the way it was before.


OK, I got it working using the first website.
weirdly, there are supposed to be 2 files named this and you need to put in that

    For nautilus-computer.desktop: Exec=pcmanfm /

and

    For nautilus-folder-handler.desktop: Exec=pcmanfm %U 

But for some reason on my system, there was a "~" at the end of the files and any changes 
I made were ignored. The only way I could rename them was to use nautilus as a super user. PCMan could not do it, kept reverting to "open folder" and "computer"

---

