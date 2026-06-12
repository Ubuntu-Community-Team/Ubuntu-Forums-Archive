---
title: "Right click to remove folder, how to?"
date: 2012-01-09
forum: General Help
---

### Post by ubto66 on 2012-01-09
ubuntu 10.04.
This video shows how to get ubuntu to shreed folders/files by right-clicking a file or
folder.  [http://www.youtube.com/watch?v=BPWW0QhajIQ](http://www.youtube.com/watch?v=BPWW0QhajIQ)

Well, I couldn't  make it shreed folders but only files.

How do you remove a folder or file by rightclicking the folder or file?
It is not moving to trash that is being asked for.

Thank you.

---

### Post by JRV on 2012-01-09
Open Nautilus
Click Edit=>Preferences=>Behavior and check "Include a Delete command that bypasses trash".

---

### Post by Basher101 on 2012-01-09
why not delete via marking all, then hitting shift + del? it will remove them permanentley instantly, without them being moved to trash. otherwise you can also delete files with ```
rm /path/to/file
```

regards

---

### Post by JRV on 2012-01-09
Open Nautilus
Click Edit=>Preferences=>Behavior and check "Include a Delete command that bypasses trash".

You will be asked to confirm before the file/folder is deleted.

Is this what you were looking for?

---

### Post by ubto66 on 2012-01-12
Thank you for answering.
Yes, that is what I'm searching for.  Using terminal rm seems to be laborious.
If I open nautilus ->
edit-> pref ->
then there is no behavor option, instead it says runtime pref. 
or UI pref. or import or export or schemes or I/O providers?
So I can't find the delete check box.

---

### Post by pretty_whistle on 2012-01-12
> **ubto66 said:**
> Thank you for answering.
Yes, that is what I'm searching for.  Using terminal rm seems to be laborious.
If I open nautilus ->
edit-> pref ->
then there is no behavor option, instead it says runtime pref. 
or UI pref. or import or export or schemes or I/O providers?
So I can't find the delete check box.
There should be a tab called "Behavior".  Then it would be at the bottom.

No tab?
WTF

---

### Post by pretty_whistle on 2012-01-12
Maybe you could open a different nautilus window and see if it's there.

---

### Post by ubto66 on 2012-01-14
To Basher: I tried, the shift delete and it works fine.
And I will use it, but it's another shortcut to remember.
Thanks.

To Pretty and JVR:
I can't find the location for the setting. Nautilus config.
tool is the one placed in the system tab?
Thanks.

---

