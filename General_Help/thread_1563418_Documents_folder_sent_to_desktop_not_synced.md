---
title: "Documents folder sent to desktop not synced"
date: 2010-08-29
forum: General Help
---

### Post by dwbsr on 2010-08-29
Ubuntu 10.04.1
GNOME desktop

OK, If you right click on the Documents folder in you home profile and select "copy to desktop" you would assume that both folders would be synced because your basically creating a short-cut for main folder to the desktop.

Assuming that these folders would sync made an *** out of me, I'm finding that I have to keep copying files from one "Documents folder" to the other one.
I don't want to hear about Ubuntu One because that NOT what I trying to do. I don't want to share my folder I just want them both to contain the same information. I don't understand if you make a short-cut of a folder it SHOULD contain the same information as the parent directory, you shouldn't have to open both folders and hand-sync them. That's just stupid and redundant.

---

### Post by sharathcshekhar on 2010-08-29
When you copied a folder to Desktop, as the name suggests, you _COPIED_ it to your Desktop. You did not create the Link to it! So Ubuntu is behaving perfectly all right. 
What you would want to try is, right Click on the folder, and select "Make a link". That would create a Link in the present working Directory. NOw Copy/Move he link to you Desktop. You have now created a true _LINK_
Alternatively, open your terminal and give
```

ln -s /full/target/path/ ~/Desktop/Link_name

```

---

### Post by dwbsr on 2010-08-29
> **sharathcshekhar said:**
> When you copied a folder to Desktop, as the name suggests, you _COPIED_ it to your Desktop. You did not create the Link to it! So Ubuntu is behaving perfectly all right. 
What you would want to try is, right Click on the folder, and select "Make a link". That would create a Link in the present working Directory. NOw Copy/Move he link to you Desktop. You have now created a true _LINK_
Alternatively, open your terminal and give
```

ln -s /full/target/path/ ~/Desktop/Link_name

```

Thank you for your assistance, it works now! I even searched google and it kept coming up with Ubuntu one information.

---

