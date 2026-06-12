---
title: "need to be root to drag and drop"
date: 2011-03-08
forum: General Help
---

### Post by Amused2Death on 2011-03-08
simple problem, i need to be able to drag and drop a txt file into a folder so the program can find the bmp's.

trouble is root owns the folder (don't know why, i installed the program) and as such i don't have the power to access the folder.

Do a google search and theres preachers shouting about fire and brimstone for using root power and sudo is the way to go... yer right, do the sudo thing in terminal doesn't allow me to drag and drop the file. from what i see it simply gives me root power in the terminal screen which is pointless to a newb like me.

where i need the text file to go is in:
./opt/pcc2/share/planets/resource folder

any help would be much appreciated, 
thanks

---

### Post by mcduck on 2011-03-08
sudo *is* the way to go, just like all the guides and people say. It's just a question of figuring out what you actually want to do and where you need to use sudo to accomplish that.

In your case it's the file manager that you want to open with sudo:
```

gksudo nautilus

```

Also you probably should read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Amused2Death on 2011-03-08
pure genius :)

Thankyou

---

