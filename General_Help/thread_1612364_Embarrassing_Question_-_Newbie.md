---
title: "Embarrassing Question - Newbie"
date: 2010-11-03
forum: General Help
---

### Post by Quarkrad on 2010-11-03
How do find the version of a file?  I#m having trouble with Skype and some solutions suggest looking at the version of a specific file and downgrading.  Nautilus shows path, size, modified date, etc  but not (on my configuration) the version number.  How do you find the version number of a file?

---

### Post by cpmman on 2010-11-03
Click on the Help in the application then About and it will show current version.

---

### Post by coldraven on 2010-11-03
Another handy way is to run System->Admin->Synaptic Package Manager.
Search for your package and you will see the current version. Then right click, select "Properties" and open the tab "Installed Files".
Then you can see where it put all it's files.
Sometimes you can discover Help documents that you would not have noticed otherwise.

Tip: Copy the path to whatever file, Open Nautilus file browser. ("Places") Then press "Ctrl+ L".
This changes the the path view from "breadcrumbs" to this style (/home/user/Music for example)
Then just Paste the path (Ctrl+V) and hit Enter and you should be in the directory. It saves a lot of typing! :)

---

### Post by Quarkrad on 2010-11-03
Sorry - not the application or package but the actual file.  E.g. on my system I have a file  /usr/lib/libv4l/v4l1compat.so    - how do I find what version v4l1compat.so is?   I have two machines, both 10.10, one Skype works OK - the other Skype crashes when you try and use video.  One solution is to run this file first and then launch Skype.  It works on one machine but not the other.  I appreciate the reason could be other things but I would like to find out if the version of the v4l1compat.so is the same before I go searching (where on earth?) to find what the difference between the two machines is.  This crashing of Skype when using video is a known/common thing on ubuntu but there are numerous solutions - this not an easy one.

---

### Post by TSJason on 2010-11-03
Assuming you're using the package manage for all installs you can simply check the package version, like this:

```

user@C9H13NO3] - [12:33:48]  
[~]$:> dpkg --list |grep libv4l
ii  libv4l-0                              0.6.4-1ubuntu1                                          Collection of video4linux support libraries
[user@C9H13NO3] - [12:33:52]  
[~]$:>

```

There you can see it's version 0.6.4.

---

