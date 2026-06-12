---
title: "Moving files in Terminal? Moving files that have root permissions"
date: 2010-03-04
forum: General Help
---

### Post by Cardboard Tube Knight on 2010-03-04
I have limited experience in terminal, but let me first explain what I am trying to do to see if there is some easier way to do it. Basically I want to change the skin in aMSN. I downloaded the new skin but am unable to unzip or move it without /root permissions. I don't know how to acquire this without being in terminal. So I figured there had to be some way to go into the terminal and use it to move the unzipped folder from the desktop to the aMSN skins folder. 

Is there an easier way to do this? 

And how do I do it with terminal if there's not?

---

### Post by wojox on 2010-03-04
You could:

```
gksudo nautilus
```

Then you'll be opening nautilus with root permissions and you can just drag and drop it in. Not sure where the aMsn skins folder is, so I thought this would be easier for you. Be careful though. You can do damage if you start clicking and deleting files outside your Home Folder.

---

### Post by Cardboard Tube Knight on 2010-03-04
This might sound stupid or noobish, but is nautilus the ubuntu equivalent of explorer?

---

### Post by wojox on 2010-03-04
Pretty much. It's your file manager. Everything work out okay?

---

