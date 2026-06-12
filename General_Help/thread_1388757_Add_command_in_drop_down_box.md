---
title: "Add command in drop down box"
date: 2010-01-23
forum: General Help
---

### Post by thebrandon on 2010-01-23
I was wondering if there was a way to add a command in the drop down box in the file browser.  I have to convert mkv to mp4 to play on my ps3 and I was hoping that when I right clicked on mkv files it would have the option to run mkv2mp4 in the terminal.

---

### Post by dcstar on 2010-01-24
> **thebrandon said:**
> I was wondering if there was a way to add a command in the drop down box in the file browser.  I have to convert mkv to mp4 to play on my ps3 and I was hoping that when I right clicked on mkv files it would have the option to run mkv2mp4 in the terminal.

Open with other application.....

Then you pick whatever app/script available.

---

### Post by VCoolio on 2010-01-24
You can create a [nautilus script]("https://help.ubuntu.com/community/NautilusScriptsHowto) for that.

Something like:

```
#!/bin/sh
gnome-terminal -e mkv2mp4 $NAUTILUS_SCRIPT_SELECTED_URIS
```

save in ~/.gnome2/nautilus-scripts , make executable (chmod +x filename) and right click your file in nautilus.

---

### Post by thebrandon on 2010-01-24
Thanks to both of you for the suggestions, the nautilus script addition is great now I just have to test it out!  Thanks again!

---

### Post by thebrandon on 2010-02-01
It doesnt appear to work at all.  The terminal flashes up and dissapears very quickly, then nothing.  Also since moving all of this stuff around and trying to put everything in my path I cant get the script to work properly anyway!

---

