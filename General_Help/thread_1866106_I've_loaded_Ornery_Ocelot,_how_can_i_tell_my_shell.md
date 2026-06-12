---
title: "I've loaded Ornery Ocelot, how can i tell my shell?"
date: 2011-10-21
forum: General Help
---

### Post by pakrat1963 on 2011-10-21
Ornery Ocelot is up and running, but i'm not sure which shell i'm using. i have a feeling i may be running the GNOME shell, and i am getting a further feeling that maybe gnomes should stay in the garden where they belong!

i'm a gooey kind of guy, so when my GUI isn't doing what i want it to do, hair starts falling out, my feet smell worse...

i do a lot of writing based on 'net research, so i spend a lot of time toggling between apps. Or i used to before the Ornery Ocelot came into my life. So far it doesn't seem to support quick toggling.

Sorry for whining like a frustrated noobie. That's what happens when a caveman gets turned loose amongst you nice tech folk.

Thanks for the help.
Pakrak

---

### Post by quequotion on 2011-10-21
+1 for Ubuntu 11.10: Ornery Ocelot

---

### Post by pakrat1963 on 2011-10-21
i thought Ornery sounded less offensive than Obnoxious Ocelot...

i've also notice that when i try to open any of the files in the dash(?), whether Documents, downloads, Videos, or Pictures, the !@#$ music player opens. i miss my "Places" button and screen bottom tool bar so much... almost as much as my On/Off switch...

Thanks for letting me whine some more, i'm open to suggestions.

Thanks,
Pakrat

---

### Post by quequotion on 2011-10-25
Well, I don't know if there's anything to be done about the problems in your first post, but if everything's opening in totem I may have a solution for you!

Check the file **~/.local/share/applications/mimeapps.list**

It has two sections **[Added Associations]** and **[Default Applications]**

In **[Added Associations]** you might have this line ```
inode/directory=totem.desktop;
``` which must be changed to ```
inode/directory=nautilus.desktop;totem.desktop;
```

Rather than deleting the line completely, as I find often suggested, this will make sure things open correctly **AND** let you open directories in Totem from the right-click menu.

Note: this is a feature/bug in GNOME. Whenever a user right-clicks on something in nautilus, and chooses to "Open with Other Application" that application is added to  mimeapps.list, first in line. If this is done to a directory, it means all directories and the files in them will open in that application.

---

